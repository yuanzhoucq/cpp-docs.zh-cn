---
title: "dynamic_cast 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "dynamic_cast"
  - "dynamic_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dynamic_cast 关键字 [C++]"
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# dynamic_cast 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将操作数 `expression` 转换成类型为`type-id` 的对象。  
  
## 语法  
  
```  
  
dynamic_cast < type-id > ( expression )  
```  
  
## 备注  
 `type-id` 必须是一个指针或引用到以前已定义的类类型的引用或“指向 void 的指针”。  如果 `type-id` 是指针，则`expression` 的类型必须是指针，如果 `type-id` 是引用，则为左值。  
  
 有关静态和动态强制转换之间区别的描述，以及各在什么情况下适合使用，请参见 [static\_cast](../cpp/static-cast-operator.md)。  
  
 在托管代码中的 `dynamic_cast`的行为中有两个重大更改。  
  
-   为指针的`dynamic_cast` 对指向装箱的枚举的基础类型的指针将在运行时失败，则返回 0 而不是已转换的指针。  
  
-   `dynamic_cast` 将不再引发一个异常，当 `type-id` 是指向值类型的内部指针，则转换在运行时失败。该转换将返回 0 指示运行值而不是引发。  
  
 如果 `type-id` 是指向 `expression`的明确的可访问的直接或间接基类的指针，则结果是指向 `type-id` 类型的唯一子对象的指针。  例如：  
  
```  
// dynamic_cast_1.cpp  
// compile with: /c  
class B { };  
class C : public B { };  
class D : public C { };  
  
void f(D* pd) {  
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class  
                                   // pc points to C subobject of pd   
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class  
                                   // pb points to B subobject of pd  
}  
```  
  
 此转换类型称为“向上转换”，因为它将在类层次结构上的指针，从派生的类移到该类派生的类。  向上转换是一种隐式转换。  
  
 如果 `type-id` 为 void\*，则做运行时进行检查确定 `expression`的实际类型。  结果是指向 by `expression` 的完整的对象的指针。  例如：  
  
```  
// dynamic_cast_2.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = new B;  
   void* pv = dynamic_cast<void*>(pa);  
   // pv now points to an object of type A  
  
   pv = dynamic_cast<void*>(pb);  
   // pv now points to an object of type B  
}  
```  
  
 如果 `type-id` 不是 void\*，则做运行时进行检查以确定是否由 `expression` 指向的对象可以转换为由 `type-id`指向的类型。  
  
 如果 `expression` 类型是 `type-id`类型的基类，则做运行时检查来看是否 `expression` 确实指向 `type-id`类型的完整对象。  如果为 true，则结果是指向 `type-id`类型的完整对象的指针。  例如：  
  
```  
// dynamic_cast_3.cpp  
// compile with: /c /GR  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   B* pb = new D;   // unclear but ok  
   B* pb2 = new B;  
  
   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D  
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D  
}  
```  
  
 此转换类型称为“向下转换”，因为它将在类层次结构下的指针，从给定的类移到该类派生的类。  
  
 对于多重继承，引入多义性的可能性。  考虑下图中显示的类层次结构。  
  
 对于 CLR 类型，如果转换可以隐式执行，则 `dynamic_cast` 结果为 no\-op，如果转换失败，则 MSIL `isinst` 指令将执行动态检查并返回 `nullptr`。  
  
 以下示例使用 `dynamic_cast` 以确定一个类是否为特殊类型的实例：  
  
```  
// dynamic_cast_clr.cpp  
// compile with: /clr  
using namespace System;  
  
void PrintObjectType( Object^o ) {  
   if( dynamic_cast<String^>(o) )  
      Console::WriteLine("Object is a String");  
   else if( dynamic_cast<int^>(o) )  
      Console::WriteLine("Object is an int");  
}  
  
int main() {  
   Object^o1 = "hello";  
   Object^o2 = 10;  
  
   PrintObjectType(o1);  
   PrintObjectType(o2);  
}  
```  
  
 ![显示多重继承的类层次结构](../cpp/media/vc39011.png "vc39011")  
显示多继承的类层次结构  
  
 指向类型 `D` 对象的指针可以安全地强制转换为 `B` 或 `C`。  但是，如果 `D` 强制转换为指向 `A` 对象的指针，会导致 `A` 的哪个实例？  这将导致不明确的强制转换错误。  若要避免此问题，可以执行两个明确的转换。  例如：  
  
