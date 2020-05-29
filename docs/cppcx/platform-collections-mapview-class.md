---
title: Platform::Collections::MapView 类
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::MapView::MapView
- COLLECTION/Platform::Collections::MapView::First
- COLLECTION/Platform::Collections::MapView::HasKey
- COLLECTION/Platform::Collections::MapView::Lookup
- COLLECTION/Platform::Collections::MapView::Size
- COLLECTION/Platform::Collections::MapView::Split
helpviewer_keywords:
- MapView Class
ms.assetid: 9577dde7-f599-43c6-b1e4-7d653706fd62
ms.openlocfilehash: 98c146cec2febefee9c16528bee8f6be83f2a026
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032429"
---
# <a name="platformcollectionsmapview-class"></a>Platform::Collections::MapView 类

将一个只读视图表示为一个 ** 映射，这是键值对的集合。

## <a name="syntax"></a>语法

```
template <
   typename K,
   typename V,
   typename C = ::std::less<K>>
ref class MapView sealed;
```

#### <a name="parameters"></a>参数

*K*<br/>
键值对中键的类型。

*五*<br/>
键值对中值的类型。

*C*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序。 默认情况下[，std：：减去\<K>](../standard-library/less-struct.md)。

### <a name="remarks"></a>备注

MapView 是[Windows：：基础：集合：：IMapView \<K，V>](/uwp/api/windows.foundation.collections.imapview-2)接口的具体 C++实现，该接口通过应用程序二进制接口 （ABI） 传递。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[地图视图：mapView](#ctor)|初始化 MapView 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[地图视图：第一](#first)|返回初始化为映射视图中第一个元素的迭代器。|
|[地图视图：：有键](#haskey)|确定当前 MapView 中是否包含指定键。|
|[地图视图：：查找](#lookup)|检索当前 MapView 对象中指定键处的元素。|
|[MapView::Size](#size)|返回当前 MapView 对象中的元素数目。|
|[地图视图：拆分](#split)|将原始 MapView 对象拆分成两个 MapView 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`MapView`

### <a name="requirements"></a>要求

**标题：** 集合.h

**命名空间：** Platform::Collections

## <a name="mapviewfirst-method"></a><a name="first"></a>地图视图：第一种方法

返回指定映射视图中第一个元素的迭代器。

### <a name="syntax"></a>语法

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>返回值

指定映射视图中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存 First（） 返回的迭代器的一个方便方法是将返回值分配给使用**自动**类型扣减关键字声明的变量。 例如，`auto x = myMapView->First();` 。

## <a name="mapviewhaskey-method"></a><a name="haskey"></a>地图视图：：有键方法

确定当前 MapView 中是否包含指定键。

### <a name="syntax"></a>语法

```

bool HasKey(K key);
```

### <a name="parameters"></a>参数

*键*<br/>
用于定位 MapView 元素的键。 *键*的类型是类型名称*K*。

### <a name="return-value"></a>返回值

如果找到密钥，**则为 true;** 否则，**假**。

## <a name="mapviewlookup-method"></a><a name="lookup"></a>地图视图：：查找方法

检索与类型 K 的指定键关联的类型 V 的值。

### <a name="syntax"></a>语法

```
V Lookup(K key);
```

### <a name="parameters"></a>参数

*键*<br/>
用于定位 MapView 中的元素的键。 的类型`key`是类型名称*K*。

### <a name="return-value"></a>返回值

与 `key` 配对的值。 返回值的类型为类型名称*V*。

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a>地图视图：mapView 构造函数

初始化 MapView 类的新实例。

### <a name="syntax"></a>语法

```cpp
explicit MapView(const C& comp = C());

explicit MapView(const ::std::map<K, V, C>& m);

explicit MapView(std::map<K, V, C>&& m);

template <typename InIt> MapView(
    InIt first,
    InIt last,
    const C& comp = C());

MapView(
    ::std::initializer_list<std::pair<const K, V>> il,
    const C& comp = C());
```

### <a name="parameters"></a>参数

*Init*<br/>
当前 MapView 的类型名称。

*Comp*<br/>
可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序的函数对象。

*米*<br/>
对 用于初始化当前 MapView`map Class`的 引用或[Lvalue 和 Rvalue。](../cpp/lvalues-and-rvalues-visual-cpp.md)

*第一*<br/>
用于初始化当前 MapView 的一系列元素中的第一个元素的输入迭代器。

*最后*<br/>
用于初始化当前 MapView 的一系列元素之后的第一个元素的输入迭代器。

*I l*<br/>
[std：：initializer_list<下：:p空气\<K，V>>](../standard-library/initializer-list-class.md)其元素将插入MapView。

## <a name="mapviewsize-method"></a><a name="size"></a>地图视图：大小方法

返回当前 MapView 对象中的元素数目。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 MapView 中的元素数目。

## <a name="mapviewsplit-method"></a><a name="split"></a>映射视图：：拆分方法

将当前 MapView 对象分成两个 MapView 对象。 此方法为非操作性的。

### <a name="syntax"></a>语法

```cpp
void Split(
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * firstPartition,
   Windows::Foundation::Collections::IMapView<
                         K, V>^ * secondPartition);
```

### <a name="parameters"></a>参数

*第一个分区*<br/>
原始 MapView 对象的第一部分。

*第二个分区*<br/>
原始 MapView 对象的第二部分。

### <a name="remarks"></a>备注

此方法为非操作性的，它不执行任何操作。

## <a name="see-also"></a>请参阅

[平台命名空间](platform-namespace-c-cx.md)
