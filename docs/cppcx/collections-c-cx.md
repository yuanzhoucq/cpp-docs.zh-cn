---
title: 集合 (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: ff3fb9899355ec05083dc15c16d74c9aa1d3fd8f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740322"
---
# <a name="collections-ccx"></a>集合 (C++/CX)

在C++/cx 程序中，可以自由使用标准模板库（STL）容器或任何其他用户定义的集合类型。 但是，当你在 Windows 运行时的应用程序二进制接口（ABI）之间来回传递集合（例如，传递到 XAML 控件或 JavaScript 客户端）时，必须使用 Windows 运行时集合类型。

Windows 运行时定义集合和相关类型的接口，并且C++/cx 提供集合 .h 头文件C++中的具体实现。 下图显示了各个集合类型之间的关系：

![用于&#43;&#43;&#47;集合类型的 c cx 继承树](../cppcx/media/cppcxcollectionsinheritancetree.png "集合类型的 c&#43;&#43;&#47;cx 继承树")

- [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md) 类似于 [std::vector 类](../standard-library/vector-class.md)。

- [Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md) 类似于 [std::map 类](../standard-library/map-class.md)。

- [Platform::Collections::VectorView 类](../cppcx/platform-collections-vectorview-class.md) 和[Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md) 是 `Vector` 和 `Map`的只读版本。

- 迭代器是在 [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md)中定义的。 这些迭代器既满足了 STL 迭代器的要求，又使你能够对任何 [Windows::Foundation::Collections](../standard-library/algorithm-functions.md#find)接口类型或  [Platform::Collections](../standard-library/algorithm-functions.md#count_if)具体类型使用 [std::find](/uwp/api/windows.foundation.collections) 、 [std::count_if](../cppcx/platform-collections-namespace.md) 和其他 STL 算法。 例如，这意味着，你可以在中C#创建的 Windows 运行时组件中循环访问集合，并将 STL 算法应用于它。

   > [!IMPORTANT]
   > 代理迭代器 `VectorIterator` 和 `VectorViewIterator` 使用代理对象 `VectoryProxy<T>` 及 `ArrowProxy<T>` 实现与 STL 容器的共同使用。 有关更多信息，请参见本文后面的“VectorProxy 元素”。

- C++/Cx 集合类型支持的线程安全保证与 STL 容器支持的线程安全保证相同。

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) 和 [Windows::Foundation::Collections::IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) 定义了在集合以多种方式发生更改时触发的事件。 通过实现这些接口，  [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) 和 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) 支持与 XAML 集合的数据绑定。 例如，如果你有一个被数据绑定到 `Vector` 的 `Grid`，则当你向集合添加项目时，Grid UI 中会反映更改。

## <a name="vector-usage"></a>向量用法

如果你的类需要将序列容器传递到另一个 Windows 运行时组件， [请使用 Windows：： Foundation：：集合：：IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_)作为参数或返回类型， [Platform：：集合：：\<Vector t >](../cppcx/platform-collections-vector-class.md)作为具体实现。 如果你尝试在公共返回值或参数中使用 `Vector` 类型，则将引发编译器错误 C3986。 可以通过将 `Vector` 更改为 `IVector`来修复该错误。

> [!IMPORTANT]
> 如果您要在自己的程序中传递序列，请使用 `Vector` 或 `std::vector` ，因为它们比 `IVector`更高效。 在通过 ABI 传递容器时，仅使用 `IVector` 。
>
> Windows 运行时类型系统不支持交错数组的概念，因此不能将 IVector < Platform：： Array\<T > > 作为返回值或方法参数传递。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。

`Vector<T>` 提供添加、移除和访问集合项所需的方法，并且，它可以隐式转换为 `IVector<T>`。 还可以对 `Vector<T>`的实例使用 STL 算法。 下面的示例演示一些基本用法。 此处的 [begin 函数](../cppcx/begin-function.md) 和 [end 函数](../cppcx/end-function.md) 来自 `Platform::Collections` 命名空间而非 `std` 命名空间。

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

`std::vector`如果你有使用的现有代码，而你想要在 Windows 运行时组件中重用它，只需使用`Vector`一个构造函数，该`std::vector`构造函数采用一个`Vector`或一对迭代器在你将跨 ABI 收集。 下面的示例演示如何从 `Vector` 将 `std::vector`移动构造函数用于高效初始化。 移动操作完成后，原始的 `vec` 变量不再有效。

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

如果您有一个必须在将来某个时间点通过 ABI 传递的字符串向量，则您必须确定最初是将字符串创建为 `std::wstring` 类型还是 `Platform::String^` 类型。 如果你必须对字符串执行大量处理，请使用 `wstring`。 否则，请将字符串创建为 `Platform::String^` 类型，这可避免稍后转换它们的开销。 你还必须确定是将这些字符串内部置于 `std:vector` 还是 `Platform::Collections::Vector` 中。 作为一种常规做法，先使用 `std::vector` ，然后在通过 ABI 传递容器时从其创建一个 `Platform::Vector` 。

## <a name="value-types-in-vector"></a>Vector 中的值类型

要存储到 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) 中的任何元素必须支持相等性比较（隐式支持或通过使用你提供的自定义 [std::equal_to](../standard-library/equal-to-struct.md) 运算符支持）。 所有引用类型和所有标量类型都隐式支持相等性比较。 对于非标量值类型（如 [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime)）或自定义比较（如 `objA->UniqueID == objB->UniqueID`），必须提供自定义函数对象。

