---
title: "析构函数语义的更改 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a9b97bd94793887f6d443d18914c2155597bec5d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="changes-in-destructor-semantics"></a>析构函数语义的更改
类析构函数语义具有显著从更改托管扩展的 c + + 为 Visual c + +。  
  
 在托管扩展中，在引用类，但不是在值类，允许已使用类析构函数。 这未更改的新语法中。 但是，已更改的类析构函数语义。 本主题重点介绍的原因更改，并讨论了它如何影响现有的 CLR 代码的转换。 它可能是最重要的程序员级别更改语言的两个版本之间。  
  
## <a name="non-deterministic-finalization"></a>非确定性终止  
 与对象相关联的内存回收垃圾回收器，一个关联之前`Finalize`调用方法，（如果存在）。 你可以将此方法视为一种超析构函数因为它不绑定到的对象的程序生存期。 我们引用此作为终止。 计时刚时或甚至是否`Finalize`调用方法是不确定的。 这是我们时，意味着什么我们表现为垃圾回收非确定性终止。  
  
 非确定性终止适用于动态内存管理。 当可用内存不足时，垃圾回收器就会启动。 在垃圾回收环境中，不是必需的析构函数释放内存。 非确定性终止不是很有效，但是，当对象维护如数据库连接或某种类型的锁定关键资源。 在这种情况下，我们应尽可能快地发布该资源。 在本机领域，通过使用构造函数/析构函数对实现。 只要对象的生存期结束，在其中声明它的本地块结束时，或由于引发的异常，导致的堆栈解散析构函数执行，并自动释放资源。 此方法非常也适用和死我们了其没有在托管扩展中。  
  
 由 CLR 提供的解决方案是一个类实现`Dispose`方法`IDisposable`接口。 此处问题是`Dispose`需要用户显式调用。 这是容易出错。 C# 语言提供适当形式的一种特殊形式的自动化`using`语句。 托管扩展的设计不提供特殊支持。  
  
## <a name="destructors-in-managed-extensions-for-c"></a>Managed Extensions for c + + 中的析构函数  
 在托管扩展中，引用类的析构函数实现通过使用以下两个步骤：  
  
1.  用户提供析构函数内部重命名为`Finalize`。 如果类具有的基础类 （请记住，在 CLR 对象模型，支持仅单一继承），编译器插入对以下用户提供代码的执行其终结器的调用。 例如，考虑下面的简单层次结构的托管扩展语言规范中获取：  
  
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
  
 在此示例中，这两个析构函数重命名为`Finalize`。 `B``Finalize`具有的调用`A`的`Finalize`添加的方法的调用之后`WriteLine`。 这是什么垃圾回收器将默认情况下调用在终止期间。 下面是此内部转换可能如下所示：  
  
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
  
1.  在第二个步骤中，编译器将合成虚拟的析构函数。 此析构函数是我们的托管扩展用户计划调用直接或通过删除表达式的应用程序。 垃圾回收器永远不会调用此操作。  
  
     此合成析构函数中放入了两个语句。 一个是对的调用`GC::SuppressFinalize`若要确保的其他调用`Finalize`。 第二个是对实际调用`Finalize`，它表示该类的用户提供析构函数。 下面是什么这可能如下所示：  
  
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
  
 虽然此实现允许用户显式调用类`Finalize`方法现在而不不是具有控制，通过一次它不会不真正将链接使用`Dispose`方法解决方案。 这是在 Visual c + + 中进行更改。  
  
## <a name="destructors-in-new-syntax"></a>新语法中的析构函数  
 在新语法中，析构函数内部重命名为`Dispose`方法和引用类自动扩展，以实现`IDispose`接口。 也就是说，在 Visual c + + 下, 类我们对转换，如下所示：  
  
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
  
 在新语法中，显式调用任一析构函数时或当`delete`应用于跟踪句柄，基础`Dispose`自动调用方法。 如果它是派生的类的调用`Dispose`在结束时的合成方法插入的基类的方法。  
  
 但这不会获取我们一直到确定性终止。 若要访问的我们需要本地引用对象的附加支持。 （这具有内托管扩展中，没有类似的支持，并且因此它不是一个转换问题）。  
  
## <a name="declaring-a-reference-object"></a>声明的引用对象  
 Visual c + + 支持引用类的对象的声明本地堆栈上或作为类的成员就像它是直接访问。 使用析构函数的关联与结合使用时`Dispose`方法，结果是引用类型终止语义对自动的调用。  
  
 首先，我们定义我们引用类，以便对象创建充当其类构造函数通过资源的获取。 其次，在类析构函数，我们发布时创建对象时获得的资源。  
  
```  
public ref class R {  
public:  
   R() { /* acquire expensive resource */ }  
   ~R() { /* release expensive resource */ }  
  
   // everything else...  
};  
```  
  
 通过使用类型名称以本地方式随附的乘幂号而在声明的对象。 所有使用该对象，例如调用方法，都通过成员选择点 (`.`) 而不是箭头 (`->`)。 在块的结尾，关联的析构函数，将转换为`Dispose`，如下所示自动调用：  
  
```  
void f() {  
   R r;   
   r.methodCall();  
  
   // r is automatically destructed here -  
   // that is, r.Dispose() is invoked  
}  
```  
  
 与`using`C# 中的语句，这不会不 defy 所有引用类型的基础 CLR 约束必须在 CLR 堆上分配。 基础的语义保持不变。 用户可编写以下实现此目的 （和这可能是由编译器执行内部转换）：  
  
```  
// equivalent implementation  
// except that it should be in a try/finally clause  
void f() {  
   R^ r = gcnew R;   
   r->methodCall();  
  
   delete r;  
}  
```  
  
 实际上，在新语法中，析构函数再次与成对出现，构造函数为自动获取/释放机制取决于本地对象的生存期。  
  
## <a name="declaring-an-explicit-finalize"></a>声明显式终止  
 在新语法中，如我们所见，析构函数合成到`Dispose`方法。 这意味着，析构函数不显式调用时，垃圾回收器在终止过程，将不像以前那样寻找一个关联`Finalize`对象的方法。 若要支持析构和终止，我们引入了一种特殊的语法提供终结器。 例如:   
  
```  
public ref class R {  
public:  
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }  
};  
```  
  
 `!`前缀相当于波形符 (`~`) 这样将引入类析构函数-也就是说，这两种后生存期方法具有一个标记的类名称作为前缀。 如果合成`Finalize`方法在派生类中，基类的调用发生`Finalize`其末尾插入方法。 如果显式调用析构函数，则取消终结器。 下面是转换可能如下所示：  
  
```  
// internal transformation under new syntax  
public ref class R {  
public:  
   void Finalize() {  
      Console::WriteLine( "I am the R::finalizer()!" );  
   }  
};   
```  
  
## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>从 Managed Extensions for c + + 移动到 Visual c + + 2010  
 它是在下编译 Visual c + + 引用类包含非普通的析构函数时，会更改托管 c + + 程序扩展的运行时行为。 必需的转换算法是类似于以下：  
  
1.  如果存在析构函数，则重写，若要将类终结器。  
  
2.  如果`Dispose`方法存在，则重写到类析构函数。  
  
3.  如果析构函数是存在但没有任何`Dispose`方法，在执行第一项时保留析构函数。  
  
 在将你的代码从托管扩展迁移到新的语法，您可能缺少执行此转换。 如果应用程序依赖在某种程度上相关联的终止方法的执行，应用程序的行为将以无提示方式不同于你预期。  
  
## <a name="see-also"></a>另请参阅  
 [托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)   
 [析构函数和终结器中如何： 定义和使用类和结构 (C + + /cli CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)