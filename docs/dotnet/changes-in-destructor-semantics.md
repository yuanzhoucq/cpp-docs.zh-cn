---
title: "析构函数语义的更改 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "析构函数, C++"
  - "终结器 [C++]"
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 析构函数语义的更改
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，类析构函数的语义发生了重大更改。  
  
 在托管扩展中，引用类（而非值类）中允许类析构函数。  在新语法中，仍是如此。  但是，类析构函数的语义发生了变化。  本主题着重介绍这些变化的原因并讨论这些变化对转换现有 CLR 代码的影响。  类析构函数语义的更改可能是两个语言版本间最重要的程序员级别的更改。  
  
## 非确定终止  
 在垃圾回收器回收与对象关联的内存之前，会调用关联的 `Finalize` 方法（如果存在）。  由于该方法没有绑定到对象的程序生存期，因此可以将它视为一种超析构函数。  我们称之为终止。  调用 `Finalize` 方法的确切时间，甚至是否调用该方法，并没有进行定义。  这就是“垃圾回收表现为非确定终止”的含义。  
  
 非确定终止适用于动态内存管理。  可用内存不足时，垃圾回收器就会启动。  在垃圾回收环境下，无需析构函数来释放内存。  然而，当对象维护关键资源（如数据库连接或某种锁）时，非确定终止并不适用。  这种情况下，应尽快释放该资源。  在本机环境下，这是通过使用构造函数\/析构函数对完成的。  只要对象生存期一结束，无论是声明该对象的本地块结束了，还是由于引发异常导致的堆栈解散，析构函数就会运行，资源即自动释放。  这种方法的工作效果很好，在托管扩展中它的缺位一直让人感到惋惜。  
  
 由 CLR 提供的解决方案是让类实现 `IDisposable` 接口的 `Dispose` 方法。  这种办法的问题是 `Dispose` 要求用户显式调用。  这可能会引发错误。  C\# 语言通过特殊的 `using` 语句提供了适当形式的自动化。  而托管扩展不提供特殊支持。  
  
## C\+\+ 托管扩展中的析构函数  
 在托管扩展中，引用类的析构函数是通过以下两个步骤来实现的：  
  
1.  用户提供的析构函数在内部被重命名为 `Finalize`。  如果该类具有基类（请记住，在 CLR 对象模型下，只支持单一继承），编译器将在执行用户提供的代码后插入对其终结器的调用。  例如，以托管扩展语言规范中提供的以下简单层次结构为例：  
  
```  
__gc class A {  
public:  
   ~A() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   ~B() { Console::WriteLine(S"in ~B");  }  
};  
```  
  
 在本例中，两个析构函数均重命名为 `Finalize`。  `B` 的 `Finalize` 在调用 `WriteLine` 后，又调用了 `A` 的 `Finalize` 方法。  这是默认情况下垃圾回收器在终止过程中将调用的内容。  下面是此内部转换可能使用的代码：  
  
```  
// internal transformation of destructor under Managed Extensions  
__gc class A {  
public:  
   void Finalize() { Console::WriteLine(S"in ~A"); }  
};  
  
__gc class B : public A {  
public:  
   void Finalize() {   
      Console::WriteLine(S"in ~B");  
      A::Finalize();   
   }  
};  
```  
  
1.  在第二个步骤中，编译器合成了一个虚拟析构函数。  托管扩展用户程序将直接调用此析构函数，或通过应用 delete 表达式进行调用。  垃圾回收器从不调用此析构函数。  
  
     此合成析构函数中放入了两个语句。  一个是对 `GC::SuppressFinalize` 的调用，目的是确保没有对 `Finalize` 的其他调用。  第二个是对 `Finalize` 的实际调用，表示用户提供该类的析构函数。  下面是它可能使用的代码：  
  
```  
__gc class A {  
public:  
   virtual ~A() {  
      System::GC::SuppressFinalize(this);  
      A::Finalize();  
   }  
};  
  
__gc class B : public A {  
public:  
   virtual ~B() {  
      System::GC::SuppressFinalize(this);  
      B::Finalize();  
   }  
};  
```  
  
 虽然此实现允许用户立即（而不是在失去控制权后）显式调用类 `Finalize` 方法，但它实际上并没有与 `Dispose` 方法解决方案联系在一起。  这一点在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中已发生了变化。  
  
