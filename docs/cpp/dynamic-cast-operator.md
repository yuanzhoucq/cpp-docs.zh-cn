---
title: dynamic_cast 运算符
ms.date: 11/19/2018
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 3b359885eb72f9272fb1efe14afe9a6cbe6ddb30
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176960"
---
# <a name="dynamiccast-operator"></a>dynamic_cast 运算符

将转换该操作数`expression`类型的对象到`type-id`。

## <a name="syntax"></a>语法

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>备注

`type-id`必须是指针或对以前定义的类类型的引用或"指向 void 指针"。 如果 `type-id` 是指针，则 `expression` 类型必须为指针，或者如果 `type-id` 是引用，则为左值。

请参阅[static_cast](../cpp/static-cast-operator.md)以及何时适合使用每个静态和动态强制转换之间的差异的说明。

中的行为有两个重大更改**dynamic_cast**在托管代码中：

- **dynamic_cast**装箱枚举的基础类型的指针到则无法在运行时，返回 0 而不是转换后的指针。

- **dynamic_cast**将不再引发异常时`type-id`是值类型，与在运行时失败的强制转换为内部指针。  强制转换现在将返回而不是引发的 0 的指针值。

如果`type-id`指向的明确访问直接或间接基类的指针`expression`，指向类型的唯一子对象的指针`type-id`是结果。 例如：

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

此转换类型称为"上传"，因为它将上类层次结构中，将指针移到派生自的类派生类中。 向上转换是隐式转换。

如果`type-id`是 void *，进行运行时检查以确定的实际类型`expression`。 结果是指向指向完整对象`expression`。 例如：

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

如果`type-id`不是 void *，进行运行时检查以查看如果指向的对象由`expression`可转换为指向类型`type-id`。

如果类型`expression`是类型的基类`type-id`，进行运行时检查以查看是否`expression`实际指向的类型的完整对象`type-id`。 如果为 true，结果是一个完整的类型的对象的指针`type-id`。 例如：

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

此类型的转换称为"向下转换"因为它将一个指针，下移类层次结构，从给定类中，以便一个类派生自它。

在多个继承的情况下，引入了不明确的可能性。 请考虑下图中所示的类层次结构。

对于 CLR 类型， **dynamic_cast**会导致不执行任何操作如果隐式地执行转换或 MSIL`isinst`指令将执行动态检查，并返回**nullptr**如果转换将失败。

下面的示例使用**dynamic_cast**确定类是否为特定类型的实例：

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

![类层次结构显示多重继承](../cpp/media/vc39011.gif "类显示多个继承层次结构") <br/>
显示多重继承的类层次结构

指向类型的对象的指针`D`可以安全地转换到`B`或`C`。 但是，如果`D`强制转换为指向`A`对象的哪些实例`A`将导致？ 这会导致不明确转换错误。 若要解决此问题，可以执行两个明确的强制转换。 例如：

```cpp
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

使用虚拟基类时，可以引入进一步二义性。 请考虑下图中所示的类层次结构。

![类层次结构显示虚拟基类的](../cpp/media/vc39012.gif "类显示虚拟基类层次结构") <br/>
显示虚拟基类的类层次结构

此层次结构中`A`是虚拟基类。 给定类的实例`E`和指针`A`子对象**dynamic_cast**指向的`B`将因多义性而失败。 您必须首先强制转换为完整`E`对象，并明确的方式，来访问正确工作反向沿层次结构，`B`对象。

请考虑下图中所示的类层次结构。

![类层次结构显示重复基类的](../cpp/media/vc39013.gif "类显示重复基类的层次结构") <br/>
显示重复基类的类层次结构

给定类型的对象`E`和指针`D`子对象，若要从导航`D`最左侧的子对象`A`子对象，可为三个转换。 你可以执行**dynamic_cast**从转换`D`指针，指向`E`指针，则转换 (任一**dynamic_cast**或隐式转换) 从`E`到`B`，并最后的隐式转换从`B`到`A`。 例如：

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

**Dynamic_cast**运算符还可用于执行"跨转换"。 使用相同的类层次结构，有可能是指针，例如，将从强制转换`B`到子对象`D`子对象，前提是完整的对象属于类型`E`。

考虑跨强制转换，它是实际上可能会执行从指针到转换`D`为指向最左侧的`A`中仅使用两个步骤的子对象。 你可以执行强制转换从跨`D`到`B`，然后从的隐式转换`B`到`A`。 例如：

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

一个 null 指针值转换为的目标类型的 null 指针值**dynamic_cast**。

当你使用`dynamic_cast < type-id > ( expression )`，如果`expression`无法安全地转换为类型`type-id`，运行时检查会导致转换失败。 例如：

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

失败的强制转换为指针类型的值为 null 指针。 失败的强制转换，以引用类型，则会引发[bad_cast 异常](../cpp/bad-cast-exception.md)。   如果`expression`不会指向或引用有效的对象，`__non_rtti_object`引发异常。

请参阅[typeid](../cpp/typeid-operator.md)有关的说明`__non_rtti_object`异常。

## <a name="example"></a>示例

下面的示例创建指向的对象 （C 结构） 的基类 (struct A) 指针。  再加上这一事实是虚拟函数，使运行时多形性。

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

## <a name="see-also"></a>请参阅

[强制转换运算符](../cpp/casting-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)