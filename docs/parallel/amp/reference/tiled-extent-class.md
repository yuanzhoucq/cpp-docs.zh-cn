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
ms.openlocfilehash: e2248c770c7eedde59d1cb592f7d5d7c1bfbde9a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126417"
---
# <a name="tiled_extent-class"></a>tiled_extent 类

`tiled_extent` 对象是一到三个维度的 `extent` 对象，它将范围空间细分为一维或三维平铺。

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
最有效维度的长度。

*_Dim1*<br/>
最后面的重要维度的长度。

*_Dim2*<br/>
最小的有效维度的长度。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[tiled_extent 构造函数](#ctor)|初始化 `tiled_extent` 类的新实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|返回一个 `extent` 对象，该对象捕获 `tiled_extent` 模板参数的值 `_Dim0`、`_Dim1`和 `_Dim2`。|
|[类似](#pad)|返回一个新的 `tiled_extent` 对象，其中的区向上调整，以使磁贴尺寸能够均匀地被调整。|
|[truncate](#truncate)|返回一个新的 `tiled_extent` 对象，其中的区向下调整以按平铺尺寸进行等距。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator=](#operator_eq)|将指定 `tiled_index` 对象的内容复制到此对象中。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[tile_dim0 常量](#tile_dim0)|存储最高有效维度的长度。|
|[tile_dim1 常量](#tile_dim1)|存储下一个到最重要的维度的长度。|
|[tile_dim2 常量](#tile_dim2)|存储最不重要维度的长度。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[tile_extent](#tile_extent)|获取一个 `extent` 对象，该对象捕获 `tiled_extent` 模板参数的值 `_Dim0`、`_Dim1`和 `_Dim2`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`extent`

`tiled_extent`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="ctor"></a> Tiled_extent 构造函数

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
要复制的 `extent` 或 `tiled_extent` 对象。

## <a name="get_tile_extent"></a> get_tile_extent

返回一个 `extent` 对象，该对象捕获 `tiled_extent` 模板参数的值 `_Dim0`、`_Dim1`和 `_Dim2`。

### <a name="syntax"></a>语法

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

捕获此 `tiled_extent` 实例的尺寸的 `extent` 对象。

## <a name="pad"></a>填充

返回一个新的 `tiled_extent` 对象，其中的区向上调整，以使磁贴尺寸能够均匀地被调整。

### <a name="syntax"></a>语法

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>返回值

新 `tiled_extent` 对象，按值。
## <a name="truncate"></a>截断

返回一个新的 `tiled_extent` 对象，其中的区向下调整以按平铺尺寸进行等距。

### <a name="syntax"></a>语法

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>返回值

返回一个新的 `tiled_extent` 对象，其中的区向下调整以按平铺尺寸进行等距。

## <a name="operator_eq"></a> operator =

将指定 `tiled_index` 对象的内容复制到此对象中。

### <a name="syntax"></a>语法

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从中进行复制的 `tiled_index` 对象。

### <a name="return-value"></a>返回值

对此 `tiled_index` 实例的引用。

## <a name="tile_dim0"></a> tile_dim0

存储最高有效维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a> tile_dim1

存储下一个到最重要的维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a> tile_dim2

存储最不重要维度的长度。

### <a name="syntax"></a>语法

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a> tile_extent
  获取一个 `extent` 对象，该对象捕获 `tiled_extent` 模板参数的值 `_Dim0`、`_Dim1`和 `_Dim2`。

### <a name="syntax"></a>语法

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
