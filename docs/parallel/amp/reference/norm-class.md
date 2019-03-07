---
title: norm 类
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 56f879ef2fc0d3010ab4f64fedaf2570dac565d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272420"
---
# <a name="norm-class"></a>norm 类

表示标准数字。 每个元素是浮点数，范围内的 [-1.0 f、 1.0f]。

## <a name="syntax"></a>语法

```
class norm;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[norm 构造函数](#ctor)|已重载。 默认构造函数。 初始化为 0.0f。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|norm::operator-||
|norm::operator--||
|norm::operator float|转换运算符。 将标准数字转换为浮点值。|
|norm::operator*=||
|norm::operator/=||
|norm::operator++||
|norm::operator+=||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>继承层次结构

`norm`

## <a name="requirements"></a>要求

**标头：** amp_short_vectors.h

**命名空间：** Concurrency:: graphics

##  <a name="ctor"></a> norm

默认构造函数。 初始化为 0.0f。

```
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>参数

*_V*<br/>
用来初始化的值。

*_Other*<br/>
用于初始化的对象。

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