```  
// dynamic_cast_4.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   D* pd = new D;  
   B* pb = dynamic_cast<B*>(pd);   // first cast to B  
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous  
}  
```  
  
 当使用虚拟基类时，其他多义性问题会被引入。  考虑下图中显示的类层次结构。  
  
 ![显示虚拟基类的类层次结构](../cpp/media/vc39012.png "vc39012")  
显示虚拟基类的类层次结构  
  
 在此层次结构中，`A` 是虚拟基类。  对于虚拟基类的定义，请参见 [虚拟基类](../misc/virtual-base-classes.md)。  给定一个 `E` 类实例和一个指向 `A` 子对象的指针，指向 `B` 指针的 `dynamic_cast` 将失败于多义性。  必须先将强制转换回完整 `E` 对象，然后以明确的方式反向沿层次结构，到达正确的 `B` 对象。  
  
 考虑下图中显示的类层次结构。  
  
 ![显示重复基类的类层次结构](../Image/vc39013.gif "vc39013")  
显示重复基类的类层次结构  
  
 给定一个 `E` 类型的对象和一个指向 `D` 子对象的指针，从 `D` 子对象定位到最左侧的 `A` 子对象，可进行三个转换。  可以从 `D` 指针到 `E` 指针执行 `dynamic_cast` 转换，然后从 `E` 到 `B` 执行转换（`dynamic_cast` 或隐式转换），最后从 `B` 到 `A` 执行隐式转换。  例如：  
  
```  
// dynamic_cast_5.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   E* pe = dynamic_cast<E*>(pd);  
   B* pb = pe;   // upcast, implicit conversion  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 `dynamic_cast` 运算符还可以使用执行 “相互转换”。使用同一个类层次结构可能进行指针转换，例如： 从`B` 子对象转换到`D`子对象（只要整个对象是类转换型`E`。  
  
 考虑相互转换，实际上从指针转换到 `D` 到指针到最左侧的 `A` 子对象只要两个步骤。  可以从 `D` 到 `B` 执行相互转换，然后从 `B` 到 `A` 执行隐式转换。  例如：  
  
```  
// dynamic_cast_6.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   B* pb = dynamic_cast<B*>(pd);   // cross cast  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 通过 `dynamic_cast` 将 null 指针值转换到目标类型的 null 指针值。  
  
 当您使用 `dynamic_cast < type-id > ( expression )`时，如果`expression`无法安全地转换成类型 `type-id`，则运行时检查会引起变换失败。  例如：  
  
```  
// dynamic_cast_7.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;  
   // B not derived from A  
}  
```  
  
 指针类型的非限定转换的值是 null 指针。  引用类型的非限定转换会引发 [bad\_cast 异常](../cpp/bad-cast-exception.md)。   如果 `expression` 不指向也不引用有效的对象，则`__non_rtti_object` 异常引发。  
  
 有关异常 `__non_rtti_object` 的解释，请参见 [typeid](../cpp/typeid-operator.md)。  
  
## 示例  
 以下示例创建基类（结构 A）指针，为一个对象（结构 C）。这以及在该情况是虚函数，启用运行时多态性。  
  
 该示例也在层次结构中调用非虚函数。  
  
```  
// dynamic_cast_8.cpp  
// compile with: /GR /EHsc  
#include <stdio.h>  
#include <iostream>  
  
struct A {  
    virtual void test() {  
        printf_s("in A\n");  
   }  
};  
  
struct B : A {  
    virtual void test() {  
        printf_s("in B\n");  
    }  
  
    void test2() {  
        printf_s("test2 in B\n");  
    }  
};  
  
struct C : B {  
    virtual void test() {  
        printf_s("in C\n");  
    }  
  
    void test2() {  
        printf_s("test2 in C\n");  
    }  
};  
  
void Globaltest(A& a) {  
    try {  
        C &c = dynamic_cast<C&>(a);  
        printf_s("in GlobalTest\n");  
    }  
    catch(std::bad_cast) {  
        printf_s("Can't cast to C\n");  
    }  
}  
  
int main() {  
    A *pa = new C;  
    A *pa2 = new B;  
  
    pa->test();  
  
    B * pb = dynamic_cast<B *>(pa);  
    if (pb)  
        pb->test2();  
  
    C * pc = dynamic_cast<C *>(pa2);  
    if (pc)  
        pc->test2();  
  
    C ConStack;  
    Globaltest(ConStack);  
  
   // will fail because B knows nothing about C  
    B BonStack;  
    Globaltest(BonStack);  
}  
```  
  
  **in C**  
**test2 in B**  
**in GlobalTest**  
**Can't cast to C**   
## 请参阅  
 [强制转换运算符](../cpp/casting-operators.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)