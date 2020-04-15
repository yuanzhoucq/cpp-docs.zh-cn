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
ms.openlocfilehash: 46a6b3548526f0917c4e022a12bf859242e70b20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375472"
---
# <a name="tiled_index-class"></a>tiled_index 类

提供索引到[tiled_extent](tiled-extent-class.md)对象。 此类具有访问相对于局部磁贴源和全局源的元素的属性。 有关平铺空间的详细信息，请参阅[使用磁贴](../../../parallel/amp/using-tiles.md)。

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
最重要的维度的长度。

*_Dim1*<br/>
第二个最重要的维度的长度。

*_Dim2*<br/>
最小尺寸的长度。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[tiled_index构造函数](#ctor)|初始化 `tile_index` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|返回具有`tiled_index`模板`_Dim0`参数值的[扩展区](extent-class.md)对象`_Dim1`， 和`_Dim2`。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[屏障常数](#tiled_index__barrier)|存储表示当前线程磁贴中障碍[tile_barrier](tile-barrier-class.md)对象。|
|||
|[全局常数](#tiled_index__global)|存储表示网格对象中全局索引的排名为 1、2 或 3 的[索引](index-class.md)对象。|
|[local 常量](#tiled_index__local)|存储排名`index`1、2 或 3 的对象，该对象表示[tiled_extent](tiled-extent-class.md)对象的当前磁贴中的相对索引。|
|[排名 常量](#tiled_index__rank)|存储`tiled_index`对象的排名。|
|[磁贴常数](#tiled_index__tile)|存储表示`index``tiled_extent`对象当前磁贴坐标的排名为 1、2 或 3 的对象。|
|[tile_dim0常量](#tiled_index__tile_dim0)|存储最重要的维度的长度。|
|[tile_dim1常量](#tiled_index__tile_dim1)|存储第二个最重要的维度的长度。|
|[tile_dim2常量](#tiled_index__tile_dim2)|存储最小尺寸的长度。|
|[tile_origin常量](#tiled_index__tile_origin)|存储排名`index`1、2 或 3 的对象，该对象表示`tiled_extent`对象中当前磁贴的原点的全局坐标。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[tile_extent](#tile_extent)|获取具有`tiled_index`模板`tiled_index`参数模板参数`_Dim0`的值的[扩展区](extent-class.md)对象`_Dim1`， 和`_Dim2`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="tiled_index-constructor"></a><a name="ctor"></a>tiled_index构造函数

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
构造`tiled_index`的全局[索引](index-class.md)。

*_Local*<br/>
构造的局部[索引](index-class.md)`tiled_index`

*_Tile*<br/>
构造的磁贴[索引](index-class.md)`tiled_index`

*_Tile_origin*<br/>
构造的切片原点[索引](index-class.md)`tiled_index`

*_Barrier*<br/>
构造的[tile_barrier](tile-barrier-class.md)对象`tiled_index`。

*_Other*<br/>
要`tile_index`复制到构造`tiled_index`的对象。

### <a name="overloads"></a>Overloads

|||
|-|-|
|名称|说明|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|从全局坐标中的磁贴索引和局部`tile_index`坐标中磁贴的相对位置初始化类的新实例。 计算`_Global``_Tile_origin`和 参数。|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|通过复制指定的`tile_index``tiled_index`对象来初始化类的新实例。|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent

返回具有`tiled_index`模板`_Dim0`参数值的[扩展区](extent-class.md)对象`_Dim1`， 和`_Dim2`。

### <a name="syntax"></a>语法

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

一个 `extent` 对象，具有 `tiled_index` 模板自变量 `_Dim0`、`_Dim1` 和 `_Dim2` 的值。

## <a name="barrier"></a><a name="tiled_index__barrier"></a>障碍

存储表示当前线程磁贴中障碍[tile_barrier](tile-barrier-class.md)对象。

### <a name="syntax"></a>语法

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a>全球

存储表示对象的全局索引的排名 1、2 或 3 的[索引](index-class.md)对象。

### <a name="syntax"></a>语法

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a>当地

存储排名 1、2 或 3 的[索引](index-class.md)对象，该对象表示[tiled_extent](tiled-extent-class.md)对象的当前磁贴中的相对索引。

### <a name="syntax"></a>语法

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a>排名

存储`tiled_index`对象的排名。

### <a name="syntax"></a>语法

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a>瓦

存储表示[tiled_extent](tiled-extent-class.md)对象的当前磁贴的坐标的排名 1、2 或 3 的[索引](index-class.md)对象。

### <a name="syntax"></a>语法

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0

存储最重要的维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1

存储第二个最重要的维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2

存储最小尺寸的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a>tile_origin

存储排名 1、2 或 3 的索引对象，该[索引](index-class.md)对象表示[tiled_extent](tiled-extent-class.md)对象中当前磁贴的原点的全局坐标。

### <a name="syntax"></a>语法

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a>tile_extent

获取具有`tiled_index`模板`tiled_index`参数模板参数`_Dim0`的值的[扩展区](extent-class.md)对象`_Dim1`， 和`_Dim2`。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
