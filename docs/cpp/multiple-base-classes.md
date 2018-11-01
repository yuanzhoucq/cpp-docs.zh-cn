---
title: 多个基类
ms.date: 11/04/2016
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: fbbe6d6194b878b4851cbde84b55d71b9e4fc02c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483455"
---
# <a name="multiple-base-classes"></a>多个基类

可以从多个基类派生的类。 在多重继承模型中 （其中类派生自多个基类），使用指定基类*基列表*语法元素。 例如，可以指定派生自 `CollectionOfBook` 和 `Collection` 的 `Book` 的类声明：

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

指定基类的顺序并不重要，只不过在某些情况下，将调用构造函数和析构函数。 在这些情况下，指定基类的顺序将影响：

- 构造函数进行初始化的顺序。 如果你的代码依赖要在 `Book` 部分之前初始化的 `CollectionOfBook` 的 `Collection` 部分，则规范的顺序很重要。 初始化发生在类中指定的顺序*基列表*。

- 调用析构函数以进行清理的顺序。 同样，如果在销毁另一部分时必须呈现类的特定“部分”，则顺序非常重要。 中指定的类的相反顺序调用析构函数*基列表*。

    > [!NOTE]
    >  基类的规范顺序会影响类的内存布局。 不要基于内存中基成员的顺序做出任何编程决策。

指定时*基列表*，不能多次指定相同的类名。 但是，可以将类多次作为派生类的间接基。

## <a name="virtual-base-classes"></a>虚拟基类

由于一个类可能多次成为派生类的间接基类，因此 C++ 提供了一种优化这种基类的工作方式的方法。 虚拟基类提供了一种节省空间和避免使用多重继承的类层次结构中出现多义性的方法。

每个非虚拟对象包含在基类中定义的数据成员的一个副本。 这种重复浪费了空间，并要求您在每次访问基类成员时都必须指定所需的基类成员的副本。

当将某个基类指定为虚拟基时，该基类可以多次作为间接基而无需复制其数据成员。 基类的数据成员的单个副本由将其用作虚拟基的所有基类共享。

当声明虚拟基类**虚拟**关键字出现在派生类的基列表中。

请考虑下图中的类层次结构，它演示了模拟的午餐排队。

![关系图的模拟的午餐](../cpp/media/vc38xp1.gif "vc38XP1")模拟午餐排队图

在该图中，`Queue` 是 `CashierQueue` 和 `LunchQueue` 的基类。 但是，当将这两个类组合成 `LunchCashierQueue` 时，会出现以下问题：新类包含类型 `Queue` 的两个子对象，一个来自 `CashierQueue`，另一个来自 `LunchQueue`。 下图显示了概念上的内存布局（实际物理内存布局可能会进行优化）。

