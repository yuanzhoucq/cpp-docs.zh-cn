---
title: unorm_2 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator+=
- amp_short_vectors/Concurrency::graphics::unnorm_2::y
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::x
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator--
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator*=
- amp_short_vectors/Concurrency::graphics::unnorm_2::xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator=
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::rg
- amp_short_vectors/Concurrency::graphics::unorm_2
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-=
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator/=
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::gr
- amp_short_vectors/Concurrency::graphics::unnorm_2::r
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::g
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator++
dev_langs:
- C++
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3762218b6171ba26d637e209e818b703db9ee5ed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410320"
---
# <a name="unorm2-class"></a>unorm_2 类

表示两个无符号的常规数字的短矢量。

## <a name="syntax"></a>语法

```
class unorm_2;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[unorm_2 构造函数](#ctor)|已重载。 默认构造函数，初始化 0 的所有元素。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|unorm_2::get_x||
|unorm_2::get_xy||
|unorm_2::get_y||
|unorm_2::get_yx||
|unorm_2::ref_g||
|unorm_2::ref_r||
|unorm_2::ref_x||
|unorm_2::ref_y||
|unorm_2::set_x||
|unorm_2::set_xy||
|unorm_2::set_y||
|unorm_2::set_yx||

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|unorm_2::operator--||
|unorm_2::operator*=||
|unorm_2::operator/=||
|unorm_2::operator++||
|unorm_2::operator+=||
|unorm_2::operator=||
|unorm_2::operator-=||

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|unorm_2::size 常量||

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|unorm_2::g||
|unorm_2::gr||
|unorm_2::r||
|unorm_2::rg||
|unorm_2::x||
|unorm_2::xy||
|unorm_2::y||
|unorm_2::yx||

## <a name="inheritance-hierarchy"></a>继承层次结构

`unorm_2`

## <a name="requirements"></a>要求

**标头：** amp_short_vectors.h

**Namespace:** concurrency:: graphics

##  <a name="ctor"></a> unorm_2

默认构造函数，初始化 0 的所有元素。

```
unorm_2() restrict(amp,
    cpu);

unorm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

unorm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

unorm_2(
    unorm _V) restrict(amp,
    cpu);

explicit unorm_2(
    float _V) restrict(amp,
    cpu);

unorm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>参数

*_V0*<br/>
要初始化元素 0 的值。

*_V1*<br/>
要初始化元素 1 的值。

*（_V)*<br/>
用于初始化值。

*_Other*<br/>
用于初始化的对象。

##  <a name="unorm_2__size"></a> 大小

```
static const int size = 2;
```

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
