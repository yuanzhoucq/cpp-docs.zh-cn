---
title: tiled_index 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f266efa2fb6de580bc1af04bdee6f80e2244fa23
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070044"
---
# <a name="tiledindex-class"></a>tiled_index 类

提供的索引[tiled_extent](tiled-extent-class.md)对象。 该类具有访问相对于本地平铺原点和相对于全局原点的元素的属性。 有关平铺空间的详细信息，请参阅[使用磁贴](../../../parallel/amp/using-tiles.md)。

## <a name="syntax"></a>语法

```
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

#### <a name="parameters"></a>参数

*_Dim0*<br/>
最高有效位维的长度。

*_Dim1*<br/>
下一步接近最高有效位维的长度。

*_Dim2*<br/>
最低有效位维的长度。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[tiled_index 构造函数](#ctor)|初始化 `tile_index` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|返回[程度](extent-class.md)对象，它具有的值`tiled_index`模板自变量`_Dim0`， `_Dim1`，并`_Dim2`。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[barrier 常量](#tiled_index__barrier)|存储[tile_barrier](tile-barrier-class.md)对象，表示当前线程的平铺屏障。|
|||
|[全局常量](#tiled_index__global)|存储[索引](index-class.md)表示网格对象中的全局索引的级别 1、 2 或 3 的对象。|
|[局部常量](#tiled_index__local)|存储`index`对象的当前磁贴中的索引，级别 1、 2 或 3，表示相对[tiled_extent](tiled-extent-class.md)对象。|
|[rank 常量](#tiled_index__rank)|将存储的秩`tiled_index`对象。|
|[tile 常量](#tiled_index__tile)|存储`index`对象的秩为 1、 2 或 3 表示当前 tile 的坐标`tiled_extent`对象。|
|[tile_dim0 常量](#tiled_index__tile_dim0)|存储最高有效位维的长度。|
|[tile_dim1 常量](#tiled_index__tile_dim1)|存储的下一步接近最高有效位维的长度。|
|[tile_dim2 常量](#tiled_index__tile_dim2)|存储最低有效位维的长度。|
|[tile_origin 常量](#tiled_index__tile_origin)|存储`index`对象当前平铺原点的级别 1、 2 或 3 表示全局坐标`tiled_extent`对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[tile_extent](#tile_extent)|获取[程度](extent-class.md)对象，它具有的值`tiled_index`模板自变量`tiled_index`模板自变量`_Dim0`， `_Dim1`，和`_Dim2`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="tiled_index__ctor"></a>  tiled_index 构造函数

初始化 `tiled_index` 类的新实例。

## <a name="syntax"></a>语法

```
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

#### <a name="parameters"></a>参数

*_Global*<br/>
全局[索引](index-class.md)构造的`tiled_index`。

*（_l)*<br/>
本地[索引](index-class.md)的构造 `tiled_index`

*_Tile*<br/>
该磁贴[索引](index-class.md)的构造 `tiled_index`

*_Tile_origin*<br/>
平铺原点[索引](index-class.md)的构造 `tiled_index`

*_Barrier*<br/>
[Tile_barrier](tile-barrier-class.md)对象的构造`tiled_index`。

*_Other*<br/>
`tile_index`对象要复制到构造`tiled_index`。

## <a name="overloads"></a>Overloads

|||
|-|-|
|name|描述|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|初始化的新实例`tile_index`类从索引中全局坐标的平铺和本地坐标中的磁贴中的相对位置。 `_Global`和`_Tile_origin`参数可计算。|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|初始化的新实例`tile_index`类的复制指定`tiled_index`对象。|

## <a name="tiled_index__get_tile_extent"></a>  get_tile_extent

返回[程度](extent-class.md)对象，它具有的值`tiled_index`模板自变量`_Dim0`， `_Dim1`，并`_Dim2`。

## <a name="syntax"></a>语法

```
extent<rank> get_tile_extent()restrict(amp,cpu);
```

## <a name="return-value"></a>返回值

一个 `extent` 对象，具有 `tiled_index` 模板自变量 `_Dim0`、`_Dim1` 和 `_Dim2` 的值。

## <a name="tiled_index__barrier"></a>  barrier

存储[tile_barrier](tile-barrier-class.md)对象，表示当前线程的平铺屏障。

## <a name="syntax"></a>语法

```
const tile_barrier barrier;
```

## <a name="tiled_index__global"></a>  全局

存储[索引](index-class.md)表示对象的全局索引的级别 1、 2 或 3 的对象。

## <a name="syntax"></a>语法

```
const index<rank> global;
```

## <a name="tiled_index__local"></a>  本地

存储[索引](index-class.md)对象的当前磁贴中的索引，级别 1、 2 或 3，表示相对[tiled_extent](tiled-extent-class.md)对象。

## <a name="syntax"></a>语法

```
const index<rank> local;
```

## <a name="tiled_index__rank"></a>  排名

将存储的秩`tiled_index`对象。

## <a name="syntax"></a>语法

```
static const int rank = _Rank;
```

## <a name="tiled_index__tile"></a>  磁贴

存储[索引](index-class.md)对象的秩为 1、 2 或 3 表示当前 tile 的坐标[tiled_extent](tiled-extent-class.md)对象。

## <a name="syntax"></a>语法

```
const index<rank> tile;
```

## <a name="tiled_index__tile_dim0"></a>  tile_dim0

存储最高有效位维的长度。

## <a name="syntax"></a>语法

```
static const int tile_dim0 = _Dim0;
```

## <a name="tiled_index__tile_dim1"></a>  tile_dim1

存储的下一步接近最高有效位维的长度。

## <a name="syntax"></a>语法

```
static const int tile_dim1 = _Dim1;
```

## <a name="tiled_index__tile_dim2"></a>  tile_dim2

存储最低有效位维的长度。

## <a name="syntax"></a>语法

```
static const int tile_dim2 = _Dim2;
```

## <a name="tiled_index__tile_origin"></a>  tile_origin

存储[索引](index-class.md)对象当前平铺中的起始级别 1、 2 或 3 表示全局坐标[tiled_extent](tiled-extent-class.md)对象。

## <a name="syntax"></a>语法

```
const index<rank> tile_origin
```

## <a name="tile_extent"></a>  tile_extent
  获取[程度](extent-class.md)对象，它具有的值`tiled_index`模板自变量`tiled_index`模板自变量`_Dim0`， `_Dim1`，和`_Dim2`。

## <a name="syntax"></a>语法

```
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
