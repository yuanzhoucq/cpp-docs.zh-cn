---
title: Platform::Collections::UnorderedMap 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
ms.openlocfilehash: c6f702850f5bf84b8b1bc857c9d0a744728d0cbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354419"
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

*K*<br/>
键值对中键的类型。

*五*<br/>
键值对中值的类型。

*C*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认情况下[，std：：equal_to\<K>](../standard-library/equal-to-struct.md)。

### <a name="remarks"></a>备注

允许的类型是：

- 整数

- 接口类*

- 公共 ref 类

- value struct

- 公共枚举类

**无序映射**基本上是用于支持存储 Windows 运行时类型的[unordered_map](../standard-library/unordered-map-class.md)的包装。 它是[Windows：：基础：集合：：IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)和[I 可观察映射](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_)类型的具体实现，它们通过公共 Windows 运行时接口传递。 如果你尝试在公共返回值或参数中使用 `Platform::Collections::UnorderedMap` 类型，则将引发编译器错误 C3986。 通过将参数或返回值的类型更改为 [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)可修复该错误。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[无序映射：无序映射](#ctor)|初始化 Map 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[无序映射：：清除](#clear)|从当前 Map 对象中移除所有键值对。|
|[无序映射：：第一](#first)|返回指定映射中第一个元素的迭代器。|
|[无序映射：获取视图](#getview)|返回当前 Map 的只读视图，即 Platform::Collections::UnorderedMapView 类。|
|[无序映射：：哈斯键](#haskey)|确定当前 Map 中是否包含指定键。|
|[无序映射：：插入](#insert)|将指定的键值对添加到当前 Map 对象中。|
|[无序映射：：查找](#lookup)|检索当前 Map 对象中指定键处的元素。|
|[无序映射：：删除](#remove)|从当前 Map 对象中删除指定的键值对。|
|[无序映射：：大小](#size)|返回当前 Map 对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|名称|说明|
|[映射：：映射已更改](#mapchanged)事件|当映射更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`UnorderedMap`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="unorderedmapclear-method"></a><a name="clear"></a>无序映射：：清除方法

从当前 UnorderedMap 对象中移除所有键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="unorderedmapfirst-method"></a><a name="first"></a>无序映射：：第一种方法

返回指定第一个[Windows：：基础：集合：：iKeyValuePair\<K，V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)无序映射中的元素的迭代器。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
   First();
```

### <a name="return-value"></a>返回值

指定映射中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存 First（） 返回的迭代器的一个方便方法是将返回值分配给使用**自动**类型扣减关键字声明的变量。 例如，`auto x = myUnorderedMap->First();` 。

## <a name="unorderedmapgetview-method"></a><a name="getview"></a>无序映射：：获取查看方法

返回当前无序地图的只读视图;即[，平台：集合：：：](../cppcx/platform-collections-unorderedmapview-class.md)实现 [Windows：：基础：集合：集合：iMapView：：iMapView]/uwp/api/Windows.Foundation.集合.IMapView_K_V_）接口的无序 MapView 类。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>返回值

一个 `UnorderedMapView` 对象。

## <a name="unorderedmaphaskey-method"></a><a name="haskey"></a>无序映射：：有键方法

确定当前 UnorderedMap 中是否包含指定键。

### <a name="syntax"></a>语法

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>参数

*关键*<br/>
用于定位 UnorderedMap 元素的键。 *键*的类型是类型名称*K*。

### <a name="return-value"></a>返回值

如果找到密钥，**则为 true;** 否则，**假**。

## <a name="unorderedmapinsert-method"></a><a name="insert"></a>无序映射：：插入方法

将指定的键值对添加到当前 UnorderedMap 对象中。

### <a name="syntax"></a>语法

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>参数

*关键*<br/>
键值对中的键部分。 *键*的类型是类型名称*K*。

*value*<br/>
键值对中的值部分。 *值*的类型是类型名称*V*。

### <a name="return-value"></a>返回值

如果当前 Map 中现有元素的键与*键*匹配，并且该元素的值部分设置为*值*，**则为 true。** 如果当前 Map 中不存在现有元素与*键*匹配，并且*键*和*值*参数被制成键值对，然后添加到当前无序映射，**则为 false。**

## <a name="unorderedmaplookup-method"></a><a name="lookup"></a>无序映射：：查找方法

检索与类型 K 的指定键关联的类型 V 的值。

### <a name="syntax"></a>语法

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>参数

*关键*<br/>
用于定位 UnorderedMap 中的元素的键。 *键*的类型是类型名称*K*。

### <a name="return-value"></a>返回值

与*键*配对的值。 返回值的类型为类型名称*V*。

## <a name="unorderedmapmapchanged"></a><a name="mapchanged"></a>无序映射：：已映射

项目插入到映射中或从映射中移除时引发。

### <a name="syntax"></a>语法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>属性值/返回值

[MapChangeEventHandler\<K，V>，](/uwp/api/windows.foundation.collections.mapchangedeventhandler)其中包含有关引发事件的对象以及发生的更改类型的信息。 另请参阅[IMapChangeEventArgs\<K>](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_)和[集合更改枚举](/uwp/api/windows.foundation.collections.collectionchange)。

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

Windows 运行时应用，我们 C# 或可视化基本项目\<IMap K，V\<>为 I字典 K，V>。

## <a name="unorderedmapremove-method"></a><a name="remove"></a>无序映射：：删除方法

从 UnorderedMap 对象中删除指定的键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>参数

*关键*<br/>
键值对中的键部分。 *键*的类型是类型名称*K*。

## <a name="unorderedmapsize-method"></a><a name="size"></a>无序映射：：大小方法

返回"无序地图"中[的窗口：：：基础：集合：：IKeyValuePair\<K，V>](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_)元素。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

UnorderedMap 中的元素数目。

## <a name="unorderedmapunorderedmap-constructor"></a><a name="ctor"></a>无序映射：：无序映射构造函数

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

*Init*<br/>
当前 UnorderedMap 的类型名称。

*P*<br/>
可比较两个键以确定它们是否相等的函数对象。 此参数默认为[std：：equal_to\<K>](../standard-library/equal-to-struct.md)。

*H*<br/>
可以为键生成哈希值的函数对象。 此参数默认为类支持的关键类型的[哈希类 1。](../standard-library/hash-class.md)

*米*<br/>
对[std：：unordered_map](../standard-library/unordered-map-class.md)的引用或[Lvalue 和 Rvalue，](../cpp/lvalues-and-rvalues-visual-cpp.md)用于初始化当前无序映射。

*I l*<br/>
用于初始化地图的[std：initializer_list：:p空气](../standard-library/pair-structure.md)对象。 [std::initializer_list](../standard-library/initializer-list-class.md)

*第一*<br/>
用于初始化当前 UnorderedMap 的一系列元素中的第一个元素的输入迭代器。

*最后*<br/>
用于初始化当前 UnorderedMap 的一系列元素之后的第一个元素的输入迭代器。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)<br/>
[Platform::Collections 命名空间](../cppcx/platform-collections-namespace.md)<br/>
[Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)<br/>
[平台：：集合：：无序的 MapView 类](../cppcx/platform-collections-unorderedmapview-class.md)<br/>
[集合](../cppcx/collections-c-cx.md)<br/>
[用 C++ 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
