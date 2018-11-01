---
title: unorm 类
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: b485d5efbfbcedbb1e11a3e212465340f0413ee4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491554"
---
# <a name="unorm-class"></a>unorm 类

表示 unorm 数字。 每个元素是一个浮点数，范围内的 [0.0f，1.0f]。

## <a name="syntax"></a>语法

```
class unorm;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[unorm 构造函数](#ctor)|已重载。 默认构造函数。 初始化为 0.0f。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|unorm::operator--||
|unorm::operator float|转换运算符。 将 unorm 数字转换为浮点值。|
|unorm::operator*=||
|unorm::operator/=||
|unorm::operator++||
|unorm::operator+=||
|unorm::operator=||
|unorm::operator-=||

## <a name="inheritance-hierarchy"></a>继承层次结构

`unorm`

## <a name="requirements"></a>要求

**标头：** amp_short_vectors.h

**Namespace:** concurrency:: graphics

##  <a name="ctor"></a> unorm

默认构造函数。 初始化为 0.0f。

```
unorm(
    void) restrict(amp,
    cpu);

explicit unorm(
    float _V) restrict(amp,
    cpu);

explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

explicit unorm(
    int _V) restrict(amp,
    cpu);

explicit unorm(
    double _V) restrict(amp,
    cpu);

unorm(
    const unorm& _Other) restrict(amp,
    cpu);

inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>参数

*（_V)*<br/>
用来初始化的值。

*_Other*<br/>
用于初始化的标准对象。

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
