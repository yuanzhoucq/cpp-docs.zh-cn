---
title: "Platform::Collections::UnorderedMap 类 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Platform::Collections::UnorderedMap
ms.assetid: dc84f261-b13c-4c0a-9b57-30dcb9e3065e
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b2266e43f3168fca823147f4c2c7e2c33513343
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2018
---
# <a name="platformcollectionsunorderedmap-class"></a>Platform::Collections::UnorderedMap 类

表示一个无序 映射，它是键值对的集合。

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

*K*  
键值对中键的类型。

*V*  
键值对中值的类型。

*C*  
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在映射中的相对顺序。 默认情况下， [std:: equal_to\<K >](../standard-library/equal-to-struct.md)。

### <a name="remarks"></a>备注

允许的类型包括：

- 整数

- 接口类 ^

- 公共 ref 类

- value struct

- 公共枚举类

**UnorderedMap**基本上是包装器[std:: unordered_map](../standard-library/unordered-map-class.md)支持 Windows 运行时类型的存储。 它是的具体实现[Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)和[IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_)公共之间传递的类型 Windows 运行时接口。 如果你尝试在公共返回值或参数中使用 `Platform::Collections::UnorderedMap` 类型，则将引发编译器错误 C3986。 可通过更改参数或返回值的类型来修复该错误[Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_)。

