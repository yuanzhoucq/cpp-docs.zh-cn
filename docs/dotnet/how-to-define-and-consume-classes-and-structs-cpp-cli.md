---
title: 如何： 定义和使用类和结构 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d8356d96b0193566814c0d52173a03a3a79d08d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>如何：定义和使用类和结构 (C++/CLI)
这篇文章演示如何定义和使用用户定义的引用类型和值类型在 C + + /cli CLI。  
  
##  <a name="BKMK_Contents"></a> 内容  
 [对象实例化](#BKMK_Object_instantiation)  
  
 [隐式抽象类](#BKMK_Implicitly_abstract_classes)  
  
 [类型可见性](#BKMK_Type_visibility)  
  
 [成员的可见性](#BKMK_Member_visibility)  
  
 [公钥和私钥的本机类](#BKMK_Public_and_private_native_classes)  
  
 [静态构造函数](#BKMK_Static_constructors)  
  
 [语义 this 指针](#BKMK_Semantics_of_the_this_pointer)  
  
 [按签名隐藏函数](#BKMK_Hide_by_signature_functions)  
  
 [复制构造函数](#BKMK_Copy_constructors)  
  
 [析构函数和终结器](#BKMK_Destructors_and_finalizers)  
  
##  <a name="BKMK_Object_instantiation"></a> 对象实例化  
 引用 (ref) 类型和值类型可以仅实例化托管堆上、 不在堆栈上或本机堆上。  
  
```  
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
 *隐式抽象类*不能实例化。 类是隐式抽象的如果类的基类型是一个接口和类未实现所有接口的成员函数。  
  
 如果你不能构造从接口派生的类中的对象，原因可能是此类是隐式抽象。 有关抽象类的详细信息，请参阅[抽象](../windows/abstract-cpp-component-extensions.md)。  
  
 下面的代码示例演示`MyClass`类不能实例化，因为函数`MyClass::func2`未实现。 若要启用编译该示例，请取消注释`MyClass::func2`。  
  
```  
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
 你可以控制的可见性公共语言运行时 (CLR) 类型，以便引用程序集，如果程序集中的类型可以是可见或程序集外部不可见。  
  
 `public` 指示类型是否可见的包含任何源文件`#using`指令包含的类型的程序集。  `private` 指示的类型不是可见的包含的源文件`#using`指令包含的类型的程序集。 但是，是在同一程序集内可见的私有类型。 默认情况下，类的可见性是`private`。  
  
 默认情况下，在 Visual c + + 2005年之前，本机类型具有程序集外部的公共可访问性。 启用[编译器警告 （等级 1） C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)以帮助您查看私有本机类型使用不正确。 使用[make_public](../preprocessor/make-public.md)杂注不能修改源代码文件中的本机类型提供公共可访问性。  
  
 有关详细信息，请参阅[#using 指令](../preprocessor/hash-using-directive-cpp.md)。  
  
 下面的示例演示如何声明类型，指定可访问性，，然后访问这些类型在程序集中。 当然，如果具有私有类型的程序集引用使用`#using`，则只在程序集中的公共类型可见。  
  
```  
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
  
 现在，让我们重写前面的示例，以便生成为 DLL。  
  
```  
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
  
 下一个示例演示如何访问程序集外部的类型。 在此示例中，客户端使用在前面的示例生成的组件。  
  
```  
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
 你可以访问从同一程序集中是公共类的成员不同于访问至该程序集外部使用的访问说明符对`public`， `protected`，和 `private`  
  
 下表汇总了各种访问说明符的效果：  
  
|说明符|效果|  
|---------------|------------|  
|public|成员是可访问内部和外部程序集。  请参阅[公共](../cpp/public-cpp.md)有关详细信息。|  
|private|成员无法访问，则内部和外部程序集都不。  请参阅[私有](../cpp/private-cpp.md)有关详细信息。|  
|protected|成员是可访问内部和外部程序集，而只是派生类型。  请参阅[保护](../cpp/protected-cpp.md)有关详细信息。|  
|internal|成员是公开的程序集内但私有程序集外部的。  `internal` 是上下文相关的关键字。  有关详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。|  
|公共受保护-或-受保护公共|成员是公开的程序集内但程序集外部的受保护。|  
|私有受保护-或-受保护的私有|成员是受保护的程序集内，但私有程序集外部的。|  
  
 下面的示例演示已使用不同的可访问性，声明的成员的公共类型，并随后显示的程序集内从这些成员访问。  
  
```  
  
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
  
 现在让我们生成为 DLL 前面的示例。  
  
```  
  
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
  
 下面的示例使用在前面的示例中，创建并从而演示如何访问程序集外部的成员的组件。  
  
```  
  
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
 可以从托管类型引用本机类型。  例如，托管类型中的函数可能需要其类型是一个本机结构的参数。  如果托管的类型和函数在是公共的程序集，然后的本机类型还必须是公共。  
  
```  
  
// native type  
public struct N {  
   N(){}  
   int i;  
};  
```  
  
 接下来，创建使用的本机类型的源代码文件：  
  
```  
  
// compile with: /clr /LD  
#include "mcppv2_ref_class3.h"  
// public managed type  
public ref struct R {  
   // public function that takes a native type  
   void f(N nn) {}  
};  
```  
  
 现在，编译客户端：  
  
```  
  
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
 CLR 类型-例如，类或结构 — 可以具有可以用于静态数据成员进行初始化的静态构造函数。  静态构造函数调用最多一次，且第一次访问类型的任何静态成员之前调用。  
  
 实例构造函数始终静态构造函数之后运行。  
  
 如果类具有静态构造函数，编译器无法内联构造函数的调用。  如果类是值类型的、 具有静态构造函数，并且没有实例构造函数，编译器无法内联对任何成员函数的调用。  CLR 可能内联调用，但编译器不能。  
  
 为私有成员函数，定义静态构造函数，因为它旨在只能由 CLR 调用。  
  
 有关静态构造函数的详细信息，请参阅[如何： 定义接口静态构造函数 (C + + /cli CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 。  
  
```  
  
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
  
##  <a name="BKMK_Semantics_of_the_this_pointer"></a> 语义 this 指针  
 如果你使用 Visual c + + 定义类型，`this`中引用类型的指针为类型"句柄"。 `this`值类型的指针为类型"内部指针"。  
  
 这些不同的语义的`this`调用默认索引器时，指针可能导致意外的行为。 下面的示例演示访问默认索引器在 ref 类型和值类型的正确方法。  
  
 有关详细信息，请参见  
  
-   [对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)  
  
-   [interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)  
  
```  
  
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
 标准 c + + 中基的类中的函数是隐藏的在派生类中，具有相同名称的函数中，即使派生类函数不具有相同数量或类型的参数。 这称为*隐藏按名称*语义。 在引用类型，基类中的函数可以仅由隐藏派生类中的函数如果的名称和参数列表相同。 这称为*按签名隐藏*语义。  
  
 当所有其函数都作为元数据中标记时，类被认为按签名隐藏类`hidebysig`。 默认情况下创建的所有类 **/clr**具有`hidebysig`函数。 当类具有`hidebysig`函数，编译器不会隐藏函数按名称的任何直接的基类，但如果编译器遇到的继承链中的隐藏按名称类，它将继续该名称隐藏的行为。  
  
 在按签名隐藏语义下的对象，调用函数时编译器将标识包含无法满足函数调用的函数的派生程度最大的类。 如果无法满足调用类中只有一个函数，编译器将调用该函数。 如果无法满足调用类中没有多个函数，编译器使用重载决策规则来确定要调用的函数。 有关重载规则的详细信息，请参阅[函数重载](../cpp/function-overloading.md)。  
  
 对于给定的函数调用，基类中的函数可能必须使其成为派生类中比函数略有更好的匹配的签名。 但是，如果在派生类的对象上显式调用该函数，在派生类中的函数调用。  
  
 返回值不被视为函数的签名的一部分，因为基类函数是隐藏如果它具有相同的名称，并为派生类函数，采用相同的数量和类型的自变量，即使它在返回值的类型不同。  
  
 下面的示例演示派生类中的函数不被隐藏基类中的函数。  
  
```  
  
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
  
 下一个示例演示 Visual c + + 编译器最多衍生的类中调用一个函数 — 即使匹配一个或多个参数所需要的转换，并不是函数调用的更好地匹配项的基类中调用函数。  
  
```  
  
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
  
 下面的示例演示可以隐藏函数，即使该基类具有与派生的类相同的签名。  
  
```  
  
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
 C + + 标准规定，当一个对象被移动，以便对对象进行创建和销毁在相同的地址时调用复制构造函数。  
  
 但是，当 **/clr**用于编译和编译为 MSIL 调用本机函数的位置的本机类的函数-或多个-传递的值和其中本机类具有复制构造函数和/或析构函数，没有复制调用构造函数和对象被销毁位于比被创建时所在的不同地址。 如果类具有插入其本身，指针或代码由地址跟踪对象，这会导致问题。  
  
 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下面的示例演示如何在不生成复制构造函数。  
  
```  
  
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
 引用类型中的析构函数执行确定性清理的资源。 终结器清理非托管资源和的析构函数或不确定地垃圾回收器可以明确地调用。 有关标准 c + + 中的析构函数的信息，请参阅[析构函数](../cpp/destructors-cpp.md)。  
  
```  
class classname {  
   ~classname() {}   // destructor  
   ! classname() {}   // finalizer  
};  
```  
  
 中托管的 Visual c + + 类的析构函数的行为与不同于 c + + 托管扩展。 有关此更改的详细信息，请参阅[析构函数语义的更改](../dotnet/changes-in-destructor-semantics.md)。  
  
 CLR 垃圾回收器删除未使用的托管的对象，并在不再需要时释放其内存。 但是，一种类型可能使用垃圾回收器不知道如何来发布的资源。 这些资源称为非托管资源 （例如本机文件处理）。 我们建议你发布的终结器中的所有非托管的资源。 垃圾回收器不确定地释放托管的资源，因为它是不安全指在终结器中的托管资源因为可能会在垃圾回收器已清除该托管资源。  
  
 Visual c + + 终结器不与相同<xref:System.Object.Finalize%2A>方法。 (CLR 文档使用终结器和<xref:System.Object.Finalize%2A>方法作同义词)。 <xref:System.Object.Finalize%2A>方法由垃圾回收器，它调用类的继承链中每个终结器。 与 Visual c + + 析构函数，不同的派生类终结器调用不会导致编译器调用在所有基类中的终结器。  
  
 因为 Visual c + + 编译器支持的资源的确定性释放，请勿尝试实现<xref:System.IDisposable.Dispose%2A>或<xref:System.Object.Finalize%2A>方法。 但是，如果你熟悉这些方法，下面是一个 Visual c + + 的终结器和析构函数调用终结器如何映射到<xref:System.IDisposable.Dispose%2A>模式：  
  
```  
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
  
 托管的类型还可以使用您希望具有确定性，释放并不留给垃圾回收器不再需要对象后，系统不确定地释放在某个时间点的托管的资源。 资源的确定性释放可以显著提高性能。  
  
 Visual c + + 编译器使您能够以确定地清理对象析构函数的定义。 使用析构函数释放你想要确定地发布的所有资源。  如果存在终结器，则在从析构函数，以避免代码重复的情况下调用它。  
  
```  
  
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
  
 如果使用你的类型的代码不调用析构函数，垃圾回收器将最终释放所有的托管的资源。  
  
 析构函数的状态并不意味着终结器的状态。 但是，一个终结器的状态意味着，必须定义析构函数，并从该析构函数调用的终结器。 这提供非托管资源的确定性释放。  
  
 调用析构函数取消-通过使用<xref:System.GC.SuppressFinalize%2A>— 终结的对象。 如果未调用的析构函数，则最终将垃圾回收器调用类型的终结器。  
  
 确定地清理通过调用析构函数的对象的资源可以提高性能与让 CLR 不确定地完成对象进行比较。  
  
 在 Visual c + + 编写并使用编译的代码 **/clr**如果运行的类型的析构函数：  
  
-   使用堆栈语义创建的对象超出范围。 有关详细信息，请参阅[对于引用类型的 c + + 堆栈语义](../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
-   在对象的构造过程中引发异常。  
  
-   对象是运行其析构函数的对象中的成员。  
  
-   你调用[删除](../cpp/delete-operator-cpp.md)在句柄运算符 ([对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md))。  
  
-   显式调用析构函数。  
  
 如果你的类型所使用的另一种语言编写的客户端，析构函数调用，如下所示：  
  
-   在调用<xref:System.IDisposable.Dispose%2A>。  
  
-   在调用`Dispose(void)`类型上。  
  
-   如果类型超出作用域中的 C#`using`语句。  
  
 （不用于引用类型使用堆栈语义） 在托管堆上创建一个引用类型的对象，如果使用[的 try-finally](../cpp/try-finally-statement.md)语法以确保异常不会阻止从正在运行的析构函数。  
  
```  
  
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
  
 如果你的类型具有析构函数，编译器将生成`Dispose`实现的方法<xref:System.IDisposable>。 如果用 Visual c + + 编写的并具有析构函数，从另一种语言使用的类型，则调用`IDisposable::Dispose`在该类型会导致该类型的析构函数调用。 从 Visual c + + 客户端使用该类型时，不能直接调用`Dispose`; 相反，通过调用其析构函数`delete`运算符。  
  
 如果你的类型有终结器，编译器将生成`Finalize(void)`方法来重写<xref:System.Object.Finalize%2A>。  
  
 如果类型具有一个终结器或析构函数，编译器将生成`Dispose(bool)`方法，根据设计模式。 (有关信息，请参阅[释放模式](/dotnet/standard/design-guidelines/dispose-pattern))。 你不能显式创作或调用`Dispose(bool)`Visual c + +。  
  
 如果类型具有符合设计模式的基类，时会调用派生类的析构函数调用的所有基类析构函数。 （如果你的类型在 Visual c + + 编写的编译器可确保你的类型实现此模式。）换而言之，引用类的析构函数链接到其基项和由 c + + 标准指定的成员-类的析构函数是运行，然后按顺序它们已构造的顺序的相反的顺序及其成员的析构函数的第一个和最后在构造它们的顺序的相反值其基类的析构函数。  
  
 析构函数和终结器不允许在值类型或接口中。  
  
 只能定义或引用类型中声明终结器。 与构造函数和析构函数，一个终结器有没有返回类型。  
  
 对象的终结器运行后，在任何基类中的终结器也称为，开头至少派生的类型。 数据成员的终结器不会自动链接到的类的终结器。  
  
 如果终结器删除的托管类型中的本机指针，则必须确保，不会过早地收集或通过本机指针的引用;而不是使用托管类型上调用析构函数<xref:System.GC.KeepAlive%2A>。  
  
 在编译时，你可以检测类型是否具有终结器或析构函数。 有关详细信息，请参阅[编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 下一个示例演示两种类型，一个具有非托管的资源，一个具有托管确定地发布的资源。  
  
```  
  
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
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)   
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)