---
title: Platform::Collections::UnorderedMapView 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- collection/Platform::Collections::UnorderedMapView
ms.assetid: 545a3725-2efd-4cc1-b590-4a7cd2351f61
ms.openlocfilehash: f0096982ad5d11b9ea394c9f02ba748a52e4216b
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031480"
---
# <a name="platformcollectionsunorderedmapview-class"></a>Platform::Collections::UnorderedMapView 类

将一个只读视图表示为一个 ** 映射，这是键值对的集合。

## <a name="syntax"></a>语法

```cpp
template <
   typename K,
   typename V,
   typename C = ::std::equal_to<K>>
ref class UnorderedMapView sealed;
```

#### <a name="parameters"></a>参数

*K*<br/>
键值对中键的类型。

*五*<br/>
键值对中值的类型。

*C*<br/>
提供可比较两个键值是否相等的函数对象的类型。 默认情况下[，std：：equal_to\<K>](../standard-library/equal-to-struct.md)

### <a name="remarks"></a>备注

无序的 MapView 是[Windows：：基础：集合：：iMapView\<K，V>](/uwp/api/windows.foundation.collections.imapview-2)接口 C++的具体实现，这些接口通过应用程序二进制接口 （ABI） 传递。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[无序地图视图：无序地图视图](#ctor)|初始化 UnorderedMapView 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[无序的地图视图：第一](#first)|返回初始化为映射视图中第一个元素的迭代器。|
|[无序地图视图：：哈斯键](#haskey)|确定当前 UnorderedMapView 中是否包含指定键。|
|[无序的地图视图：：查找](#lookup)|检索当前 UnorderedMapView 对象中指定键处的元素。|
|[无序的地图视图：大小](#size)|返回当前 UnorderedMapView 对象中的元素数目。|
|[无序的地图视图：拆分](#split)|将原始 UnorderedMapView 对象拆分成两个 UnorderedMapView 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`UnorderedMapView`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="unorderedmapviewfirst-method"></a><a name="first"></a>无序的 MapView：第一种方法

返回指定第一个[Windows：：基础：集合：：iKeyValuePair\<K，V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)无序映射中的元素的迭代器。

### <a name="syntax"></a>语法

```cpp
virtual Windows::Foundation::Collections::IIterator<
    Windows::Foundation::Collections::IKeyValuePair<K, V>^>^
    First();
```

### <a name="return-value"></a>返回值

指定映射视图中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存 First（） 返回的迭代器的一个方便方法是将返回值分配给使用**自动**类型扣减关键字声明的变量。 例如，`auto x = myMapView->First();` 。

## <a name="unorderedmapviewhaskey-method"></a><a name="haskey"></a>无序的 MapView：：有键方法

确定当前 UnorderedMap 中是否包含指定键。

### <a name="syntax"></a>语法

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>参数

*键*<br/>
用于定位元素的键。 的类型`key`是类型名称*K*。

### <a name="return-value"></a>返回值

如果找到密钥，**则为 true;** 否则，**假**。

## <a name="unorderedmapviewlookup-method"></a><a name="lookup"></a>无序的 MapView：查找方法

检索与类型 K 的指定键关联的类型 V 的值。

### <a name="syntax"></a>语法

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>参数

*键*<br/>
用于定位 UnorderedMapView 中的元素的键。 的类型`key`是类型名称*K*。

### <a name="return-value"></a>返回值

与 `key` 配对的值。 返回值的类型为类型名称*V*。

## <a name="unorderedmapviewsize-method"></a><a name="size"></a>无序映射视图：大小方法

返回"无序地图视图"中的窗口数[：：基础：集合：：iKeyValuePair\<K，V>](/uwp/api/windows.foundation.collections.ikeyvaluepair-2)元素。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

UnorderedMapView 中的元素数目。

## <a name="unorderedmapviewsplit-method"></a><a name="split"></a>无序映射视图：：拆分方法

将当前 UnorderedMapView 对象分成两个 UnorderedMapView 对象。 此方法为非操作性的。

### <a name="syntax"></a>语法

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K,V>^ * secondPartition);
```

### <a name="parameters"></a>参数

*第一个分区*<br/>
原始 UnorderedMapView 对象的第一部分。

*第二个分区*<br/>
原始 UnorderedMapView 对象的第二部分。

### <a name="remarks"></a>备注

此方法为非操作性的，它不执行任何操作。

## <a name="unorderedmapviewunorderedmapview-constructor"></a><a name="ctor"></a>无序 MapView：无序的 MapView 构造函数

初始化 UnorderedMapView 类的新实例。

### <a name="syntax"></a>语法

```cpp
UnorderedMapView();
explicit UnorderedMapView(size_t n);
UnorderedMapView(size_t n, const H& h);
UnorderedMapView(size_t n, const H& h, const P& p);

explicit UnorderedMapView(
    const std::unordered_map<K, V, H, P>& m);
explicit UnorderedMapView(
    std::unordered_map<K, V, H, P>&& m);

template <typename InIt> UnorderedMapView(InIt first, InIt last );
template <typename InIt> UnorderedMapView(InIt first, InIt last, size_t n );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h );

template <typename InIt> UnorderedMapView(
    InIt first,
    InIt last,
    size_t n,
    const H& h,
    const P& p );

UnorderedMapView(std::initializer_list<std::pair<const K, V>);

UnorderedMapView(std::initializer_list< std::pair<const K, V>> il, size_t n

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h);

UnorderedMapView(
    std::initializer_list< std::pair<const K, V>> il,
    size_t n,
    const H& h,
    const P& p );
```

### <a name="parameters"></a>参数

*n*<br/>
要预分配空间的元素数目。

*Init*<br/>
UnorderedMapView 的类型名称。

*H*<br/>
可以为键生成哈希值的函数对象。 默认值为[std：：：哈希\<K>](../standard-library/hash-class.md)支持的类型`std::hash`。

*P*<br/>
提供可比较两个键以确定其相等性的函数对象的类型。 默认值为[：equal_to\<K>](../standard-library/equal-to-struct.md)。

*米*<br/>
用于初始化无序 MapView 的[std：：unordered_map](../standard-library/unordered-map-class.md)的引用或[Lvalue 和 Rvalue。](../cpp/lvalues-and-rvalues-visual-cpp.md)

*第一*<br/>
用于初始化 UnorderedMapView 的一系列元素中的第一个元素的输入迭代器。

*最后*<br/>
用于初始化 UnorderedMapView 的一系列元素之后的第一个元素的输入迭代器。

## <a name="see-also"></a>请参阅

[Platform::Collections 命名空间](../cppcx/platform-collections-namespace.md)<br/>
[Windows::Foundation::IMapView](/uwp/api/windows.foundation.collections.imapview-2)
