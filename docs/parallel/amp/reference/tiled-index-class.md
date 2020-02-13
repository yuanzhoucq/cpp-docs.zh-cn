---
title: tiled_index 类
ms.date: 03/27/2019
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: eda01667a6b239284c682ba6ae3f9b857c713447
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142425"
---
# <a name="tiled_index-class"></a>tiled_index 类

为[tiled_extent](tiled-extent-class.md)对象提供索引。 此类具有一些属性，可访问相对于本地平铺原点和相对于全局原点的元素。 有关平铺空间的详细信息，请参阅[使用磁贴](../../../parallel/amp/using-tiles.md)。

## <a name="syntax"></a>语法

```cpp
template <
    int _Dim0,
    int _Dim1 = 0,
    int _Dim2 = 0
>
class tiled_index : public _Tiled_index_base<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;

template <
    int _Dim0
>
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;
```

### <a name="parameters"></a>参数

*_Dim0*<br/>
最有效维度的长度。

*_Dim1*<br/>
最后面的重要维度的长度。

*_Dim2*<br/>
最小的有效维度的长度。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[tiled_index 构造函数](#ctor)|初始化 `tile_index` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|返回一个[片区](extent-class.md)对象，该对象具有 `_Dim0`、`_Dim1`和 `_Dim2``tiled_index` 模板参数的值。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[关卡常量](#tiled_index__barrier)|存储一个表示当前线程磁贴中的关卡的[tile_barrier](tile-barrier-class.md)对象。|
|||
|[全局常量](#tiled_index__global)|存储一个秩为1、2或3的[index](index-class.md)对象，该对象表示网格对象中的全局索引。|
|[局部常量](#tiled_index__local)|存储一个秩为1、2或3的 `index` 对象，该对象表示[tiled_extent](tiled-extent-class.md)对象的当前平铺中的相对索引。|
|[rank 常量](#tiled_index__rank)|存储 `tiled_index` 对象的排名。|
|[平铺常量](#tiled_index__tile)|存储一个秩为1、2或3的 `index` 对象，该对象表示 `tiled_extent` 对象的当前平铺的坐标。|
|[tile_dim0 常量](#tiled_index__tile_dim0)|存储最高有效维度的长度。|
|[tile_dim1 常量](#tiled_index__tile_dim1)|存储下一个到最重要的维度的长度。|
|[tile_dim2 常量](#tiled_index__tile_dim2)|存储最不重要维度的长度。|
|[tile_origin 常量](#tiled_index__tile_origin)|存储一个秩为1、2或3的 `index` 对象，该对象表示 `tiled_extent` 对象中当前磁贴原点的全局坐标。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[tile_extent](#tile_extent)|获取一个[区](extent-class.md)对象，该对象具有 `tiled_index` 模板参数 `tiled_index` 模板参数的值 `_Dim0`、`_Dim1`和 `_Dim2`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="ctor"></a>tiled_index 构造函数

初始化 `tiled_index` 类的新实例。

### <a name="syntax"></a>语法

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Global*<br/>
构造的 `tiled_index`的全局[索引](index-class.md)。

*_Local*<br/>
构造的 `tiled_index` 的本地[索引](index-class.md)

*_Tile*<br/>
构造的 `tiled_index` 的平铺[索引](index-class.md)

*_Tile_origin*<br/>
构造的 `tiled_index` 的磁贴源[索引](index-class.md)

*_Barrier*<br/>
构造的 `tiled_index`的[tile_barrier](tile-barrier-class.md)对象。

*_Other*<br/>
要复制到构造的 `tiled_index`的 `tile_index` 对象。

### <a name="overloads"></a>Overloads

|||
|-|-|
|名称|说明|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|从全局坐标中磁贴的索引和以本地坐标表示的磁贴中的相对位置，初始化 `tile_index` 类的新实例。 计算 `_Global` 和 `_Tile_origin` 参数。|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|通过复制指定的 `tiled_index` 对象，初始化 `tile_index` 类的新实例。|

## <a name="tiled_index__get_tile_extent"></a>get_tile_extent

返回一个[片区](extent-class.md)对象，该对象具有 `_Dim0`、`_Dim1`和 `_Dim2``tiled_index` 模板参数的值。

### <a name="syntax"></a>语法

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

一个 `extent` 对象，具有 `tiled_index` 模板自变量 `_Dim0`、`_Dim1` 和 `_Dim2` 的值。

## <a name="tiled_index__barrier"></a>关卡

存储一个表示当前线程磁贴中的关卡的[tile_barrier](tile-barrier-class.md)对象。

### <a name="syntax"></a>语法

```cpp
const tile_barrier barrier;
```

## <a name="tiled_index__global"></a>全局

存储一个秩为1、2或3的[index](index-class.md)对象，该对象表示对象的全局索引。

### <a name="syntax"></a>语法

```cpp
const index<rank> global;
```

## <a name="tiled_index__local"></a>地方

存储一个秩为1、2或3的[index](index-class.md)对象，该对象表示[tiled_extent](tiled-extent-class.md)对象的当前磁贴中的相对索引。

### <a name="syntax"></a>语法

```cpp
const index<rank> local;
```

## <a name="tiled_index__rank"></a>级别

存储 `tiled_index` 对象的排名。

### <a name="syntax"></a>语法

```cpp
static const int rank = _Rank;
```

## <a name="tiled_index__tile"></a>磁

存储一个秩为1、2或3的[index](index-class.md)对象，该对象表示[tiled_extent](tiled-extent-class.md)对象的当前平铺的坐标。

### <a name="syntax"></a>语法

```cpp
const index<rank> tile;
```

## <a name="tiled_index__tile_dim0"></a>tile_dim0

存储最高有效维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tiled_index__tile_dim1"></a>tile_dim1

存储下一个到最重要的维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tiled_index__tile_dim2"></a>tile_dim2

存储最不重要维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tiled_index__tile_origin"></a>tile_origin

存储一个秩为1、2或3的[index](index-class.md)对象，该对象表示[tiled_extent](tiled-extent-class.md)对象内当前磁贴原点的全局坐标。

### <a name="syntax"></a>语法

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a>tile_extent

获取一个[区](extent-class.md)对象，该对象具有 `tiled_index` 模板参数 `tiled_index` 模板参数的值 `_Dim0`、`_Dim1`和 `_Dim2`。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
