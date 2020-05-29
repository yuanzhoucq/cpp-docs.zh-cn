---
title: tiled_extent 类
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: ce2710da1a745efedcd6e9e524355eda41e26de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374713"
---
# <a name="tiled_extent-class"></a>tiled_extent 类

对象`tiled_extent`是一`extent`到三维的对象，将范围空间细分为一维、二维或三维切片。

## <a name="syntax"></a>语法

```cpp
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
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
|[tiled_extent构造函数](#ctor)|初始化 `tiled_extent` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|返回捕获`extent``tiled_extent`模板参数`_Dim0`的值的对象`_Dim1`， 和`_Dim2`。|
|[垫](#pad)|返回一个新`tiled_extent`对象，其扩展的扩展区可被切片尺寸均匀整除。|
|[截断](#truncate)|返回一个新`tiled_extent`对象，其范围向下调整，以被切片尺寸均匀整除。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[运算符*](#operator_eq)|将指定`tiled_index`对象的内容复制到此对象中。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[tile_dim0常量](#tile_dim0)|存储最重要的维度的长度。|
|[tile_dim1常量](#tile_dim1)|存储第二个最重要的维度的长度。|
|[tile_dim2常量](#tile_dim2)|存储最小尺寸的长度。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[tile_extent](#tile_extent)|获取捕获`extent``tiled_extent`模板参数`_Dim0`的值的对象`_Dim1`， 和`_Dim2`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`extent`

`tiled_extent`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="tiled_extent-constructor"></a><a name="ctor"> </a> tiled_extent构造函数

初始化 `tiled_extent` 类的新实例。

### <a name="syntax"></a>语法

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>参数

*_Other*<br/>
要`extent``tiled_extent`复制的对象。

## <a name="get_tile_extent"></a><a name="get_tile_extent"> </a> get_tile_extent

返回捕获`extent``tiled_extent`模板参数`_Dim0`的值的对象`_Dim1`， 和`_Dim2`。

### <a name="syntax"></a>语法

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

捕获`extent`此`tiled_extent`实例维度的对象。

## <a name="pad"></a><a name="pad"> </a>垫

返回一个新`tiled_extent`对象，其扩展的扩展区可被切片尺寸均匀整除。

### <a name="syntax"></a>语法

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>返回值

新`tiled_extent`对象，按值。

## <a name="truncate"></a><a name="truncate"> </a>截流

返回一个新`tiled_extent`对象，其范围向下调整，以被切片尺寸均匀整除。

### <a name="syntax"></a>语法

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>返回值

返回一个新`tiled_extent`对象，其范围向下调整，以被切片尺寸均匀整除。

## <a name="operator"></a><a name="operator_eq"> </a>运算符*

将指定`tiled_index`对象的内容复制到此对象中。

### <a name="syntax"></a>语法

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要`tiled_index`复制的对象。

### <a name="return-value"></a>返回值

对此`tiled_index`实例的引用。

## <a name="tile_dim0"></a><a name="tile_dim0"> </a> tile_dim0

存储最重要的维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"> </a> tile_dim1

存储第二个最重要的维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"> </a> tile_dim2

存储最小尺寸的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"> </a> tile_extent

获取捕获`extent``tiled_extent`模板参数`_Dim0`的值的对象`_Dim1`， 和`_Dim2`。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
