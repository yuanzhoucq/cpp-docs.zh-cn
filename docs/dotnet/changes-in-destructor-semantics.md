---
title: 析构函数语义的更改 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finalizers [C++]
- destructors, C++
ms.assetid: f1869944-a407-452f-b99a-04d8c209f0dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c25045291afed1e8072867ee668716b2f396ef30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420018"
---
# <a name="changes-in-destructor-semantics"></a>析构函数语义的更改

类析构函数的语义发生了重大更改从托管扩展 c + + 的 Visual c + +。

托管扩展中，在类析构函数被允许在引用类，但不是在值类。 这未在新语法中进行更改。 但是，已更改的类析构函数语义。 本主题重点介绍的原因更改，并讨论了它如何影响现有 CLR 代码的转换。 它可能是语言的两个版本之间最重要的程序员级别更改。

## <a name="non-deterministic-finalization"></a>非确定性终结

与对象关联的内存回收垃圾回收器，一个关联之前`Finalize`调用方法，（如果存在）。 您可以将此方法作为一种超级析构函数的因为它不绑定到的程序生存期的对象。 我们之所以称为终止于此。 时间只是当或甚至是否`Finalize`方法调用是不确定的。 这就是我们说我们说垃圾收集具有不确定性的定案。

非确定性的定案适用于动态内存管理。 当可用内存不足时，垃圾收集器介入。 在垃圾回收的环境中，不是必需的析构函数释放内存。 不确定性定案不是很有效，但是，当对象维护对关键资源，例如数据库连接或某种类型的锁。 在这种情况下，我们应该尽快释放该资源。 在本机环境下，通过使用构造函数/析构函数对实现。 只要对象的生存期结束后，在其中声明它的本地块结束时，或导致引发异常的堆栈解散析构函数执行，并自动释放资源。 这种方法运行非常出色，托管扩展下的缺少遗漏了和益处语焉不详。

由 CLR 提供的解决方案是一个类来实现`Dispose`方法的`IDisposable`接口。 此处的问题是`Dispose`需要由用户显式调用。 这是容易出错。 C# 语言提供了适当形式中的一种特殊形式的自动化的`using`语句。 托管扩展的设计不提供特殊支持。

## <a name="destructors-in-managed-extensions-for-c"></a>C + + 托管扩展中的析构函数

在托管扩展中，引用类的析构函数实现通过使用以下两个步骤：

1. 用户提供析构函数内部重命名为`Finalize`。 如果类具有一个基类 （请记住，在 CLR 对象模型中，支持仅单一继承），编译器会插入到以下用户提供代码的执行其终结器调用。 例如，考虑下面的简单层次结构从托管扩展语言规范：

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

在此示例中，这两个析构函数重命名为`Finalize`。 `B``Finalize`已调用`A`的`Finalize`方法的调用之后添加`WriteLine`。 这是什么垃圾回收器将默认情况下调用在终止期间。 下面是此内部转换可能如下所示：

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

1. 在第二个步骤中，编译器将合成虚拟析构函数。 此析构函数是我们的托管扩展的用户程序调用直接或通过删除表达式的应用程序。 垃圾回收器永远不会调用此操作。

     此合成析构函数中放入了两个语句。 一个是调用`GC::SuppressFinalize`以确保没有更多调用`Finalize`。 第二个是实际调用`Finalize`，表示该类的用户提供析构函数。 下面是什么这可能如下所示：

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

尽管此实现允许用户显式调用类`Finalize`方法现在而非每次你对任何控件，它不真正会长使用`Dispose`方法解决方案。 这是在 Visual c + + 中进行更改。

## <a name="destructors-in-new-syntax"></a>在新语法中的析构函数

在新语法中，析构函数内部重命名为`Dispose`方法，并引用类自动扩展以实现`IDispose`接口。 即，在 Visual c + +，我们对类转换，如下所示：

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

在新语法中，显式调用析构函数时或当`delete`应用于跟踪句柄，基础`Dispose`自动调用的方法。 如果它是派生的类，调用的`Dispose`在合成的方法的结束处插入方法的基类。

但是，这不会向确定性定案不实现。 若要访问的我们需要本地引用对象的附加支持。 （这具有内托管扩展中，没有类似的支持，因此它不会转换问题。）

## <a name="declaring-a-reference-object"></a>声明的引用对象

Visual c + + 支持引用类的对象的声明在本地堆栈上或作为类的成员，就好像直接访问。 当具有析构函数的关联结合使用时`Dispose`方法，结果是自动的调用终止引用类型语义。

首先，我们定义我们引用类，使对象创建函数获取的资源通过其类构造函数。 其次，在类析构函数，我们发布时创建对象时获得的资源。

```
public ref class R {
public:
   R() { /* acquire expensive resource */ }
   ~R() { /* release expensive resource */ }

   // everything else...
};
```

通过使用类型名称在本地，但不随附 hat 声明对象。 所有使用该对象，如调用方法，可以通过成员选择点来都完成 (`.`) 而不是箭头 (`->`)。 在块的结束时，相关联的析构函数，转换为`Dispose`，自动调用的如下所示：

```
void f() {
   R r;
   r.methodCall();

   // r is automatically destructed here -
   // that is, r.Dispose() is invoked
}
```

与使用`using`C# 中的语句，这不会不迎接所有引用类型的基础 CLR 约束必须在 CLR 堆上分配。 底层的语义保持不变。 用户可编写以下等效 （和这可能是由编译器执行的内部转换操作）：

```
// equivalent implementation
// except that it should be in a try/finally clause
void f() {
   R^ r = gcnew R;
   r->methodCall();

   delete r;
}
```

实际上，在新语法中，析构函数再次与配对，构造函数作为自动获得/释放机制取决于本地对象的生存期。

## <a name="declaring-an-explicit-finalize"></a>声明显式终止

在新语法中，如我们所见，析构函数合成到`Dispose`方法。 这意味着，在没有显式调用析构函数，垃圾回收器在终止过程，将不像以前一样寻找关联`Finalize`对象的方法。 若要支持析构和终止，我们引入了特殊的语法提供终结器。 例如：

```
public ref class R {
public:
   !R() { Console::WriteLine( "I am the R::finalizer()!" ); }
};
```

`!`前缀是类似于颚化符 (`~`) 引入类析构函数-也就是说，这两种生存期后方法具有一个标记作为前缀的类的名称。 如果合成`Finalize`方法在派生类中，基类的调用发生`Finalize`在其末尾插入方法。 如果显式调用析构函数，则会抑制终结器。 下面是转换可能如下所示：

```
// internal transformation under new syntax
public ref class R {
public:
   void Finalize() {
      Console::WriteLine( "I am the R::finalizer()!" );
   }
};
```

## <a name="moving-from-managed-extensions-for-c-to-visual-c-2010"></a>从托管扩展 c + + 迁移到 Visual c + + 2010

在编译时在 Visual c + + 下，当引用类中包含非普通的析构函数时，更改 c + + 程序的托管扩展的运行时行为。 所需的翻译算法是类似于下面：

1. 如果存在析构函数，则重写为类终结器。

1. 如果`Dispose`方法存在，则重写到类析构函数。

1. 如果析构函数是存在但没有任何`Dispose`方法，在执行第一项时保留析构函数。

在将你的代码从托管扩展迁移到新的语法，可能会缺失此转换的执行。 如果应用程序以某种方式依赖于相关联的终止方法的执行，该应用程序的行为将以无提示方式不同于预期的一个。

## <a name="see-also"></a>请参阅

[将托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[析构函数和终结器中如何： 定义和使用类和结构 (C + + CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)