![模拟午餐&#45;行对象](../cpp/media/vc38xp2.gif "vc38XP2")模拟午餐排队对象

请注意，`Queue` 对象中有两个 `LunchCashierQueue` 子对象。 以下代码将 `Queue` 声明为虚拟基类：

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

**虚拟**关键字可确保只有一个子对象的副本`Queue`包含 （请参阅下图）。

![模拟午餐&#45;行对象、 虚拟基类](../cpp/media/vc38xp3.gif "vc38XP3")带虚拟基类模拟午餐排队对象

一个类可以同时具有一个给定类型的虚拟组件和非虚拟组件。 下图演示了这种情况。

![虚拟和非虚拟组件的类](../cpp/media/vc38xp4.gif "vc38XP4")虚拟和非虚拟组件的同一个类

在图中，`CashierQueue` 和 `LunchQueue` 将 `Queue` 用作虚拟基类。 但是，`TakeoutQueue` 将 `Queue` 指定为基类而不是虚拟基类。 因此，`LunchTakeoutCashierQueue` 具有类型 `Queue` 的两个子对象：一个来自包含 `LunchCashierQueue` 的继承路径，另一个来自包含 `TakeoutQueue` 的路径。 下图对此进行了演示。

![对象布局中的虚拟和非虚拟继承](../cpp/media/vc38xp5.gif "vc38XP5")带有虚拟和非虚拟继承的对象布局

> [!NOTE]
>  与非虚拟继承相比较，虚拟继承提供了显著的大小优势。 但是，它可能会引入额外的处理开销。

如果派生类重写它从虚拟基类继承的虚函数，并且派生基类的构造函数或析构函数使用指向虚拟基类的指针调用该虚函数，则编译器可能会将其他隐藏的“vtordisp”字段引入到具有虚拟基的类中。 `/vd0`编译器选项将禁止添加隐藏的 vtordisp 构造函数/析构函数置换成员。 `/vd1`编译器选项，默认情况下，让它们将在必要时。 仅当确定所有类构造函数和析构函数以虚拟方式调用虚函数时才关闭 vtordisps。

`/vd`编译器选项会影响整个编译模块。 使用`vtordisp`杂注，然后重新启用`vtordisp`个类的类的字段：

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>名称多义性

多重继承使得沿多个路径继承名称成为可能。 沿这些路径的类成员名称不一定是唯一的。 这些名称冲突称为“多义性”。

任何引用类成员的表达式必须采用明确的引用。 以下示例说明如何产生多义性：

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

对于前面的类声明，如下所示的代码是不明确的，因为 `b` 所指的 `b` 是在 `A` 中还是在 `B` 中并不清楚：

```cpp
C *pc = new C;

pc->b();
```

请看前面的示例。 由于名称 `a` 是类 `A` 和类 `B` 的成员，因此编译器无法辩明哪个 `a` 指定将调用函数。 如果成员可以引用多个函数、对象、类型或枚举数，则对该成员的访问是不明确的。

编译器通过按此顺序执行测试来检测多义性：

1. 如果对名称的访问是不明确的（如上所述），则会生成错误消息。

1. 如果重载函数是明确的，则将解析它们。

1. 如果对名称的访问违背了成员访问权限，则会生成错误消息。 (有关详细信息，请参阅[成员访问控制](../cpp/member-access-control-cpp.md)。)

在表达式通过继承产生多义性时，您可以通过限定考虑中的名称及其类名来手动消除该多义性。 若要适当编译上面的示例而不产生多义性，请使用如下代码：

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
>  在声明 `C` 时，如果在 `B` 的范围内引用 `C`，则可能会导致出现错误。 但不会发出任何错误，直到在 `B` 的范围内实际创建对 `C` 的非限定引用。

### <a name="dominance"></a>主导

通过一个继承关系图到达多个名称（函数、对象或枚举器）是可能的。 这种情况被视为与非虚拟基类一起使用时目的不明确。 这些名称与虚拟基类一起使用时目的不明确，除非其中一个名称“决定”其他名称。

如果某个名称在两个类中定义并且一个类派生自另一个类，则该名称可控制另一个名称。 基准名称是派生类中的名称；此名称在本应出现多义性时使用，如以下示例所示：

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>不明确的转换

从指向类类型的指针或对类类型的引用的显式或隐式转换可能会导致多义性。 下图（指向基类的指针的不明确转换）显示如下内容：

- `D` 类型的对象的声明。

- 应用 address-of 运算符的效果 (**&**) 对该对象。 请注意，address-of 运算符总是提供该对象的基址。

- 将使用 address-of 运算符获取的指针显式转换为基类类型 `A` 的效果。 请注意，将该对象的地址强制转换为 `A*` 类型并不总是为编译器提供足够的信息，以供 `A` 类型的子对象进行选择；在这种情况下，将存在两个子对象。

![指针到基类的不明确转换](../cpp/media/vc38xt1.gif "vc38XT1")不明确转换指针到基类

到类型 `A*`（指向 `A` 的指针）的转换是不明确的，因为无法辩明 `A` 类型的哪个子对象是正确的。 请注意，您可以通过显式指定要使用的子对象来避免多义性，如下所示：

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>多义性和虚拟基类

如果使用虚拟基类，则函数、对象、类型和枚举数可通过多重继承路径到达。 因为仅有一个基类实例，因此在访问这些名称时不存在二义性。

下图显示如何使用虚拟和非虚拟继承构成对象。

![虚拟派生与非虚拟派生](../cpp/media/vc38xr1.gif "vc38XR1")虚拟 vs。非虚拟派生

在该图中，通过非虚拟基类访问类 `A` 的任何成员都将导致二义性；编译器没有解释是使用与 `B` 关联的子对象还是与 `C` 关联的子对象的信息。 但是，将 `A` 指定为虚拟基类时，访问哪一个子对象都不成问题。

## <a name="see-also"></a>请参阅

[继承](../cpp/inheritance-cpp.md)