## 新语法中的析构函数  
 在新语法中，析构函数在内部被重命名为 `Dispose` 方法，引用类则被自动扩展为实现 `IDispose` 接口。  也就是说，在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 下，这一对类被转换为：  
  
```  
// internal transformation of destructor under the new syntax  
__gc class A : IDisposable {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~A");  
   }  
};  
  
__gc class B : public A {  
public:  
   void Dispose() {   
      System::GC::SuppressFinalize(this);  
      Console::WriteLine( "in ~B");    
      A::Dispose();   
   }  
};  
```  
  
 在新语法下显式调用析构函数时，或者将 `delete` 应用于跟踪句柄时，会自动调用基础 `Dispose` 方法。  如果它是派生类，将在合成方法的结束位置插入对基类的 `Dispose` 方法的调用。  
  
 但是，这不总是可以实现确定终止。  为了实现确定终止，我们需要附加的本地引用对象支持。（托管扩展内没有类似的支持，因此，不会构成转换问题。）  
  
## 声明引用对象  
 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 支持在本地堆栈上声明引用类的对象，或者将其声明为类的成员（就像可以直接访问它一样）。  当与析构函数和 `Dispose` 方法的关联结合使用时，结果将是对引用类型自动调用终止语义。  
  
 首先，定义引用类，使对象创建能够用来通过类构造函数获取资源。  其次，在类析构函数内，释放创建对象时获得的资源。  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // … everything else …  
};  
```  
  
 该对象是使用类型名称（不附带“帽子”）在本地声明的。  对该对象的所有使用（如调用方法）都是通过成员选择点 \(`.`\) 而不是箭头 \(`->`\)来实现的。  在块的末尾，自动调用关联的析构函数（被转换为 `Dispose`），如下所示：  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here –  
   // that is, r.Dispose() is invoked  
}  
```  
  
 与 C\# 内的 `using` 语句一样，这不违反必须在 CLR 堆上分配所有引用类型的基础 CLR 约束。  基础语义保持不变。  用户可编写以下等效代码（这可能是由编译器执行的内部转换）：  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 实际上，在新语法下，析构函数再次与构造函数进行配对，作为绑定到本地对象生存期的自动获取\/释放机制。  
  
## 声明显式终止  
 如前所述，在新语法中，析构函数合成到了 `Dispose` 方法中。  这意味着，在没有显式调用析构函数的情况下，在终止过程中垃圾回收器不会像以前一样寻找对象的关联 `Finalize` 方法。  为了同时支持析构和终止，我们引入了提供终结器的特殊语法。  例如：  
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 `!` 前缀与引入类析构函数的颚化符 \(`~`\) 类似，即，两种生存期后方法在类名称前都有一个标记作为前缀。  如果合成的 `Finalize` 方法出现在派生类中，则在其末尾处插入对基类 `Finalize` 方法的调用。  如果析构函数被显式调用，则取消终结器。  下面是可能的转换代码：  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## 从 C\+\+ 托管扩展迁移到 Visual C\+\+ 2010  
 在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 下编译时，只要引用类包含非常用析构函数，C\+\+ 托管扩展程序的运行时行为便会改变。  所需的转换算法大致如下：  
  
1.  如果存在析构函数，则将其重写为类终结器。  
  
2.  如果存在 `Dispose` 方法，则将其重写到类析构函数中。  
  
3.  如果存在析构函数但不存在 `Dispose` 方法，则在执行第一项时保留析构函数。  
  
 在将代码从托管扩展迁移到新语法时，可能会遗漏此转换的执行。  如果应用程序在某方面依赖于相关联的终止方法的执行，则该应用程序的行为将自行改变，不同于您期望的行为。  
  
## 请参阅  
 [托管类型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)   
 [Visual C\+\+ 中的析构函数和终结器](../misc/destructors-and-finalizers-in-visual-cpp.md)