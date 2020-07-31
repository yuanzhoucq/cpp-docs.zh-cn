---
title: dynamic_cast 运算符
description: C + + 语言 dynamic_cast 运算符的概述。
ms.date: 02/03/2020
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 15609aeaef815ff89ca196876e1143090c65221b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221635"
---
# <a name="dynamic_cast-operator"></a>dynamic_cast 运算符

将操作数转换 `expression` 为类型的对象 `type-id` 。

## <a name="syntax"></a>语法

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>备注

`type-id`必须是指向以前定义的类类型或 "指向 void 的指针" 的指针或引用。 如果 `type-id` 是指针，则 `expression` 类型必须为指针，或者如果 `type-id` 是引用，则为左值。

请参阅[static_cast](../cpp/static-cast-operator.md) ，了解静态和动态强制转换之间的差异，以及何时使用它们。

托管代码的行为有两种重大更改 **`dynamic_cast`** ：

- **`dynamic_cast`** 指向装箱枚举的基础类型的指针将在运行时失败，并返回0而不是转换后的指针。

- **`dynamic_cast`** 当 `type-id` 是指向值类型的内部指针，且在运行时失败时，将不再引发异常。  转换现在将返回0指针值，而不是引发。

如果 `type-id` 是指向可明确访问的直接或间接基类的指针 `expression` ，则为类型的唯一子对象的指针 `type-id` 。 例如：

```cpp
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

这种类型的转换称为 "向上转换"，因为它将指向派生类的指针向上移动到它派生自的类。 向上转换是一个隐式转换。

如果 `type-id` 为 void *，则进行运行时检查以确定的实际类型 `expression` 。 结果是指向指向的完整对象的指针 `expression` 。 例如：

```cpp
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

如果不 `type-id` 是 void *，则会执行运行时检查，以查看指向的对象是否 `expression` 可以转换为指向的类型 `type-id` 。

如果的类型 `expression` 是的类型的基类，则执行 `type-id` 运行时检查，以查看是否 `expression` 确实指向的类型的完整对象 `type-id` 。 如果为 true，则结果为指向的类型的完整对象的指针 `type-id` 。 例如：

```cpp
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

这种类型的转换称为 "向下转换"，因为它将指向某个类层次结构的指针向下移动到一个派生自的类。

在多重继承的情况下，会引入可能的多义性。 请考虑下图中显示的类层次结构。

对于 CLR 类型， **`dynamic_cast`** 如果可以隐式执行转换，则会产生无操作，也会生成 MSIL `isinst` 指令，如果转换失败，则将执行动态检查并返回 **`nullptr`** 。

下面的示例使用 **`dynamic_cast`** 来确定类是否为特定类型的实例：

```cpp
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

![显示多重继承的类层次结构](../cpp/media/vc39011.gif "显示多重继承的类层次结构") <br/>
显示多重继承的类层次结构

指向类型的对象的指针 `D` 可以安全地强制转换为 `B` 或 `C` 。 但是，如果 `D` 将强制转换为指向 `A` 对象， `A` 将会产生哪个实例？ 这会导致不明确的转换错误。 若要解决此问题，可以执行两个明确的强制转换。 例如：

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A {virtual void f();};
class D : public B, public C {virtual void f();};

void f() {
   D* pd = new D;
   A* pa = dynamic_cast<A*>(pd);   // C4540, ambiguous cast fails at runtime
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

使用虚拟基类时，可能会引入更多歧义。 请考虑下图中显示的类层次结构。

![显示虚拟基类的类层次结构](../cpp/media/vc39012.gif "显示虚拟基类的类层次结构") <br/>
显示虚拟基类的类层次结构

在此层次结构中， `A` 是一个虚拟基类。 给定类的实例和指向子对象的 `E` 指针 `A` 时，指向的 **`dynamic_cast`** 指针的将因多义性而 `B` 失败。 必须首先强制转换回完整的 `E` 对象，然后以明确的方式将层次结构备份到正确的 `B` 对象。

请考虑下图中显示的类层次结构。

![显示重复基类的类层次结构](../cpp/media/vc39013.gif "显示重复基类的类层次结构") <br/>
显示重复基类的类层次结构

给定类型的对象和指向子对象的 `E` 指针 `D` ，若要从子对象导航到最左侧的子对象 `D` `A` ，则可以进行三次转换。 可以执行 **`dynamic_cast`** 从 `D` 指针到指针的转换 `E` ，然后执行从到的转换（ **`dynamic_cast`** 或隐式转换） `E` `B` ，最后将隐式转换 `B` 为 `A` 。 例如：

```cpp
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

**`dynamic_cast`** 运算符还可用于执行 "交叉强制转换"。 使用相同的类层次结构，可以将指针强制转换为子对象，例如， `B` `D` 只要完整的对象属于类型就可以 `E` 。

考虑跨转换，实际上可以执行从指向最左侧子对象的指针到指向 `D` 最左侧子对象的转换， `A` 只需执行两个步骤。 可以执行从到的交叉转换 `D` `B` ，然后执行从到的隐式转换 `B` `A` 。 例如：

```cpp
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

空指针值被转换为目标类型的 null 指针值 **`dynamic_cast`** 。

当你使用时 `dynamic_cast < type-id > ( expression )` ，如果 `expression` 不能安全地转换为类型 `type-id` ，则运行时检查将导致强制转换失败。 例如：

```cpp
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

转换为指针类型的失败的值为 null 指针。 未能强制转换为引用类型会引发[Bad_cast 异常](../cpp/bad-cast-exception.md)。   如果不 `expression` 指向或引用有效的对象，则 `__non_rtti_object` 会引发异常。

有关异常的说明，请参阅[typeid](../cpp/typeid-operator.md) `__non_rtti_object` 。

## <a name="example"></a>示例

下面的示例创建一个指向对象（结构 C）的基类（结构 A）指针。  这也是有虚函数的事实，它支持运行时多态性。

该示例还调用层次结构中的非虚拟函数。

```cpp
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

## <a name="see-also"></a>另请参阅

[转换运算符](../cpp/casting-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)
