---
title: 值类型语义 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72dc6a613616d13e9ff92e8af0c39c63dfe63162
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413791"
---
# <a name="value-type-semantics"></a>值类型语义

值类型语义具有从托管扩展中的 c + + 更改为 Visual c + +。

下面是在托管扩展中用于 c + + 规范的规范的简单值类型：

```
__value struct V { int i; };
__gc struct R { V vr; };
```

在托管扩展中，我们可以具有值类型的四个语法变体 （其中窗体 2 和 3 为相同语义上）：

```
V v = { 0 };       // Form (1)
V *pv = 0;         // Form (2) an implicit form of (3)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0; // Form (4) must be local
```

## <a name="invoking-inherited-virtual-methods"></a>调用继承的虚方法

`Form (1)` 是规范化的值对象，并且它是相当容易理解，除了当有人尝试调用继承的虚方法，如`ToString()`。 例如：

```
v.ToString(); // error!
```

若要调用此方法，因为它未被重写中`V`，编译器必须有权访问基类的关联的虚拟表。 由于值类型是在状态存储，没有关联的指针指向其虚拟表 (vptr)，这就要求`v`进行装箱。 在托管扩展语言设计中，隐式装箱不支持，但必须显式指定由程序员，如

```
__box( v )->ToString(); // Managed Extensions: note the arrow
```

此设计背后的主要目的是教学： 基础机制必须是对编程人员可见，以便她将了解不提供在她值类型实例的成本。 已`V`若要包含的实例`ToString`，将不需要装箱。

在新语法中删除的显式装箱对象，但未装箱本身的基本费用词法复杂性：

```
v.ToString(); // new syntax
```

但这样可能会误导类设计器不具有提供的显式实例的成本`ToString`方法内的`V`。 优先使用隐式装箱的原因是虽然通常只是一个类设计器，有无限的数量的用户，他们不会能自由地修改`V`以消除可能导致重大开销的显式装箱。

若要确定是否提供重写的实例所依据的条件`ToString`类应在值中是频率和使用该方法的位置。 如果调用很少，是当然在其定义中的一些好处。 同样，如果调用应用程序的几个方面与性能无关时，将其添加将也不会显著提高将添加到应用程序的常规性能。 或者，一个可以跟踪句柄保留到装箱的值，并通过该句柄的调用将不需要执行装箱。

## <a name="there-is-no-longer-a-value-class-default-constructor"></a>不再值类默认构造函数

值类型的托管扩展和新语法之间的另一个差异是支持的因为删除了对默认构造函数。 这是因为有时可在其中 CLR 创建值类型的实例而无需调用相关联的默认构造函数的执行过程。 即尝试下托管扩展支持的值类型中的默认构造函数可能不在实践中得到保证。 给定保证的它是感觉是更好一些，完全删除支持，而不是让它变得不确定其应用程序中。

这不是最初可能看起来像那么糟糕。 这是因为自动清值类型的每个对象 （即，每个类型初始化为其默认值）。 因此，本地实例的成员将永远不会不确定。 在这种情况下，定义一个普通的默认构造函数的功能丢失真正丢失根本不-和实际上是由 CLR 执行时效率更高。

当托管扩展的用户定义的非普通的默认构造函数时，此问题。 这会产生不能映射到新的语法。 构造函数中的代码将需要迁移到之后必须由用户显式调用的已命名的初始化方法。

否则保持不变值类型对象的新语法中的声明。 这样做的缺点是值类型不令人满意的本机类型换行的原因如下：

- 没有析构函数中的值类型的支持。 即，没有办法自动执行的一组对象的生存期结束时触发的操作。

- 本机类可以包含仅在托管类型中作为指针，然后在本机堆上分配。

我们想要包装在值类型而不是引用类型以避免双堆分配的小本机类： 包含本机类型，在本机堆和 CLR 堆来保存的托管的包装。 包装值类型中的本机类，你可以避免托管的堆中，但它无法自动执行的本机堆内存回收。 引用类型是在其中包装重要的本机类的唯一可行托管的类型。

## <a name="interior-pointers"></a>内部指针

`Form (2)` 和`Form (3)`更高版本可以解决这个世界或下一个 （也就是说，任何托管或本机类型） 中几乎任何类型。 因此，例如，以下所有允许在托管扩展：

```
__value struct V { int i; };
__gc struct R { V vr; };

V v = { 0 };  // Form (1)
V *pv = 0;  // Form (2)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0;  // Form (4)

R* r;

pv = &v;            // address a value type on the stack
pv = __nogc new V;  // address a value type on native heap
pv = pvgc;          // we are not sure what this addresses
pv = pvbx;          // address a boxed value type on managed heap
pv = &r->vr;        // an interior pointer to value type within a
                    //    reference type on the managed heap
```