## <a name="vectorproxy-elements"></a>VectorProxy 元素

[Platform：：集合：： VectorIterator](../cppcx/platform-collections-vectoriterator-class.md)和[Platform：：集合：： VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md)允许将`range for`循环和算法（如[std：： sort](../standard-library/algorithm-functions.md#sort) ）与[IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_)容器一起使用。 但是，无法通过 C++ 指针取消引用来访问 `IVector` 元素，只能通过 [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) 和 [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) 方法访问此类元素。 因此，这些迭代器使用代理类`Platform::Details::VectorProxy<T>` ， `Platform::Details::ArrowProxy<T>`并通过 __\*__ 、 __->__ 和 __\[]__ 运算符提供对各个元素的访问，如标准库所要求。 严格来说，给定 `IVector<Person^> vec`， `*begin(vec)` 的类型为 `VectorProxy<Person^>`。 不过，代理对象对于你的代码几乎始终是透明的。 我们不讨论这些代理对象，因为它们仅由迭代器在内部使用，但了解该机制的工作原理将非常有用。

对 `range for` 容器使用 `IVector` 循环时，请使用 `auto&&` 以使迭代器变量正确绑定到 `VectorProxy` 元素。 如果使用 `auto` 或 `auto&`，将引发编译器警告 C4239，警告文本中将提到 `VectoryProxy` 。

下图演示了针对 `range for` 的 `IVector<Person^>`循环。 请注意，执行操作在第 64 行的断点处停止。 **“快速监视”** 窗口显示迭代器变量 `p` 实际上是具有 `VectorProxy<Person^>` 和 `m_v` 成员变量的 `m_i` 。 不过，当调用 `GetType` 时，它将返回与 `Person` 实例 `p2`相同的类型。 要点在于，虽然 `VectorProxy` 和 `ArrowProxy` 可能显示在 **“快速监视”** 、调试器的某些编译器错误或其他位置中，但通常不需要对它们进行显式编码。

![基于&#45;]范围内 for 循环(../cppcx/media/vectorproxy-1.png "VectorProxy&#45;")的 VectorProxy

必须针对代理对象进行编码的一种情况是，你必须对元素执行 `dynamic_cast` ，例如你在 `UIElement` 元素集合中寻找特定类型的 XAML 对象。 在此情况下，必须先将元素强制转换为 [Platform::Object](../cppcx/platform-object-class.md)^，然后执行动态强制转换：

```cpp
void FindButton(UIElementCollection^ col)
{
    // Use auto&& to avoid warning C4239
    for (auto&& elem : col)
    {
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));
        if (nullptr != temp)
        {
            // Use temp...
        }
    }
}
```

## <a name="map-usage"></a>映射用法

此示例演示如何在[Platform：：集合：： Map](../cppcx/platform-collections-map-class.md)中插入并查找项目，然后将`Map`作为只读 [Windows：： Foundation：：集合：： IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_）返回类别.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

通常，对于内部映射功能，出于性能考虑，应尽可能首选 `std::map` 类型。 如果必须通过 ABI 传递容器，请从 [std::map](../cppcx/platform-collections-map-class.md) 构造一个 [Platform::Collections::Map](../standard-library/map-class.md) ，然后将 `Map` 作为 [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)返回。 如果你尝试在公共返回值或参数中使用 `Map` 类型，则将引发编译器错误 C3986。 可以通过将 `Map` 更改为 `IMap`来修复该错误。 在某些情况下，例如，如果您不需要大量查找或插入，而需要通过 ABI 频繁传递集合，则在一开始使用 `Platform::Collections::Map` 可能成本较低，同时可避免转换 `std::map`的开销。 在任何情况下，应避免在 `IMap` 上执行查找和插入操作，因为这些是三种类型中性能最差的操作。 仅在你通过 ABI 传递容器之处转换为 `IMap` 。

## <a name="value-types-in-map"></a>Map 中的值类型

[Platform::Collections::Map](../cppcx/platform-collections-map-class.md) 中的元素已进行排序。 要存储到 `Map` 中的任何元素都必须支持严格弱排序中的小于比较（隐式支持或使用您提供的自定义 [stl::less](../standard-library/less-struct.md) 比较运算符支持）。 标量类型隐式支持比较。 对于非标量类型（如 `Windows::Foundation::DateTime`）或自定义比较（如 `objA->UniqueID < objB->UniqueID`），你必须提供自定义比较器。

## <a name="collection-types"></a>集合类型

集合分为四种类别：序列集合和关联集合各自的可修改版本和只读版本。 此外，/Cx C++通过提供三个迭代器类来简化集合的访问，从而增强集合。

可以更改可修改集合的元素，但是，只读集合的元素（称作 *视图*）只能读取。 [Platform：： collection：： Vector](../cppcx/platform-collections-vector-class.md)或[platform：： Collection：： VectorView](../cppcx/platform-collections-vectorview-class.md)集合的元素可以通过使用迭代器或集合的[Vector：： GetAt](../cppcx/platform-collections-vector-class.md#getat)和索引进行访问。 可以使用集合的[Map：： Lookup](../cppcx/platform-collections-map-class.md#lookup)和键访问关联集合的元素。

[Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)<br/>
可修改的关联集合。 映射元素为键/值对。 支持查找键以检索其关联值，也支持遍历所有键值对。

`Map` 和 `MapView` 在 `<K, V, C = std::less<K>>`上模板化，因此，你可以自定义比较器。  此外， `Vector` 和 `VectorView` 在 `<T, E = std::equal_to<T>>` 上模板化，以便你可以自定义 `IndexOf()`的行为。 这通常对于值结构的 `Vector` 和 `VectorView` 非常重要。 例如，若要创建 Vector\<Windows：： Foundation：:D atetime >，必须提供自定义比较运算符，因为 DateTime 不会重载 = = 运算符。

[Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md)<br/>
`Map`的只读版本。

[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)<br/>
可修改的序列集合。 `Vector<T>` 支持定时随机访问和分摊定时 [追加](../cppcx/platform-collections-vector-class.md#append) 操作。

[Platform::Collections::VectorView 类](../cppcx/platform-collections-vectorview-class.md)<br/>
`Vector`的只读版本。

[Platform::Collections::InputIterator 类](../cppcx/platform-collections-inputiterator-class.md)<br/>
满足 STL 输入迭代器要求的 STL 迭代器。

[Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)<br/>
满足 STL 可变随机访问迭代器要求的 STL 迭代器。

[Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
满足 STL  `const` 随机访问迭代器要求的 STL 迭代器。

### <a name="begin-and-end-functions"></a>begin() 和 end() 函数

为简化使用 STL 以处理`Vector` `MapView` `Map`、 `VectorView`、、和`Windows::Foundation::Collections`任意对象， C++/cx 支持对[begin 函数](../cppcx/begin-function.md)和[end 函数](../cppcx/end-function.md)非成员的重载函数.

下表列出可用迭代器和函数。

|Iterators|函数|
|---------------|---------------|
|[Platform::Collections::VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> （在内部[存储 Windows：： Foundation：：集合：：IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_)和 int。）|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md)([Windows::Foundation::Collections::IVector\<T >](/uwp/api/Windows.Foundation.Collections.IVector_T_)）|
|[Platform::Collections::VectorViewIterator\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> （在内部[存储\<IVectorView T >](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^ 和 int。）|[开始](../cppcx/begin-function.md)/ [端](../cppcx/end-function.md)（[IVectorView\<T>](/uwp/api/Windows.Foundation.Collections.IVectorView_T_)^）|
|[Platform::Collections::InputIterator\<T>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> （在内部[存储\<iiterator<t> t >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ 和 t。）|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IIterable\<T>](/uwp/api/Windows.Foundation.Collections.IIterable_T_))|
|[Platform：：集合：： InputIterator < IKeyValuePair\<K，V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> （在内部[存储\<iiterator<t> t >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ 和 t。）|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([IMap\<K,V>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|
|[Platform：：集合：： InputIterator < IKeyValuePair\<K，V > ^ >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> （在内部[存储\<iiterator<t> t >](/uwp/api/Windows.Foundation.Collections.IIterator_T_)^ 和 t。）|[begin](../cppcx/begin-function.md)/ [end](../cppcx/end-function.md) ([Windows::Foundation::Collections::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_))|

### <a name="collection-change-events"></a>集合更改事件

`Vector` 和 `Map` 支持 XAML 集合中的数据绑定，方式是通过实现在更改或重置集合对象，或在插入、移除或更改集合的任何元素时发生的事件。 您可编写自己的支持数据绑定的类型，尽管因这些类型是密封类型而导致无法从 `Map` 或 `Vector` 继承。

[Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) 和 [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) 委托用于指定集合更改事件的事件处理程序的签名。 [Windows::Foundation::Collections::CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) 公共枚举类和 `Platform::Collection::Details::MapChangedEventArgs` 与 `Platform::Collections::Details::VectorChangedEventArgs` ref 类用于存储事件参数以确定引发事件的原因。 类型是`Map`在命名空间中定义的，因为你在使用或`Vector`时无需显式构造或使用它们。 `Details` `*EventArgs`

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[C++/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)
