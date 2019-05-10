---
title: 如何：定义和使用类和结构 (C++/CLI)
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5fe7d6876b094c84fe3d4cdbba417106edcca528
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447291"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>如何：定义和使用类和结构 (C++/CLI)

本文介绍如何定义和使用用户定义的引用类型和中的值类型C++/CLI。

##  <a name="BKMK_Contents"></a> 内容

[对象实例化](#BKMK_Object_instantiation)

[隐式抽象类](#BKMK_Implicitly_abstract_classes)

[类型可见性](#BKMK_Type_visibility)

[成员的可见性](#BKMK_Member_visibility)

[公钥和私钥的本机类](#BKMK_Public_and_private_native_classes)

[静态构造函数](#BKMK_Static_constructors)

[语义的 this 指针](#BKMK_Semantics_of_the_this_pointer)

[按签名隐藏函数](#BKMK_Hide_by_signature_functions)

[复制构造函数](#BKMK_Copy_constructors)

[析构函数和终结器](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a> 对象实例化

引用 (ref) 可以仅将类型实例化托管堆上，不能在堆栈或本机堆上。 值类型可以在堆栈或托管的堆上实例化。

```cpp
// mcppv2_ref_class2.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;

   // nested class
   ref class MyClass2 {
   public:
      int i;
   };

   // nested interface
   interface struct MyInterface {
      void f();
   };
};

ref class MyClass2 : public MyClass::MyInterface {
public:
   virtual void f() {
      System::Console::WriteLine("test");
   }
};

public value struct MyStruct {
   void f() {
      System::Console::WriteLine("test");
   }
};

int main() {
   // instantiate ref type on garbage-collected heap
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass -> i = 4;

   // instantiate value type on garbage-collected heap
   MyStruct ^ p_MyStruct = gcnew MyStruct;
   p_MyStruct -> f();

   // instantiate value type on the stack
   MyStruct p_MyStruct2;
   p_MyStruct2.f();

   // instantiate nested ref type on garbage-collected heap
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;
   p_MyClass2 -> i = 5;
}
```

##  <a name="BKMK_Implicitly_abstract_classes"></a> 隐式抽象类

*隐式抽象类*不能实例化。 如果类的基类型是一个接口和类未实现的所有接口的成员函数，类是隐式抽象。

如果你不能构造中从接口派生的类的对象，原因可能是此类是隐式抽象。 有关抽象类的详细信息，请参阅[抽象](../extensions/abstract-cpp-component-extensions.md)。

下面的代码示例演示`MyClass`不能实例化类，因为函数`MyClass::func2`未实现。 若要启用要编译的示例，请取消注释`MyClass::func2`。

```cpp
// mcppv2_ref_class5.cpp
// compile with: /clr
interface struct MyInterface {
   void func1();
   void func2();
};

ref class MyClass : public MyInterface {
public:
   void func1(){}
   // void func2(){}
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259
                                          // To resolve, uncomment MyClass::func2.
}
```

##  <a name="BKMK_Type_visibility"></a> 类型可见性

您可以控制公共语言运行时 (CLR) 类型的可见性，以便引用程序集，如果程序集中的类型可以是可见或程序集外部不可见。

`public` 指示类型是否包含任何源文件可见`#using`指令包含的类型的程序集。  `private` 指示类型不可见的包含源文件`#using`指令包含的类型的程序集。 但是，专用类型都是相同的程序集内可见的。 默认情况下，一个类的可见性是`private`。

默认情况下，在 Visual Studio 2005 之前的本机类型必须在程序集外部的公共可访问性。 启用[编译器警告 （等级 1） C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)以帮助您查看私有本机类型使用不正确。 使用[make_public](../preprocessor/make-public.md)杂注提供公共可访问性不能修改源代码文件中的本机类型。

有关详细信息，请参阅 [#using 指令](../preprocessor/hash-using-directive-cpp.md)。

下面的示例演示如何声明类型并指定其可访问性，然后访问这些类型在程序集中。 当然，如果具有私有类型的程序集引用使用`#using`、 只在程序集中的公共类型都是可见。

```cpp
// type_visibility.cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// default accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   Private_Class ^ b = gcnew Private_Class;
   b->Test();

   Private_Class_2 ^ c = gcnew Private_Class_2;
   c->Test();
}
```

**输出**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

现在，让我们重新编写前面的示例，以便生成为 DLL。

```cpp
// type_visibility_2.cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside the assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// by default, accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};
```

下一个示例演示如何访问程序集之外的类型。 在此示例中，客户端使用在前面的示例生成的组件。

```cpp
// type_visibility_3.cpp
// compile with: /clr
#using "type_visibility_2.dll"
int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   // private types not accessible outside the assembly
   // Private_Class ^ b = gcnew Private_Class;
   // Private_Class_2 ^ c = gcnew Private_Class_2;
}
```

**输出**

```Output
in Public_Class
```

##  <a name="BKMK_Member_visibility"></a> 成员的可见性

您可以对访问从同一程序集中的公共类的成员不同于访问到它从程序集外部的通过使用成对的访问说明符`public`， `protected`，和 `private`

下表汇总了各种访问说明符的效果：

|说明符|效果|
|---------------|------------|
|public|成员是可访问内部和外部程序集。  请参阅[公共](../cpp/public-cpp.md)有关详细信息。|
|private|成员不是内部和外部程序集都不访问的。  请参阅[专用](../cpp/private-cpp.md)有关详细信息。|
|protected|成员是可访问内部和外部程序集，而只是派生类型。  请参阅[保护](../cpp/protected-cpp.md)有关详细信息。|
|internal|成员是在程序集中公共的但是私有程序集外部的。  `internal` 是上下文相关的关键字。  有关详细信息，请参阅[上下文相关的关键字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。|
|公共受保护-或-受保护公共|成员是在程序集中公共的但是程序集外部的受保护。|
|专用受保护-或-受保护的私有|成员是受保护在程序集中，但专用程序集外部的。|

下面的示例显示了具有不同的可访问性，使用声明的成员的公共类型，然后显示了如何在程序集中从这些成员的访问。

```cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();
   a->Protected_Public_Function();
   a->Public_Protected_Function();

   // accessible inside but not outside the assembly
   a->Internal_Function();

   // call protected functions
   b->Test();

   // not accessible inside or outside the assembly
   // a->Private_Function();
}
```

**输出**

```Output
in Public_Function
in Protected_Public_Function
in Public_Protected_Function
in Internal_Function
=======================
in function of derived class
in Protected_Function
in Protected_Private_Function
in Private_Protected_Function
exiting function of derived class
=======================
```

现在让我们构建一个 DLL 作为前面的示例。

```cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};
```

下面的示例使用在上一示例中，创建并从而演示如何访问从外部程序集的成员的组件。

```cpp
// compile with: /clr
#using "type_member_visibility_2.dll"
using namespace System;
// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Public_Function();
      Public_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();

   // call protected functions
   b->Test();

   // can't be called outside the assembly
   // a->Private_Function();
   // a->Internal_Function();
   // a->Protected_Private_Function();
   // a->Private_Protected_Function();
}
```

**输出**

```Output
in Public_Function
=======================
in function of derived class
in Protected_Function
in Protected_Public_Function
in Public_Protected_Function
exiting function of derived class
=======================
```

##  <a name="BKMK_Public_and_private_native_classes"></a> 公钥和私钥的本机类

可以从托管类型中引用的本机类型。  例如，托管类型中的函数可以采用参数的类型为本机结构。  如果公共程序集中的托管的类型和函数，然后在本机类型还必须公共。

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

接下来，创建使用本机类型的源的代码文件：

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

现在，编译客户端：

```cpp
// compile with: /clr
#using "mcppv2_ref_class3.dll"

#include "mcppv2_ref_class3.h"

int main() {
   R ^r = gcnew R;
   N n;
   r->f(n);
}
```

##  <a name="BKMK_Static_constructors"></a>静态构造函数

CLR 类型，例如，类或结构，可以具有可用于初始化静态数据成员的静态构造函数。  静态构造函数调用最多一次，并在第一次访问类型的任何静态成员之前调用。

实例构造函数始终在静态构造函数之后运行。

如果类具有静态构造函数，编译器不能内联构造函数的调用。  如果类是值类型的、 具有静态构造函数，并且不包含实例构造函数，编译器不能内联到任何成员函数的调用。  CLR 可以内联调用，但编译器不能。

作为私有成员函数，定义静态构造函数，因为它旨在只能由 CLR 调用。

有关静态构造函数的详细信息，请参阅[如何：定义接口静态构造函数 (C++/CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 。

```cpp
// compile with: /clr
using namespace System;

ref class MyClass {
private:
   static int i = 0;

   static MyClass() {
      Console::WriteLine("in static constructor");
      i = 9;
   }

public:
   static void Test() {
      i++;
      Console::WriteLine(i);
   }
};

int main() {
   MyClass::Test();
   MyClass::Test();
}
```

**输出**

```Output
in static constructor
10
11
```

##  <a name="BKMK_Semantics_of_the_this_pointer"></a> 语义的 this 指针

使用视觉对象时C++定义类型，`this`中引用类型的指针为类型"句柄"。 `this`在值类型的指针为类型"内部指针"。

这些不同的语义的`this`调用默认索引器时，指针可能会导致意外的行为。 下面的示例演示访问默认索引器 ref 类型和值类型中的正确方法。

有关详细信息，请参见

- [对象句柄运算符 (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md)

```cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      // accessing default indexer
      Console::WriteLine("{0}", this[3.3]);
   }
};

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      // accessing default indexer
      Console::WriteLine("{0}", this->default[3.3]);
   }
};

int main() {
   A ^ mya = gcnew A();
   B ^ myb = gcnew B();
   myb->Test();
}
```

**输出**

```Output
10.89
10.89
```

##  <a name="BKMK_Hide_by_signature_functions"></a> 按签名隐藏函数

在标准C++，即使该派生类函数不具有相同数量或类型的参数，在派生类中，具有相同名称的函数被隐藏基类中的函数。 这被称为*按名称隐藏*语义。 在引用类型，在基类中的函数可以仅隐藏由派生类中的函数如果的名称和参数列表相同。 这称为*按签名隐藏*语义。

类被视为按签名隐藏类，其所有功能都作为元数据中标记为`hidebysig`。 默认情况下，将创建的所有类 **/clr**具有`hidebysig`函数。 当一个类具有`hidebysig`函数，编译器不会在任何直接的基类中按名称隐藏函数，但如果编译器遇到继承链中的一个按名称隐藏类，它仍然按名称隐藏该行为。

按签名隐藏语义下对一个对象，调用函数时编译器标识包含无法满足函数调用的函数的派生程度最高的类。 如果无法满足该调用的类中只有一个函数，编译器将调用该函数。 如果无法满足该调用的类中存在多个函数，编译器使用重载决策规则来确定要调用的函数。 有关重载规则的详细信息，请参阅[函数重载](../cpp/function-overloading.md)。

对于给定的函数调用中，在基类中的函数可能必须使其成为派生类中的略有更好的匹配比函数的签名。 但是，如果在派生类的对象上显式调用该函数，被调用派生类中的函数。

因为返回值不被视为函数的签名的一部分，基类函数是隐藏如果它具有相同的名称，并为派生类函数，采用的相同数量和类型的自变量，即使它在返回值的类型不同。

下面的示例显示了由派生类中的函数不会隐藏基类中的函数。

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test() {
      Console::WriteLine("Base::Test");
   }
};

ref struct Derived : public Base {
   void Test(int i) {
      Console::WriteLine("Derived::Test");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Test() in the base class will not be hidden
   t->Test();
}
```

**输出**

```Output
Base::Test
```

下一步的示例演示在 MicrosoftC++编译器调用的函数派生程度最高的类中 — 即使需要转换，以匹配一个或多个参数，并不是函数调用的更好地匹配项的基类中调用函数。

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test2(Single d) {
      Console::WriteLine("Base::Test2");
   }
};

ref struct Derived : public Base {
   void Test2(Double f) {
      Console::WriteLine("Derived::Test2");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Base::Test2 is a better match, but the compiler
   // calls a function in the derived class if possible
   t->Test2(3.14f);
}
```

**输出**

```Output
Derived::Test2
```

下面的示例演示就可以隐藏函数，即使基本类具有与派生的类相同的签名。

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   int Test4() {
      Console::WriteLine("Base::Test4");
      return 9;
   }
};

ref struct Derived : public Base {
   char Test4() {
      Console::WriteLine("Derived::Test4");
      return 'a';
   }
};

int main() {
   Derived ^ t = gcnew Derived;

   // Base::Test4 is hidden
   int i = t->Test4();
   Console::WriteLine(i);
}
```

**输出**

```Output
Derived::Test4
97
```

##  <a name="BKMK_Copy_constructors"></a> 复制构造函数

C++标准规定当移动对象，以便对对象进行创建和销毁在相同的地址时，调用复制构造函数。

但是，当 **/clr**用于编译和编译为 MSIL 调用本机函数的本机类的函数，或多个-传递的值，其中的本机类具有一个复制构造函数和/或析构函数，没有复制调用构造函数和对象被销毁后，在与创建它时所在不同的地址。 如果类具有到自身，指针或代码的地址跟踪对象，这可能导致问题。

有关详细信息，请参阅 [/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。

下面的示例演示时不生成复制构造函数。

```cpp
// compile with: /clr
#include<stdio.h>

struct S {
   int i;
   static int n;

   S() : i(n++) {
      printf_s("S object %d being constructed, this=%p\n", i, this);
   }

   S(S const& rhs) : i(n++) {
      printf_s("S object %d being copy constructed from S object "
               "%d, this=%p\n", i, rhs.i, this);
   }

   ~S() {
      printf_s("S object %d being destroyed, this=%p\n", i, this);
   }
};

int S::n = 0;

#pragma managed(push,off)
void f(S s1, S s2) {
   printf_s("in function f\n");
}
#pragma managed(pop)

int main() {
   S s;
   S t;
   f(s,t);
}
```

**输出**

```Output
S object 0 being constructed, this=0018F378
S object 1 being constructed, this=0018F37C
S object 2 being copy constructed from S object 1, this=0018F380
S object 3 being copy constructed from S object 0, this=0018F384
S object 4 being copy constructed from S object 2, this=0018F2E4
S object 2 being destroyed, this=0018F380
S object 5 being copy constructed from S object 3, this=0018F2E0
S object 3 being destroyed, this=0018F384
in function f
S object 5 being destroyed, this=0018F2E0
S object 4 being destroyed, this=0018F2E4
S object 1 being destroyed, this=0018F37C
S object 0 being destroyed, this=0018F378
```

##  <a name="BKMK_Destructors_and_finalizers"></a> 析构函数和终结器

引用类型中的析构函数执行确定性清理的资源。 终结器清理非托管资源，析构函数或不确定地由垃圾回收器可以明确地调用。 有关标准中的析构函数的信息C++，请参阅[析构函数](../cpp/destructors-cpp.md)。

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

托管的视觉对象中的析构函数的行为C++类不同于托管扩展C++。 有关此更改的详细信息，请参阅[析构函数语义的更改](../dotnet/changes-in-destructor-semantics.md)。

CLR 垃圾回收器删除未使用的托管的对象，并在不再需要时释放其内存。 但是，一种类型可能会使用垃圾回收器不知道如何释放的资源。 这些资源称为非托管资源 （例如本机文件处理）。 我们建议在发布的终结器中的所有非托管的资源。 因为垃圾回收器不确定地释放托管的资源，是不安全，请参阅对托管资源，在终结器因为可能有垃圾回收器已清除该托管资源。

视觉对象C++终结器不与相同<xref:System.Object.Finalize%2A>方法。 (CLR 文档使用终结器和<xref:System.Object.Finalize%2A>方法同义词)。 <xref:System.Object.Finalize%2A>垃圾回收器，它调用类的继承链中每个终结器调用方法。 与不同的视觉对象C++析构函数，派生类终结器调用不会导致编译器将调用所有基类中的终结器。

因为 MicrosoftC++编译器支持的资源的确定性释放，请勿尝试实现<xref:System.IDisposable.Dispose%2A>或<xref:System.Object.Finalize%2A>方法。 但是，如果您熟悉这些方法，下面是一个视觉对象C++终结器和析构函数调用终结器将映射到<xref:System.IDisposable.Dispose%2A>模式：

```cpp
// Visual C++ code
ref class T {
   ~T() { this->!T(); }   // destructor calls finalizer
   !T() {}   // finalizer
};

// equivalent to the Dispose pattern
void Dispose(bool disposing) {
   if (disposing) {
      ~T();
   } else {
      !T();
   }
}
```

托管的类型还可以使用您希望具有确定性，发布，而不将留给垃圾回收器不再需要对象后，系统不确定地释放在某个时间点的托管的资源。 资源的确定性释放可以显著提高性能。

MicrosoftC++编译器使您能够以明确地清理对象的析构函数的定义。 使用析构函数释放要明确地释放的所有资源。  如果存在一个终结器，则请从析构函数，以避免代码重复调用它。

```cpp
// compile with: /clr /c
ref struct A {
   // destructor cleans up all resources
   ~A() {
      // clean up code to release managed resource
      // ...
      // to avoid code duplication,
      // call finalizer to release unmanaged resources
      this->!A();
   }

   // finalizer cleans up unmanaged resources
   // destructor or garbage collector will
   // clean up managed resources
   !A() {
      // clean up code to release unmanaged resources
      // ...
   }
};
```

如果使用你的类型的代码未调用析构函数时，垃圾回收器最终释放所有托管的资源。

析构函数存在并不表示终结器存在。 但是，终结器的出现意味着，必须定义析构函数，并从该析构函数调用的终结器。 这提供了非托管资源的确定性释放。

调用析构函数取消 — 通过使用<xref:System.GC.SuppressFinalize%2A>— 终结的对象。 如果未调用析构函数，则最终将由垃圾回收器调用类型的终结器。

明确地清理对象的资源通过调用析构函数可以提高性能与让 CLR 以非确定性终结该对象进行比较。

视觉对象中编写的代码C++并使用编译的 **/clr**如果运行类型的析构函数：

- 通过使用堆栈语义创建的对象超出范围。 有关详细信息，请参阅[C++引用类型的堆栈语义](../dotnet/cpp-stack-semantics-for-reference-types.md)。

- 在对象的构造期间引发异常。

- 该对象是运行其析构函数的对象中的成员。

- 在调用[删除](../cpp/delete-operator-cpp.md)句柄运算符 ([对象句柄运算符 (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md))。

- 显式调用析构函数。

如果您的类型由以另一种语言编写的客户端，析构函数调用，如下所示：

- 在调用<xref:System.IDisposable.Dispose%2A>。

- 在调用`Dispose(void)`类型上。

- 如果不在 C# 中的范围之内类型`using`语句。

如果 （不引用类型使用堆栈语义） 在托管堆上创建引用类型的对象，请使用[的 try-finally](../cpp/try-finally-statement.md)语法以确保异常不会运行阻止析构函数。

```cpp
// compile with: /clr
ref struct A {
   ~A() {}
};

int main() {
   A ^ MyA = gcnew A;
   try {
      // use MyA
   }
   finally {
      delete MyA;
   }
}
```

如果您的类型具有析构函数，编译器将生成`Dispose`方法，实现<xref:System.IDisposable>。 如果编写视觉对象中的类型C++和具有从另一种语言，使用析构函数调用`IDisposable::Dispose`对该类型将导致该类型的析构函数调用。 当类型使用从视觉对象C++客户端，不能直接调用`Dispose`; 相反，通过调用其析构函数`delete`运算符。

如果您的类型有终结器，编译器将生成`Finalize(void)`方法来重写<xref:System.Object.Finalize%2A>。

如果类型具有终结器或析构函数，编译器将生成`Dispose(bool)`方法，根据设计模式。 (有关信息，请参阅[Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern))。 不能显式创作或调用`Dispose(bool)`视觉对象中C++。

如果类型具有一个基类，它符合设计模式，时会调用派生类的析构函数调用的所有基类的析构函数。 (如果您的类型编写视觉对象中C++，编译器可确保您的类型实现此模式。)换而言之，引用类的析构函数链接到其基类和成员由指定C++标准 — 类的析构函数为运行，则在相反的顺序在其中它们的创建过程，其成员的析构函数的第一个和最后在构造它们的顺序相反其基类的析构函数。

析构函数和终结器不允许在值类型或接口中。

只能定义或引用类型中声明终结器。 与构造函数和析构函数中，终结器有没有返回类型。

对象的终结器运行后，在任何基类中的终结器也称为，开头的派生程度最低的类型。 数据成员的终结器不会自动链接到类的终结器。

如果终结器中删除的托管类型中的本机指针，则必须确保，不会过早地收集到或通过本机指针的引用;而不是使用的托管类型上调用析构函数<xref:System.GC.KeepAlive%2A>。

在编译时，可以检测类型是否具有终结器或析构函数。 有关详细信息，请参阅[编译器支持类型特征](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)。

下一个示例演示两种类型，一个具有非托管的资源，一个具有托管确定性地释放的资源。

```cpp
// compile with: /clr
#include <vcclr.h>
#include <stdio.h>
using namespace System;
using namespace System::IO;

ref class SystemFileWriter {
   FileStream ^ file;
   array<Byte> ^ arr;
   int bufLen;

public:
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),
                                     arr(gcnew array<Byte>(1024)) {}

   void Flush() {
      file->Write(arr, 0, bufLen);
      bufLen = 0;
   }

   ~SystemFileWriter() {
      Flush();
      delete file;
   }
};

ref class CRTFileWriter {
   FILE * file;
   array<Byte> ^ arr;
   int bufLen;

   static FILE * getFile(String ^ n) {
      pin_ptr<const wchar_t> name = PtrToStringChars(n);
      FILE * ret = 0;
      _wfopen_s(&ret, name, L"ab");
      return ret;
   }

public:
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}

   void Flush() {
      pin_ptr<Byte> buf = &arr[0];
      fwrite(buf, 1, bufLen, file);
      bufLen = 0;
   }

   ~CRTFileWriter() {
      this->!CRTFileWriter();
   }

   !CRTFileWriter() {
      Flush();
      fclose(file);
   }
};

int main() {
   SystemFileWriter w("systest.txt");
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");
}
```

## <a name="see-also"></a>请参阅

[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)
