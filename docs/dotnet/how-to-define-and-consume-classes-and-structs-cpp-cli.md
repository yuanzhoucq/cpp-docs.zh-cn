---
title: 如何：定义和使用类和结构 (C++/CLI)
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5bec92ce2bd97f11723cdf59c58b7331b39565f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370181"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>如何：定义和使用类和结构 (C++/CLI)

本文演示如何在C++/CLI中定义和使用用户定义的引用类型和值类型。

## <a name="contents"></a><a name="BKMK_Contents"></a>内容

[对象实例化](#BKMK_Object_instantiation)

[隐式抽象类](#BKMK_Implicitly_abstract_classes)

[类型可见性](#BKMK_Type_visibility)

[成员可见性](#BKMK_Member_visibility)

[公共和私有本机类](#BKMK_Public_and_private_native_classes)

[静态构造函数](#BKMK_Static_constructors)

[此指针的语义](#BKMK_Semantics_of_the_this_pointer)

[按签名隐藏功能](#BKMK_Hide_by_signature_functions)

[复制构造函数](#BKMK_Copy_constructors)

[析构函数和终结器](#BKMK_Destructors_and_finalizers)

## <a name="object-instantiation"></a><a name="BKMK_Object_instantiation"></a>对象实例化

引用（ref） 类型只能在托管堆上实例化，只能在堆栈上或本机堆上实例化。 值类型可以在堆栈或托管堆上实例化。

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

## <a name="implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a>隐式抽象类

无法实例化*隐式抽象类*。 如果类的基类型是接口，并且类未实现接口的所有成员函数，则类是隐式抽象的。

如果无法从从接口派生的类构造对象，原因可能是该类是隐式抽象的。 有关抽象类的详细信息，请参阅[抽象](../extensions/abstract-cpp-component-extensions.md)。

以下代码示例演示了由于函数`MyClass``MyClass::func2`未实现而无法实例化类。 要使示例编译，请取消注释`MyClass::func2`。

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

## <a name="type-visibility"></a><a name="BKMK_Type_visibility"></a>类型可见性

您可以控制通用语言运行时 （CLR） 类型的可见性，以便在引用程序集时，程序集中的类型可以在程序集外部可见或不可见。

`public`指示类型对包含该类型的程序集的`#using`指令的任何源文件都可见。  `private`指示类型对于包含该类型的程序集的`#using`指令的源文件不可见。 但是，私有类型在同一程序集中可见。 默认情况下，类的可见性为`private`。

默认情况下，在 Visual Studio 2005 之前，本机类型具有程序集外部的公共可访问性。 启用[编译器警告（级别 1） C4692，](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)以帮助您查看私有本机类型的使用不正确的位置。 使用[make_public](../preprocessor/make-public.md)实用新型为源代码文件中无法修改的本机类型提供公共可访问。

有关详细信息，请参阅 [#using 指令](../preprocessor/hash-using-directive-cpp.md)。

下面的示例演示如何声明类型并指定其可访问性，然后在程序集中访问这些类型。 当然，如果使用 引用具有私有类型的程序集`#using`，则只有程序集中的公共类型可见。

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

现在，让我们重写前面的示例，以便将其构建为 DLL。

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

下一个示例演示如何访问程序集外部的类型。 在此示例中，客户端使用上一个示例中生成的组件。

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

## <a name="member-visibility"></a><a name="BKMK_Member_visibility"></a>成员可见性

您可以使用访问指定器`public`对 ，使从同一程序集中访问公共类的成员不同于从程序集外部访问公共类的成员。 `protected``private`

下表总结了各种访问指定器的效果：

|说明符|效果|
|---------------|------------|
|public|成员可在程序集内外访问。  有关详细信息，请参阅[公众](../cpp/public-cpp.md)。|
|private|成员不可访问，无论是在程序集内部还是外部。  有关详细信息，请参阅[私有](../cpp/private-cpp.md)。|
|protected|成员可在程序集内外访问，但只能访问派生类型。  有关详细信息，请参阅[受保护](../cpp/protected-cpp.md)。|
|internal|成员在程序集内是公共的，但在程序集外部是私有的。  `internal` 是上下文相关的关键字。  有关详细信息，请参阅[上下文相关关键字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。|
|公共保护-或受保护的公众|成员在程序集内是公共的，但在程序集外部受到保护。|
|私有保护 -或受保护的私有|成员在程序集内受到保护，但在程序集外部是私有的。|

下面的示例显示了一种公共类型，该类型具有使用不同的访问权限声明的成员，然后显示这些成员从程序集内访问。

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

现在，让我们将前面的示例构建为 DLL。

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

以下示例使用在前一个示例中创建的组件，从而演示如何从程序集外部访问成员。

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

## <a name="public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a>公共和私有本机类

可以从托管类型引用本机类型。  例如，托管类型的函数可以采用其类型为本机结构的参数。  如果托管类型和函数在程序集中是公共的，则本机类型也必须为公共类型。

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

接下来，创建使用本机类型的源代码文件：

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

## <a name="static-constructors"></a><a name="BKMK_Static_constructors"></a>静态构造函数

CLR 类型（例如类或结构）可以具有可用于初始化静态数据成员的静态构造函数。  静态构造函数最多调用一次，并在首次访问类型的任何静态成员之前调用。

实例构造函数始终在静态构造函数之后运行。

如果类具有静态构造函数，编译器不能将调用内联到构造函数。  如果类是值类型、具有静态构造函数并且没有实例构造函数，则编译器不能将调用内联到任何成员函数。  CLR 可以内联调用，但编译器不能。

将静态构造函数定义为私有成员函数，因为它仅由 CLR 调用。

有关静态构造函数的详细信息，请参阅[如何：定义接口静态构造函数 （C++/CLI）。](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

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

## <a name="semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a>此指针的语义

使用 Visual C++定义类型时，`this`引用类型的指针的类型为"句柄"。 值`this`类型的指针为"内部指针"类型。

当调用默认索引器时`this`，指针的这些不同语义可能会导致意外行为。 下一个示例显示了在 ref 类型和值类型中访问默认索引器的正确方法。

有关详细信息，请参阅

- [句柄到对象运算符 （*）](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr（C++/CLI）](../extensions/interior-ptr-cpp-cli.md)

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

## <a name="hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a>按签名隐藏功能

在标准C++中，基类中的函数由派生类中具有相同名称的函数隐藏，即使派生类函数的参数数量或类型不同。 这称为 *"逐名隐藏*"语义。 在引用类型中，如果名称和参数列表相同，则基类中的函数只能由派生类中的函数隐藏。 这称为 *"按签名隐藏*"语义。

当类的所有函数在元数据中标记为`hidebysig`时，类被视为按签名隐藏类。 默认情况下，在 **/clr**下创建的所有类都有`hidebysig`函数。 当类具有`hidebysig`函数时，编译器不会在任何直接基类中按名称隐藏函数，但如果编译器在继承链中遇到逐名隐藏类，则它将继续这种逐个名称隐藏行为。

在"逐个签名"语义下，当在对象上调用函数时，编译器标识包含可满足函数调用的函数的最派生类。 如果类中只有一个函数可以满足调用，编译器将调用该函数。 如果类中有多个函数可以满足调用，编译器将使用重载解析规则来确定调用哪个函数。 有关重载规则的详细信息，请参阅[函数重载](../cpp/function-overloading.md)。

对于给定的函数调用，基类中的函数可能具有一个签名，使其比派生类中的函数稍微匹配一些。 但是，如果在派生类的对象上显式调用该函数，则调用派生类中的函数。

由于返回值不被视为函数签名的一部分，因此，如果基类函数具有相同的名称，并且采用与派生类函数相同的数量和类型的参数，即使它在返回值的类型上有所不同，则隐藏该函数。

下面的示例显示基类中的函数不被派生类中的函数隐藏。

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

下一个示例显示 Microsoft C++编译器调用派生最多的类中的函数，即使需要转换以匹配一个或多个参数，也不会调用基类中更适合函数调用的函数。

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

下面的示例显示，即使基类具有与派生类相同的签名，也可以隐藏函数。

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

## <a name="copy-constructors"></a><a name="BKMK_Copy_constructors"></a>复制构造函数

C++标准表示，在移动对象时调用复制构造函数，以便在同一地址创建和销毁对象。

但是，当 **/clr**用于编译，编译到 MSIL 的函数调用本机函数，其中本机类（或多个类）通过值传递，而本机类具有复制构造函数和/或析构函数，则不调用任何复制构造函数，并且对象在创建位置不同的地址被销毁。 如果类本身有指针，或者代码按地址跟踪对象，则可能会导致问题。

有关更多信息，请参见 [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md)。

以下示例演示如何生成复制构造函数。

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

## <a name="destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a>析构函数和终结器

引用类型的析构函数执行资源确定性清理。 终结器清理非托管资源，并且可以由析构函数或垃圾回收器在确定性上调用确定性资源。 有关标准C++中的析构函数的信息，请参阅[析构函数](../cpp/destructors-cpp.md)。

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

托管 Visual C++ 类中的析构函数的行为不同于 C++的托管扩展。 有关此更改的详细信息，请参阅[析构函数语义中的更改](../dotnet/changes-in-destructor-semantics.md)。

CLR 垃圾回收器删除未使用的托管对象，并在不再需要它们时释放其内存。 但是，类型可能使用垃圾回收器不知道如何释放的资源。 这些资源称为非托管资源（例如本机文件句柄）。 我们建议您释放终结器中的所有非托管资源。 由于托管资源由垃圾回收器非确定性地释放，因此在终结器中引用托管资源不安全，因为垃圾回收器可能已清理该托管资源。

可视化C++终结器与<xref:System.Object.Finalize%2A>方法不同。 （CLR 文档使用终结器和方法<xref:System.Object.Finalize%2A>同义）。 垃圾<xref:System.Object.Finalize%2A>回收器调用该方法，它调用类继承链中的每个终结器。 与 Visual C++析构函数不同，派生类终结器调用不会导致编译器调用所有基类中的终结器。

由于 Microsoft C++编译器支持资源确定性释放，因此不要尝试实现 或<xref:System.IDisposable.Dispose%2A><xref:System.Object.Finalize%2A>方法。 但是，如果您熟悉这些方法，下面是 Visual C++终结器和将终结器映射调用<xref:System.IDisposable.Dispose%2A>模式的析构函数的方式：

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

托管类型还可以使用您希望以确定性方式释放的托管资源，而不是让垃圾回收器在不再需要对象后的某个时间点以非确定性方式释放。 确定性资源释放可以显著提高性能。

Microsoft C++编译器使析构函数的定义能够确定清理对象。 使用析构函数释放要确定释放的所有资源。  如果存在终结器，请从析构函数调用它，以避免代码重复。

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

如果使用您的类型的代码不调用析构函数，则垃圾回收器最终将释放所有托管资源。

析构函数的存在并不意味着存在终结器。 但是，终结器的存在意味着您必须定义析构函数并从该析构函数调用终结器。 这提供了非托管资源的确定性释放。

调用析构函数会通过对象的<xref:System.GC.SuppressFinalize%2A>"定稿"来抑制。 如果未调用析构函数，则垃圾回收器最终将调用类型的终结器。

与让 CLR 非确定性地完成对象相比，通过调用析构函数来确定清理对象的资源可以提高性能。

在 Visual C++ 中编写并使用 **/clr**编译的代码在：

- 使用堆栈语义创建的对象超出范围。 有关详细信息，请参阅[C++堆栈语义的引用类型](../dotnet/cpp-stack-semantics-for-reference-types.md)。

- 在对象的构造期间引发异常。

- 该对象是正在运行析构函数的对象中的成员。

- 在句柄上调用[删除](../cpp/delete-operator-cpp.md)运算符 （[句柄到对象运算符 （*）。](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- 显式调用析构函数。

如果类型被用其他语言编写的客户端使用，则析构函数的调用方式如下：

- 在呼叫<xref:System.IDisposable.Dispose%2A>时。

- 在类型`Dispose(void)`上的调用。

- 如果类型超出 C#`using`语句的范围。

如果在托管堆上创建引用类型的对象（不对引用类型使用堆栈语义），请使用[尝试-finally](../cpp/try-finally-statement.md)语法来确保异常不会阻止析构函数运行。

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

如果类型具有析构函数，编译器将生成实现`Dispose`<xref:System.IDisposable>的方法。 如果以 Visual C++编写的类型具有从另一种语言消耗的析构函数，则调用`IDisposable::Dispose`该类型会导致调用该类型的析构函数。 当类型从 Visual C++ 客户端使用时，不能直接调用`Dispose`;相反，使用`delete`运算符调用析构函数。

如果类型具有终结器，编译器将生成一个`Finalize(void)`重写<xref:System.Object.Finalize%2A>的方法。

如果类型具有终结器或析构函数，编译器将根据设计模式生成方法`Dispose(bool)`。 （有关信息，请参阅[处置模式](/dotnet/standard/design-guidelines/dispose-pattern)。 您不能在 Visual C++中`Dispose(bool)`显式创作或调用。

如果类型具有符合设计模式的基类，则当调用派生类的析构函数时，将调用所有基类的析构函数。 （如果类型是在 Visual C++中编写的，编译器将确保类型实现此模式。换句话说，引用类的析构函数按C++标准指定，链到其基和成员，首先运行类的析构函数，然后按其构造顺序相反的成员的析构函数，最后以其基类的析构函数按其构造顺序的相反运行。

不允许在值类型或接口内使用析构函数和终结器。

只能以引用类型定义或声明终结器。 与构造函数和析构函数一样，终结器没有返回类型。

运行对象的终结器后，还会调用任何基类中的终结器，从派生最少的类型开始。 数据成员的终结者不会由类的终结器自动链接到。

如果终结器删除托管类型的本机指针，则必须确保不会过早地收集对本机指针的引用或通过本机指针收集的引用;否则，将不过早地收集对本机指针的引用。调用托管类型的析构函数，而不是使用<xref:System.GC.KeepAlive%2A>。

在编译时，可以检测类型是具有终结器还是析构函数。 有关详细信息，请参阅[编译器对类型特征的支持](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)。

下一个示例显示两种类型，一种具有非托管资源，另一种具有具有确定性释放的托管资源。

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

## <a name="see-also"></a>另请参阅

[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)