有关详细信息，请参阅[集合](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[UnorderedMap::UnorderedMap](#ctor)|初始化 Map 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[UnorderedMap::Clear](#clear)|从当前 Map 对象中移除所有键值对。|
|[UnorderedMap::First](#first)|返回指定映射中第一个元素的迭代器。|
|[UnorderedMap::GetView](#getview)|返回当前 Map 的只读视图，即 Platform::Collections::UnorderedMapView 类。|
|[UnorderedMap::HasKey](#haskey)|确定当前 Map 中是否包含指定键。|
|[UnorderedMap::Insert](#insert)|将指定的键值对添加到当前 Map 对象中。|
|[UnorderedMap::Lookup](#lookup)|检索当前 Map 对象中指定键处的元素。|
|[UnorderedMap::Remove](#remove)|从当前 Map 对象中删除指定的键值对。|
|[UnorderedMap::Size](#size)|返回当前 Map 对象中的元素数目。|

### <a name="events"></a>事件

|||
|-|-|
|name|描述|
|[Map:: mapchanged](#mapchanged)事件|当映射更改时发生。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`UnorderedMap`

### <a name="requirements"></a>惠?

**标头：** collection.h

**命名空间：** Platform::Collections

## <a name="clear"></a>Unorderedmap:: Clear 方法

从当前 UnorderedMap 对象中移除所有键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Clear();
```

## <a name="first"></a>Unorderedmap:: First 方法

返回一个迭代器，指定第一个[Windows::Foundation::Collections::IKeyValuePair\<K，V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx)无序映射中的元素。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ 
   First();
```

### <a name="return-value"></a>返回值

指定映射中第一个元素的迭代器。

### <a name="remarks"></a>备注

保留 first 返回的迭代器一种简便方式是将返回值分配给使用声明的变量**自动**类型推导关键字。 例如 `auto x = myUnorderedMap->First();`。

## <a name="getview"></a>Unorderedmap:: Getview 方法

返回当前 UnorderedMap 中; 的只读视图也就是说， [Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)实现[Windows::Foundation::Collections::IMapView::IMapView](http://msdn.microsoft.com/library/windows/apps/br226037.aspx)接口。

### <a name="syntax"></a>语法

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>返回值

一个 `UnorderedMapView` 对象。

## <a name="haskey"></a>Unorderedmap:: Haskey 方法

确定当前 UnorderedMap 中是否包含指定键。

### <a name="syntax"></a>语法

```cpp
bool HasKey(
   K key
);
```

### <a name="parameters"></a>参数

*key*  
用于定位 UnorderedMap 元素的键。 一种*密钥*名称*K*。

### <a name="return-value"></a>返回值

如果找到该键，则为 `true`；否则为 `false`。

## <a name="insert"></a>  UnorderedMap::Insert Method

将指定的键值对添加到当前 UnorderedMap 对象中。

### <a name="syntax"></a>语法

```cpp
virtual bool Insert(
   K key,
   V value
);
```

### <a name="parameters"></a>参数

*key*  
键值对中的键部分。 一种*密钥*名称*K*。

*值*  
键值对中的值部分。 一种*值*名称*V*。

### <a name="return-value"></a>返回值

`true`如果当前映射中一个现有元素的键匹配*密钥*并且该元素的值部分设置为*值*。 `false`如果当前映射中的没有任何现有元素匹配*密钥*和*密钥*和*值*参数构成键值对并随后添加到当前 UnorderedMap。

## <a name="lookup"></a>Unorderedmap:: Lookup 方法

检索与类型 K 的指定键关联的类型 V 的值。

### <a name="syntax"></a>语法

```cpp
V Lookup(
   K key
);
```

### <a name="parameters"></a>参数

*key*  
用于定位 UnorderedMap 中的元素的键。 一种*密钥*名称*K*。

### <a name="return-value"></a>返回值

与成对的值*密钥*。 返回值的类型是 e *V*。

## <a name="mapchanged"></a>  UnorderedMap::MapChanged

项目插入到映射中或从映射中移除时引发。

### <a name="syntax"></a>语法

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>属性值/返回值

A [MapChangedEventHandler\<K，V >](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) ，包含有关引发该事件，然后所发生的更改类型的对象信息。 另请参阅[IMapChangedEventArgs\<K >](http://msdn.microsoft.com/library/windows/apps/br226034.aspx)和[CollectionChange 枚举](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx)。

## <a name="net-framework-equivalent"></a>.NET Framework 等效项

Windows 应用商店应用的 C# 或 Visual Basic 项目 IMap\<K，V > 作为 IDictionary\<K，V >。

## <a name="remove"></a>Unorderedmap:: Remove 方法

从 UnorderedMap 对象中删除指定的键值对。

### <a name="syntax"></a>语法

```cpp
virtual void Remove(
   K key);
```

### <a name="parameters"></a>参数

*key*  
键值对中的键部分。 一种*密钥*名称*K*。

## <a name="size"></a>Unorderedmap:: Size 方法

返回的数目[Windows::Foundation::Collections::IKeyValuePair\<K，V >](http://msdn.microsoft.com/library/windows/apps/br226031.aspx) UnorderedMap 中的元素。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

UnorderedMap 中的元素数目。

## <a name="ctor"></a>  UnorderedMap::UnorderedMap 构造函数

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

*InIt*  
当前 UnorderedMap 的类型名称。

*P*  
可比较两个键以确定它们是否相等的函数对象。 此参数默认为[std:: equal_to\<K >](../standard-library/equal-to-struct.md)。

*H*  
可以为键生成哈希值的函数对象。 此参数默认为[哈希类 1](../standard-library/hash-class.md)键类型的类支持。

*m*  
引用或[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)到[std:: unordered_map](../standard-library/unordered-map-class.md)用于初始化当前 UnorderedMap。

*il* A [std:: initializer_list](../standard-library/initializer-list-class.md)的[std:: pair](../standard-library/pair-structure.md)用于初始化映射的对象。

*first*  
用于初始化当前 UnorderedMap 的一系列元素中的第一个元素的输入迭代器。

*last*  
用于初始化当前 UnorderedMap 的一系列元素之后的第一个元素的输入迭代器。

## <a name="see-also"></a>请参阅

[平台 Namespace](platform-namespace-c-cx.md)  
[Platform::Collections 命名空间](../cppcx/platform-collections-namespace.md)  
[Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)  
[Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)  
[集合](../cppcx/collections-c-cx.md)  
[C + + 创建 Windows 运行时组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)  
