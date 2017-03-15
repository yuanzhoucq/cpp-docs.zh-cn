---
title: "如何︰ 定义和使用类和结构 (c + + CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "结构 [C++]"
  - "类 [C++], 实例化"
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：定义和使用类和结构 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文演示如何定义和使用用户定义的引用类型和中的值类型 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)]。  
  
##  <a name="a-namebkmkcontentsa-contents"></a><a name="BKMK_Contents"></a> 内容  
 [对象实例化](#BKMK_Object_instantiation)  
  
 [隐式抽象类](#BKMK_Implicitly_abstract_classes)  
  
 [类型可见性](#BKMK_Type_visibility)  
  
 [成员的可见性](#BKMK_Member_visibility)  
  
 [公钥和私钥的本机类](#BKMK_Public_and_private_native_classes)  
  
 [静态构造函数](#BKMK_Static_constructors)  
  
 [语义的此指针](#BKMK_Semantics_of_the_this_pointer)  
  
 [按签名隐藏函数](#BKMK_Hide_by_signature_functions)  
  
 [复制构造函数](#BKMK_Copy_constructors)  
  
 [析构函数和终结器](#BKMK_Destructors_and_finalizers)  
  
##  <a name="a-namebkmkobjectinstantiationa-object-instantiation"></a><a name="BKMK_Object_instantiation"></a> 对象实例化  
 引用 (ref) 类型和值类型可以只实例化托管堆上，不能在堆栈或本机堆上。  
  
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
  
##  <a name="a-namebkmkimplicitlyabstractclassesa-implicitly-abstract-classes"></a><a name="BKMK_Implicitly_abstract_classes"></a> 隐式抽象类  
  *隐式抽象类* 不能实例化。 如果类的基类型是一个接口和类未实现接口的成员函数的所有类为隐式抽象类。  
  
 如果您不能以构造从接口派生的类中的对象的原因可能是此类是隐式抽象。 有关抽象类的详细信息，请参阅 [抽象](../windows/abstract-cpp-component-extensions.md)。  
  
 下面的代码示例演示 `MyClass` 类不能实例化，因为函数 `MyClass::func2` 未实现。 若要启用要编译该示例，请取消注释 `MyClass::func2`。  
  
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
  
##  <a name="a-namebkmktypevisibilitya-type-visibility"></a><a name="BKMK_Type_visibility"></a> 类型可见性  
 这样，引用程序集，如果程序集中的类型可以可见或不可见程序集之外，您可以控制公共语言运行时 (CLR) 类型的可见的性。  
  
 `public` 表示一种类型包含任何源文件看到 `#using` 指令包含的类型的程序集。  `private` 表示一种类型不包含源文件看到 `#using` 指令包含的类型的程序集。 但是，专用类型都是可见的同一程序集中。 默认情况下，一个类的可见性是 `private`。  
  
 默认情况下，在 Visual c + + 2005年之前，本机类型必须在程序集外部的公共可访问性。 启用 [编译器警告 （等级 1） C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) 以帮助您查看私有本机类型使用不正确。 使用 [make_public](../preprocessor/make-public.md) 杂注可赋予您不能修改源代码文件中的本机类型的公共可访问性。  
  
 有关详细信息，请参阅 [#using 指令](../preprocessor/hash-using-directive-cpp.md)。  
  
 下面的示例演示如何声明类型和指定其可访问性，，然后访问这些类型在程序集中。 当然，如果具有私有类型的程序集引用使用 `#using`, ，则只在程序集中的公共类型都是可见。  
  
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
  
 现在，让我们重新编写前面的示例，以便建立作为 DLL。  
  
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
  
 下一个示例演示如何访问程序集之外的类型。 在此示例中，客户端使用在前面的示例生成的组件。  
  
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
  
##  <a name="a-namebkmkmembervisibilitya-member-visibility"></a><a name="BKMK_Member_visibility"></a> 成员的可见性  
 您可以使访问同一程序集中从一个公共类的成员对它在程序集外部访问与不同通过使用访问说明符对 `public`, ，`protected`, ，和 `private`  
  
 下表汇总了各种访问说明符的效果︰  
  
|说明符|效果|  
|---------------|------------|  
|public|成员是可访问内部和外部程序集。  请参阅 [公共](../cpp/public-cpp.md) 有关详细信息。|  
|private|成员无法访问，则内部和外部程序集都不。  请参阅 [专用](../cpp/private-cpp.md) 有关详细信息。|  
|protected|成员是可访问内部和外部程序集，而只是派生类型。  请参阅 [保护](../cpp/protected-cpp.md) 有关详细信息。|  
|internal|成员是公共程序集内，但专用程序集之外。  `internal` 是上下文相关的关键字。  有关详细信息，请参阅 [上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。|  
|公共受保护-或-受保护的公共|成员是公共程序集内，但在程序集外部受保护。|  
|私有受保护-或-受保护的私有|成员是受保护在程序集中，但专用程序集之外。|  
  
 下面的示例演示一个具有不同可访问性，用声明的成员的公共类型，，然后显示在程序集中从这些成员的访问。  
  
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
  
 现在让我们构建作为 DLL 前面的示例。  
  
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
  
 下面的示例使用在上一示例中，创建并从而演示如何访问的成员在程序集外部的组件。  
  
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
  
##  <a name="a-namebkmkpublicandprivatenativeclassesa-public-and-private-native-classes"></a><a name="BKMK_Public_and_private_native_classes"></a> 公钥和私钥的本机类  
 本机类型可以从托管类型引用。  例如，函数的托管类型中可使用其类型是一个本机结构的参数。  如果托管的类型和函数在是公共的程序集，然后的本机类型还必须公开。  
  
```  
  
// native type  
public struct N {  
   N(){}  
   int i;  
};  
```  
  
 接下来，创建使用本机类型的源代码文件︰  
  
```  
  
// compile with: /clr /LD  
#include "mcppv2_ref_class3.h"  
// public managed type  
public ref struct R {  
   // public function that takes a native type  
   void f(N nn) {}  
};  
```  
  
 现在，编译客户端︰  
  
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
  
##  <a name="a-namebkmkstaticconstructorsa-static-constructors"></a><a name="BKMK_Static_constructors"></a> 静态构造函数  
 CLR 类型 — 例如，类或结构，可以有一个可用于初始化静态数据成员的静态构造函数。  静态构造函数调用最多一次，并在第一次访问类型的任何静态成员之前调用。  
  
 静态构造函数后始终运行的实例构造函数。  
  
 如果类具有一个静态构造函数，编译器不能内联调用构造函数。  如果类是值类型、 具有静态构造函数，并且不具有实例构造函数，编译器不能内联对任何成员函数的调用。  CLR 可以内联调用，但编译器不能。  
  
 为私有成员函数，定义一个静态构造函数，因为它旨在只能由 CLR 调用。  
  
 有关静态构造函数的详细信息，请参阅 [如何︰ 定义接口静态构造函数 (C + + /cli CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md) 。  
  
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
  
##  <a name="a-namebkmksemanticsofthethispointera-semantics-of-the-this-pointer"></a><a name="BKMK_Semantics_of_the_this_pointer"></a> 语义的此指针  
 在使用 Visual c + + 来定义类型时, `this` 引用类型的指针为类型"句柄"。  `this` 在值类型的指针为类型"内部指针"。  
  
 这些不同的语义的 `this` 调用默认索引器时，指针会导致意外的行为。 下面的示例演示了访问 ref 类型和值类型中的默认索引器的正确方法。  
  
 有关详细信息，请参见  
  
-   [对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)  
  
-   [interior_ptr (C + + /cli CLI)](../windows/interior-ptr-cpp-cli.md)  
  
-   [如何︰ 使用索引属性](../misc/how-to-use-indexed-properties.md)  
  
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
  
##  <a name="a-namebkmkhidebysignaturefunctionsa-hide-by-signature-functions"></a><a name="BKMK_Hide_by_signature_functions"></a> 按签名隐藏函数  
 标准 c + + 中在基类中的函数是隐藏的派生类中具有相同名称的函数中，即使该派生类函数不具有相同数量或类型的参数。 这被称为 *按名称隐藏* 语义。 在为引用类型，在基类中的函数可以仅隐藏由派生类中的函数如果的名称和参数列表相同。 这称为 *按签名隐藏* 语义。  
  
 类被视为按签名隐藏类作为元数据中标记其所有功能时 `hidebysig`。 默认情况下，在下创建的所有类 **/clr** 具有 `hidebysig` 函数。 但是，通过使用编译的类 **/clr:oldSyntax** 没有 `hidebysig` 函数中; 相反，它们是按名称隐藏函数。 当类具有 `hidebysig` 函数，编译器不会在任何直接基类中按名称隐藏函数，但如果编译器遇到继承链中的按名称隐藏类，它仍然按名称隐藏该行为。  
  
 在按签名隐藏语义下的对象上调用函数时编译器将标识包含无法满足函数调用的函数的派生程度最大的类。 如果无法满足调用的类中只有一个函数，编译器将调用该函数。 如果无法满足调用的类中存在多个函数，编译器使用重载决策规则来确定要调用的函数。 有关重载规则的详细信息，请参阅 [函数重载](../cpp/function-overloading.md)。  
  
 对于给定的函数调用中，基类中的函数可能必须使其成为派生类中的略有更好的匹配比函数的签名。 但是，如果在派生类的对象上显式调用该函数，被调用派生类中的函数。  
  
 返回值不会考虑函数的签名的一部分，因为基类函数被隐藏如果它具有相同的名称，并为派生类函数，采用相同的数量和类型的参数，即使在返回值的类型不同。  
  
 下面的示例演示派生类中的函数未隐藏基类中的函数。  
  
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
  
 下一个示例演示 Visual c + + 编译器派生程度最高的类中调用一个函数，即使需要转换以匹配一个或多个参数 — 并不是函数调用的更好地匹配项的基类中调用函数。  
  
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
  
 下面的示例演示可以隐藏函数，即使类的基类派生的类相同的签名。  
  
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
  
 下面的示例定义一个组件，它通过编译 **/clr:oldSyntax**。 通过使用 c + + 托管扩展中定义的类，具有按名称隐藏成员函数。  
  
```  
  
// compile with: /clr:oldSyntax /LD  
using namespace System;  
public __gc struct Base0 {  
   void Test() {   
      Console::WriteLine("in Base0::Test");  
   }  
};  
  
public __gc struct Base1 : public Base0 {  
   void Test(int i) {   
      Console::WriteLine("in Base1::Test");  
   }  
};  
```  
  
 下一个示例使用在前面的示例生成的组件。 请注意隐藏按签名功能不应用于通过使用编译的类型的基类 **/clr:oldSyntax**。  
  
```  
  
// compile with: /clr:oldSyntax /LD  
// compile with: /clr  
using namespace System;  
#using "hide_by_signature_4.dll"  
  
ref struct Derived : public Base1 {  
   void Test(int i, int j) {   
      Console::WriteLine("Derived::Test");  
   }  
};  
  
int main() {  
   Derived ^ t = gcnew Derived;  
   t->Test(8, 8);   // OK  
   t->Test(8);   // OK  
   t->Test();   // C2661  
}  
```  
  
##  <a name="a-namebkmkcopyconstructorsa-copy-constructors"></a><a name="BKMK_Copy_constructors"></a> 复制构造函数  
 C + + 标准中提到，如果一个对象被移动，以便创建对象并将其销毁在相同的地址将调用复制构造函数。  
  
 但是，当 **/clr** 用于编译和编译为 MSIL 调用本机函数的位置的本机类的函数，或多个 — 通过值和其中本机类具有一个复制构造函数和/或析构函数，没有复制构造函数将调用且与在其上创建不同的地址在销毁该对象传递。 如果类具有一个指针，插入其本身，或者如果代码由地址跟踪对象，这可能导致问题。  
  
 有关更多信息，请参见 [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md)。  
  
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
  
##  <a name="a-namebkmkdestructorsandfinalizersa-destructors-and-finalizers"></a><a name="BKMK_Destructors_and_finalizers"></a> 析构函数和终结器  
 引用类型中的析构函数执行确定性清理的资源。 终结器清理非托管资源和的析构函数或不确定地垃圾回收器可以确定地调用。 有关标准 c + + 中的析构函数的信息，请参阅 [析构函数](../cpp/destructors-cpp.md)。  
  
```  
class classname {  
   ~classname() {}   // destructor  
   ! classname() {}   // finalizer  
};  
```  
  
 在托管 Visual c + + 类的析构函数的行为不同于 c + + 托管扩展。 有关此更改的详细信息，请参阅 [析构函数语义的更改](../dotnet/changes-in-destructor-semantics.md)。  
  
 CLR 垃圾回收器删除未使用的托管的对象，并在不再需要时释放其内存。 但是，一种类型可能会使用垃圾回收器不知道如何释放的资源。 这些资源称为非托管资源 （例如本机文件处理）。 我们建议您发布的终结器中的所有非托管的资源。 由于垃圾回收器不确定地释放托管的资源，因此是不安全，请对在终结器中的托管资源因为可能会在垃圾回收器已清除该托管资源。  
  
 Visual c + + 终结器不是与相同 <xref:System.Object.Finalize%2A> 方法。 (CLR 文档使用终结器和 <xref:System.Object.Finalize%2A> 方法同义词)。  <xref:System.Object.Finalize%2A> 垃圾回收器，它会调用类继承链中的每个终结器调用方法。 与 Visual c + + 析构函数不同的派生类释放方法调用不会导致编译器将调用所有基类中的终结器。  
  
 由于 Visual c + + 编译器支持的资源的确定性释放，不要尝试实现 <xref:System.IDisposable.Dispose%2A> 或 <xref:System.Object.Finalize%2A> 方法。 但是，如果您熟悉这些方法，下面是 Visual c + + 终结器和终结器调用了析构函数如何映射到 <xref:System.IDisposable.Dispose%2A> 模式︰  
  
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
  
 托管的类型还可以使用您希望具有确定性，释放并不留给垃圾回收器不再需要该对象之后，系统不确定地释放在某一时刻的托管的资源。 资源的确定性释放可以显著提高性能。  
  
 Visual c + + 编译器使您能够以明确地清理对象的析构函数的定义。 使用析构函数释放您想要确定地发布的所有资源。  如果存在一个终结器，则在从析构函数，以避免代码重复的情况下调用它。  
  
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
  
 如果使用您的类型的代码未调用析构函数时，垃圾回收器最终释放所有的托管的资源。  
  
 析构函数存在并不意味着终结器的状态。 但是，一个终结器的存在意味着，必须定义析构函数，并从该析构函数调用的终结器。 这提供对非托管资源的非确定性释放。  
  
 调用析构函数取消 — 通过使用 <xref:System.GC.SuppressFinalize%2A>— 终结的对象。 如果未调用析构函数，则最终将垃圾回收器调用您的类型的终结器。  
  
 明确地清理通过调用析构函数的对象的资源可以提高性能与让 CLR 以非确定性终结该对象进行比较。  
  
 已在 Visual c + + 中编写并使用编译的代码， **/clr** 如果运行类型的析构函数︰  
  
-   通过使用堆栈语义创建的对象超出范围。 有关详细信息，请参阅 [对于引用类型的 c + + 堆栈语义](../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
-   在对象的构造过程中引发异常。  
  
-   该对象是运行其析构函数的对象中的成员。  
  
-   您调用 [删除](../cpp/delete-operator-cpp.md) 对于句柄运算符 ([对象句柄运算符 (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md))。  
  
-   显式调用析构函数。  
  
 如果您的类型由另一种语言编写的客户端，析构函数调用，如下所示︰  
  
-   在调用 <xref:System.IDisposable.Dispose%2A>。  
  
-   在调用 `Dispose(void)` 类型上。  
  
-   如果类型超出作用域内的 C# `using` 语句。  
  
 （不用于引用类型使用堆栈语义） 位于托管堆上创建一个引用类型的对象，如果使用 [的 try-finally](../cpp/try-finally-statement.md) 语法以确保异常不会运行阻止析构函数。  
  
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
  
 如果您的类型具有析构函数，编译器将生成 `Dispose` 方法，实现 <xref:System.IDisposable>。 如果用 Visual c + + 编写并已从另一种语言使用了析构函数的类型，则调用 `IDisposable::Dispose` 对该类型会导致类型的析构函数调用。 从 Visual c + + 客户端使用该类型时，不能直接调用 `Dispose`; 相反，通过调用其析构函数 `delete` 运算符。  
  
 如果您的类型有一个终结器，编译器将生成 `Finalize(void)` 方法来重写 <xref:System.Object.Finalize%2A>。  
  
 如果某个类型有一个终结器或析构函数，编译器将生成 `Dispose(bool)` 方法，根据设计模式。 (有关信息，请参阅 [释放模式](../Topic/Dispose%20Pattern.md))。 无法显式创作或调用 `Dispose(bool)` Visual c + +。  
  
 如果类型具有一个基类，符合设计模式，调用派生类的析构函数时，会调用的所有基类的析构函数。 （如果您的类型用 Visual c + + 编写的编译器可确保您的类型实现此模式。）换而言之，引用类的析构函数链接到其基项和由 c + + 标准指定的成员，类的析构函数是运行程序，则相反的顺序在其中它们的创建过程，其成员的析构函数的第一个和最后已构造的顺序反过来其基类的析构函数。  
  
 值类型或接口中不允许析构函数和终结器。  
  
 只能定义或引用类型中声明终结器。 使用构造函数和析构函数，与终结器有没有返回类型。  
  
 对象的终结器运行后，在任何基类中的终结器也称为，开头的派生程度最低的类型。 数据成员的终结器都不会自动链接到类的终结器。  
  
 如果终结器中删除的托管类型中的本机指针，则必须确保，不会过早地收集的或通过本机指针的引用;而不是使用托管类型上调用其析构函数 <xref:System.GC.KeepAlive%2A>。  
  
 在编译时，您可以检测到某个类型有一个终结器或析构函数。 有关详细信息，请参阅 [编译器支持类型特征](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 下一个示例演示两种类型，即具有非托管的资源，另一个具有托管确定性地释放资源。  
  
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
  
## <a name="see-also"></a>另请参阅  
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)   
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)