因此，`V*`可以解决本地块内的位置 （并因此可以无关联），在全局范围内，在本机堆在 CLR 堆内 （例如，如果其所寻址的对象已被删除），（并因此将跟踪它是应重定位垃圾回收期间），并在 CLR 堆 （内部指针，因为此调用时，还以透明方式跟踪） 上的引用对象的内部。

在托管扩展中，没有方法分离出的本机方面`V*`; 也就是说，它被视为在其包含在内，用于处理其寻址的对象或托管堆上的子对象的可能性。

在新语法中，值类型指针可分解为两种类型： `V*`，这仅限于非 CLR 堆位置和内部指针`interior_ptr<V>`，允许但不需要托管堆中的地址。

```
// may not address within managed heap
V *pv = 0;

// may or may not address within managed heap
interior_ptr<V> pvgc = nullptr;
```

`Form (2)` 并`Form (3)`的托管扩展将映射到`interior_ptr<V>`。 `Form (4)` 是跟踪句柄。 它解决了已装箱到托管堆中的整个对象。 转换到新的语法中`V^`，

```
V^ pvbx = nullptr; // __box V* pvbx = 0;
```

全部映射到新语法中的内部指针的托管扩展中的以下声明。 (它们是值类型中的`System`命名空间。)

```
Int32 *pi;   // => interior_ptr<Int32> pi;
Boolean *pb; // => interior_ptr<Boolean> pb;
E *pe;       // => interior_ptr<E> pe; // Enumeration
```

内置类型不被认为是托管的类型，尽管它们执行操作作为对中的类型的别名`System`命名空间。 因此以下映射成立之间的托管扩展和新的语法：

```
int * pi;     // => int* pi;
int __gc * pi2; // => interior_ptr<int> pi2;
```

在转换时`V*`在现有程序中，最保守的策略是始终将它转换为`interior_ptr<V>`。 这是在托管扩展中已处理方式。 在新语法中，程序员可以选择通过指定将值类型限制为非托管堆地址`V*`而不是内部指针。 如果在转换程序时，可以执行它使用的所有可传递闭包，并确保所有已分配的地址均位于托管堆，然后将其保留为`V*`没问题。

## <a name="pinning-pointers"></a>钉住指针

垃圾回收器 （可选） 可能会移在压缩阶段通常驻留在 CLR 堆到堆中的其他位置的对象。 此移动不是与跟踪句柄、 跟踪引用和内部指针以透明方式更新这些实体的出现问题。 此移动是对象的一个问题，但是，如果用户已在运行时环境之外的 CLR 堆上传递的地址。 在这种情况下，可能会导致运行时失败是易失性移动的对象。 免除的对象，如的移动，我们必须本地将其固定到其位置的外部使用程度。

在托管扩展*钉住指针*声明的限定指针声明与`__pin`关键字。 下面是示例稍做修改的托管扩展规范：

```
__gc struct H { int j; };

int main()
{
   H * h = new H;
   int __pin * k = & h -> j;

   // ...
};
```

在新的语言设计中，语法类似于内部指针声明钉住指针。

```
ref struct H
{
public:
   int j;
};

int main()
{
   H^ h = gcnew H;
   pin_ptr<int> k = &h->j;

   // ...
}
```

在新语法的钉住指针是一种特殊情况的内部指针。 钉住指针的原始约束保持。 例如，它不能用作参数或返回类型的方法;它可以仅在本地对象上声明。 但是，具有在新语法中添加了许多其他约束。

钉住指针的默认值是`nullptr`，而不`0`。 一个`pin_ptr<>`无法初始化或分配`0`。 所有分配`0`现有代码中将需要更改为`nullptr`。

已允许钉住指针下的托管扩展来解决整个对象，如下面的示例摘自托管扩展规范中所示：

```
__gc class G {
public:
   void incr(int* pi) { pi += 1; }
};
__gc struct H { int j; };
void f( G * g ) {
   H __pin * pH = new H;
   g->incr(& pH -> j);
};
```

在新语法中，固定整个对象返回的`new`表达式不受支持。 而是需要固定的内部成员的地址。 例如，应用于对象的

```
ref class G {
public:
   void incr(int* pi) { *pi += 1; }
};
ref struct H { int j; };
void f( G^ g ) {
   H ^ph = gcnew H;
   Console::WriteLine(ph->j);
   pin_ptr<int> pj = &ph->j;
   g->incr(  pj );
   Console::WriteLine(ph->j);
}
```

## <a name="see-also"></a>请参阅

[值类型及其行为 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)<br/>
[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)