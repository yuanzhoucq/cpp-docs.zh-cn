---
title: Platform::Collections::UnorderedMap 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: 3c95f4a982e23d757b330ecadcae5cfbfd6fd531
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213068"
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap 类

表示一个无序 ** 映射，它是键值对的集合。

## <a name="syntax"></a>语法

```cpp
template <
   typename K,
   typename V,
   typename C = std::equal_to<K>
>
ref class Map sealed;
```

#### <a name="parameters"></a>参数

*温度*<br/>
键值对中键的类型。

*向量*<br/>
键值对中值的类型。

*C*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认情况下， [std：： \<K> equal_to](../standard-library/equal-to-struct.md)。

### <a name="remarks"></a>备注

允许的类型是：

- integers

- 接口类 ^

- 公共 ref 类

- value struct

- 公共枚举类

**UnorderedMap**基本上是支持存储 Windows 运行时类型的[std：： unordered_map](../standard-library/unordered-map-class.md)的包装。 它是在公共 Windows 运行时接口之间传递的[Windows：： Foundation：：集合：： IMap](/uwp/api/windows.foundation.collections.imap-2)和[IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2)类型的具体实现。 如果你尝试在公共返回值或参数中使用 `Platform::Collections::UnorderedMap` 类型，则将引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2)可修复该错误。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[UnorderedMap：： UnorderedMap](#ctor)|初始化 Map 类的新实例。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[UnorderedMap：： Clear](#clear)|从当前 Map 对象中移除所有键值对。|
|[UnorderedMap：： First](#first)|返回指定映射中第一个元素的迭代器。|
|[UnorderedMap：： GetView](#getview)|返回当前 Map 的只读视图，即 Platform::Collections::UnorderedMapView 类。|
|[UnorderedMap：： HasKey](#haskey)|确定当前 Map 中是否包含指定键。|
|[UnorderedMap：： Insert](#insert)|将指定的键值对添加到当前 Map 对象中。|
|[UnorderedMap：： Lookup](#lookup)|检索当前 Map 对象中指定键处的元素。|
|[UnorderedMap：： Remove](#remove)|从当前 Map 对象中删除指定的键值对。|
|[UnorderedMap：： Size](#size)|返回当前 Map 对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|名称|描述|
|[Map：： MapChanged](#mapchanged)事件|当映射更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`UnorderedMap`

### <a name="requirements"></a>要求

**标头：** 集合。h

**命名空间：** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a>UnorderedMap：： Clear 方法

从当前 UnorderedMap 对象中移除所有键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>UnorderedMap：： First 方法

返回一个迭代器，该迭代器指定无序映射中的第一个[Windows \<K,V> ：： Foundation：：集合：： IKeyValuePair](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>返回值

指定映射中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存第一个（）返回的迭代器的一种简便方法是将返回值分配给使用 **`auto`** 类型推导关键字声明的变量。 例如，`auto x = myUnorderedMap->First();`。

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>UnorderedMap：： GetView 方法

返回当前 UnorderedMap 的只读视图;即实现[Windows：： Foundation：：集合：： IMapView：： IMapView](/uwp/api/windows.foundation.collections.imapview-2)接口的[Platform：：集合：： UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>返回值

一个 `UnorderedMapView` 对象。

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>UnorderedMap：： HasKey 方法

确定当前 UnorderedMap 中是否包含指定键。

### <a name="syntax"></a>语法

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位 UnorderedMap 元素的键。 *键*类型为 typename *K*。

### <a name="return-value"></a>返回值

**`true`** 如果找到该键，则为;否则为 **`false`** 。

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>UnorderedMap：： Insert 方法

将指定的键值对添加到当前 UnorderedMap 对象中。

### <a name="syntax"></a>语法

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>参数

*key*<br/>
键值对中的键部分。 *键*类型为 typename *K*。

*value*<br/>
键值对中的值部分。 *值*的类型为 typename *V*。

### <a name="return-value"></a>返回值

**`true`** 如果当前映射中现有元素的键与*键*匹配，并且该元素的值部分设置为*value*。 **`false`** 如果当前映射中没有任何现有元素匹配*键*，并且*键*和*值*参数成为键值对并随后添加到当前 UnorderedMap 中，则为。

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>UnorderedMap：： Lookup 方法

检索与类型 K 的指定键关联的类型 V 的值。

### <a name="syntax"></a>语法

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位 UnorderedMap 中的元素的键。 *键*类型为 typename *K*。

### <a name="return-value"></a>返回值

与*键*配对的值。 返回值的类型为 typename *V*。

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>UnorderedMap：： MapChanged

项目插入到映射中或从映射中移除时引发。

### <a name="syntax"></a>语法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>属性值/返回值

一个[MapChangedEventHandler \<K,V> ](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) ，其中包含有关引发事件的对象的信息，以及发生的更改类型。 另请[参阅 \<K> Imapchangedeventargs<k>](/uwp/api/windows.foundation.collections.imapchangedeventargs-1)和[CollectionChange 枚举](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

Windows 运行时美国 c # 或 Visual Basic 项目 IMap \<K,V> 作为 IDictionary 的应用 \<K,V> 。

## <a name="unorderedmapremove-method"></a><a name="remove"></a>UnorderedMap：： Remove 方法

从 UnorderedMap 对象中删除指定的键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>参数

*key*<br/>
键值对中的键部分。 *键*类型为 typename *K*。

## <a name="unorderedmapsize-method"></a><a name="size"></a>UnorderedMap：： Size 方法

返回 UnorderedMap 中的[Windows：： Foundation：：集合：： IKeyValuePair \<K,V> ](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素的数目。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

UnorderedMap 中的元素数目。

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>UnorderedMap：： UnorderedMap 构造函数

初始化 UnorderedMap 类的新实例。

### <a name="syntax"></a>语法

```cpp
UnorderedMap();

explicit UnorderedMap(
    size_t n
    );

UnorderedMap(
    size_t n,
    const H& h
    );

UnorderedMap(
    size_t n,
    const H& h,
    const P& p
    );

explicit UnorderedMap(
    const std::unordered_map<K, V, H, P>& m
    );

explicit UnorderedMap(
    std::unordered_map<K, V, H, P>&& m
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h
    );

template <typename InIt>
UnorderedMap(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h
    );

UnorderedMap(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p
    );
```

### <a name="parameters"></a>参数

*InIt*<br/>
当前 UnorderedMap 的类型名称。

*P*<br/>
可比较两个键以确定它们是否相等的函数对象。 此参数默认为[std：： equal_to \<K> ](../standard-library/equal-to-struct.md)。

*H*<br/>
可以为键生成哈希值的函数对象。 对于类支持的键类型，此参数默认为 "[哈希类 1](../standard-library/hash-class.md) "。

*m*<br/>
用于初始化当前 UnorderedMap 的[std：： unordered_map](../standard-library/unordered-map-class.md)的引用、[左值和右](../cpp/lvalues-and-rvalues-visual-cpp.md)。

*il*<br/>
Std： [： initializer_list](../standard-library/initializer-list-class.md) [std：:p](../standard-library/pair-structure.md)用于初始化地图的空气对象。

*first*<br/>
用于初始化当前 UnorderedMap 的一系列元素中的第一个元素的输入迭代器。

*last*<br/>
用于初始化当前 UnorderedMap 的一系列元素之后的第一个元素的输入迭代器。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)<br/>
[Platform：：集合命名空间](../cppcx/platform-collections-namespace.md)<br/>
[Platform：：集合：： Map 类](../cppcx/platform-collections-map-class.md)<br/>
[Platform：：集合：： UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[集合](../cppcx/collections-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
