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
ms.openlocfilehash: 6c50825cb3003c2b1b63a25419ca67742c92b52f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214992"
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

*温度*<br/>
键值对中键的类型。

*向量*<br/>
键值对中值的类型。

*C*<br/>
提供一个函数对象的类型，该对象可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序。 默认情况下， [std：： \<K> less](../standard-library/less-struct.md)。

### <a name="remarks"></a>备注

MapView 是跨应用程序二进制接口（ABI）传递的[Windows：： Foundation：： \<K,V> 集合：： IMapView](/uwp/api/windows.foundation.collections.imapview-2)接口的具体 c + + 实现。 有关更多信息，请参见 [集合 (C++/CX)](../cppcx/collections-c-cx.md)。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[MapView：： MapView](#ctor)|初始化 MapView 类的新实例。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[MapView：： First](#first)|返回初始化为映射视图中第一个元素的迭代器。|
|[MapView：： HasKey](#haskey)|确定当前 MapView 中是否包含指定键。|
|[MapView：： Lookup](#lookup)|检索当前 MapView 对象中指定键处的元素。|
|[MapView::Size](#size)|返回当前 MapView 对象中的元素数目。|
|[MapView：： Split](#split)|将原始 MapView 对象拆分成两个 MapView 对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`MapView`

### <a name="requirements"></a>要求

**标头：** 集合。h

**命名空间：** Platform::Collections

## <a name="mapviewfirst-method"></a><a name="first"></a>MapView：： First 方法

返回指定映射视图中第一个元素的迭代器。

### <a name="syntax"></a>语法

```
virtual Windows::Foundation::Collections::IIterator<
   Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>返回值

指定映射视图中第一个元素的迭代器。

### <a name="remarks"></a>备注

保存第一个（）返回的迭代器的一种简便方法是将返回值分配给使用 **`auto`** 类型推导关键字声明的变量。 例如，`auto x = myMapView->First();`。

## <a name="mapviewhaskey-method"></a><a name="haskey"></a>MapView：： HasKey 方法

确定当前 MapView 中是否包含指定键。

### <a name="syntax"></a>语法

```

bool HasKey(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位 MapView 元素的键。 *键*类型为 typename *K*。

### <a name="return-value"></a>返回值

**`true`** 如果找到该键，则为;否则为 **`false`** 。

## <a name="mapviewlookup-method"></a><a name="lookup"></a>MapView：： Lookup 方法

检索与类型 K 的指定键关联的类型 V 的值。

### <a name="syntax"></a>语法

```
V Lookup(K key);
```

### <a name="parameters"></a>参数

*key*<br/>
用于定位 MapView 中的元素的键。 的类型 `key` 为 Typename *K*。

### <a name="return-value"></a>返回值

与 `key` 配对的值。 返回值的类型为 typename *V*。

## <a name="mapviewmapview-constructor"></a><a name="ctor"></a>MapView：： MapView 构造函数

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

*InIt*<br/>
当前 MapView 的类型名称。

*comp*<br/>
可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序的函数对象。

*m*<br/>
用于初始化当前 MapView 的[左值和右](../cpp/lvalues-and-rvalues-visual-cpp.md)的引用 `map Class` 。

*first*<br/>
用于初始化当前 MapView 的一系列元素中的第一个元素的输入迭代器。

*last*<br/>
用于初始化当前 MapView 的一系列元素之后的第一个元素的输入迭代器。

*il*<br/>
[Std：： initializer_list<std \<K,V> > ：:p](../standard-library/initializer-list-class.md)要将其元素插入到 MapView 中的空气。

## <a name="mapviewsize-method"></a><a name="size"></a>MapView：： Size 方法

返回当前 MapView 对象中的元素数目。

### <a name="syntax"></a>语法

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>返回值

当前 MapView 中的元素数目。

## <a name="mapviewsplit-method"></a><a name="split"></a>MapView：： Split 方法

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

*firstPartition*<br/>
原始 MapView 对象的第一部分。

*secondPartition*<br/>
原始 MapView 对象的第二部分。

### <a name="remarks"></a>备注

此方法为非操作性的，它不执行任何操作。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)
