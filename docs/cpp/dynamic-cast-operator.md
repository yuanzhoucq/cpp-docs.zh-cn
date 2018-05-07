---
title: dynamic_cast 运算符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dynamic_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a87105ad2d52ebbb7749deafadedcd510314038f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="dynamiccast-operator"></a>dynamic_cast 运算符
将转换该操作数`expression`类型的对象到`type-id`。  
  
## <a name="syntax"></a>语法  
  
```  
  
dynamic_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>备注  
 `type-id`必须是指针或对以前定义的类类型的引用或"指向 void 指针"。 如果 `type-id` 是指针，则 `expression` 类型必须为指针，或者如果 `type-id` 是引用，则为左值。  
  
 请参阅[static_cast](../cpp/static-cast-operator.md)有关之间的差异静态和动态强制转换，以及何时适合使用它们的说明。  
  
 中的行为有两个重大更改`dynamic_cast`在托管代码中：  
  
-   `dynamic_cast` 在运行时，返回 0 而不是转换后的指针的指针到装箱枚举的基础类型将失败。  
  
-   `dynamic_cast` 将不再引发异常时`type-id`是值类型，与在运行时失败的强制转换为内部指针。  现在，该强制转换将返回 0 的指针值而不是引发。  
  
 如果`type-id`是指向一个明确访问直接或间接基类的`expression`，指向类型的唯一的子对象的指针`type-id`结果。 例如：  
  
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
  
 这种类型的转换称为"向上转换"，因为它将类层次结构，向上的指针移到派生自的类派生类。 向上转换是隐式转换。  
  
 如果`type-id`是 void * 进行运行时检查以确定的实际类型`expression`。 结果是指向完整对象的指针`expression`。 例如：  
  
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
  
 如果`type-id`不是 void * 进行运行时检查以查看如果指向的对象通过`expression`可以转换为指向类型`type-id`。  
  
 如果的一种`expression`是基类的一种`type-id`，进行运行时检查以查看是否`expression`实际指向的类型的完整对象`type-id`。 如果这是真的，结果是指向整个对象的类型的`type-id`。 例如：  
  
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
  
 此类型的转换称为"向下转换"因为它将一个指针下移类层次结构中，从给定类的类派生自它。  
  
 多重继承的情况下，在引入了不明确的可能性。 请考虑下图中所示的类层次结构。  
  
 对于 CLR 类型，`dynamic_cast`导致不执行任何操作可以隐式执行转换或 MSIL`isinst`指令，这将执行动态检查，并返回`nullptr`如果转换失败。  
  
 下面的示例使用`dynamic_cast`以确定是否类是特定类型的实例：  
  
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
  
 ![类层次结构显示多重继承的](../cpp/media/vc39011.gif "vc39011")  
显示多继承的类层次结构  
  
 指向类型的对象的指针`D`能够安全地转换为`B`或`C`。 但是，如果`D`被强制转换为指向`A`对象，哪个实例`A`将导致？ 这将导致不明确的强制转换错误。 若要获取解决此问题，你可以执行两个明确的强制转换。 例如：  
  
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
  
 当你使用虚拟基类时，可以引入了进一步的多义性。 请考虑下图中所示的类层次结构。  
  
 ![类层次结构显示虚拟基类的](../cpp/media/vc39012.gif "vc39012")  
显示虚拟基类的类层次结构  
  
 此层次结构中`A`是虚拟基类。 给定类的实例`E`和一个指向`A`子对象，`dynamic_cast`的指针到`B`由于语意不明确将失败。 你必须首先重新强制转换为完整`E`对象，然后以明确方式，来访问正确工作反向沿层次结构，`B`对象。  
  
 请考虑下图中所示的类层次结构。  
  
 ![类层次结构显示重复基类的](../cpp/media/vc39013.gif "vc39013")  
显示重复基类的类层次结构  
  
 给定类型的对象`E`和一个指向`D`子对象，若要从导航`D`到最左边的子对象`A`子对象，可以进行三个转换。 你可以执行`dynamic_cast`从转换`D`指向`E`指针，则转换 (或者`dynamic_cast`或隐式转换) 从`E`到`B`，和最后一个从隐式转换`B`到`A`。 例如：  
  
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
  
 `dynamic_cast`运算符还可以用于执行"交叉 cast"。 使用相同的类层次结构，它可强制是指针，例如，转换从`B`到的子对象`D`子对象，前提是完整的对象属于类型`E`。  
  
 考虑跨强制转换时，它是实际可用来执行从指向的指针转换`D`的指针到最左侧`A`仅使用两个步骤中的子对象。 你可以执行强制转换从跨`D`到`B`，然后从隐式转换`B`到`A`。 例如：  
  
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
  
 一个 null 指针值转换为的目标类型的 null 指针值`dynamic_cast`。  
  
 当你使用`dynamic_cast < type-id > ( expression )`，如果`expression`无法安全地转换为类型`type-id`，运行时检查导致转换失败。 例如：  
  
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
  
 失败的强制转换为指针类型的值是 null 指针。 失败的强制转换为引用类型会引发[bad_cast 异常](../cpp/bad-cast-exception.md)。   如果`expression`不指向或引用有效的对象，`__non_rtti_object`引发异常。  
  
 请参阅[typeid](../cpp/typeid-operator.md)有关的说明`__non_rtti_object`异常。  
  
## <a name="example"></a>示例  
 下面的示例创建基类 （结构一个） 指针，指向的对象 （结构 C）。  再加上存在的事实是虚拟函数，启用运行时多态性。  
  
 本示例还调用层次结构中的非虚拟函数。  
  
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
  
```Output  
in C  
test2 in B  
in GlobalTest  
Can't cast to C  
```  
  
## <a name="see-also"></a>请参阅  
 [强制转换运算符](../cpp/casting-operators.md)   
 [关键字](../cpp/keywords-cpp.md)