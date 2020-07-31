---
title: Concurrency::fast_math 命名空间
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 6ed8dcfa2faff49e8811769b76aad9df15b2fe7b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226745"
---
# <a name="concurrencyfast_math-namespace"></a>Concurrency::fast_math 命名空间

命名空间中的函数 `fast_math` 的准确性较低，仅支持单精度（ **`float`** ），并调用 DirectX 内部函数。 每个函数都有两个版本，例如 `cos` 和 `cosf` 。 这两个版本都采用并返回 **`float`** ，但每个版本都调用相同的 DirectX 内部函数。

## <a name="syntax"></a>语法

```cpp
namespace fast_math;
```

## <a name="members"></a>成员

### <a name="functions"></a>函数

|名称|说明|
|----------|-----------------|
|[缆](concurrency-fast-math-namespace-functions.md#cos)|计算参数的反余弦|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|计算参数的反余弦|
|[asin](concurrency-fast-math-namespace-functions.md#asin)|计算参数的反正弦|
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|计算参数的反正弦|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|计算参数的反正切值|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|计算 _Y/_X 的反正切值|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|计算 _Y/_X 的反正切值|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|计算参数的反正切值|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|计算参数的上限|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|计算参数的上限|
|[缆](concurrency-fast-math-namespace-functions.md#cos)|计算参数的余弦值|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|计算参数的余弦值|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|计算参数的双曲余弦值|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|计算参数的双曲余弦值|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|计算自变量的以 e 为底的指数|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|计算参数的以2为底的指数|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|计算参数的以2为底的指数|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|计算自变量的以 e 为底的指数|
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|返回参数的绝对值。|
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|返回参数的绝对值。|
|[突破](concurrency-fast-math-namespace-functions.md#floor)|计算参数的下限|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|计算参数的下限|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|确定参数的最大数值|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|确定参数的最大数值|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|确定参数的最小数值|
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|确定参数的最小数值|
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|计算 _X/_Y 的浮点余数|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|计算 _X/_Y 的浮点余数|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|获取 _X 的尾数和指数|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|获取 _X 的尾数和指数|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|确定参数是否具有有限值|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|确定参数是否为无穷|
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|确定参数是否为 NaN|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|从尾数和指数计算实数|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|从尾数和指数计算实数|
|[日志](concurrency-fast-math-namespace-functions.md#log)|计算自变量的以 e 为底的对数|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|计算自变量的以10为底的对数|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|计算自变量的以10为底的对数|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|计算参数的以2为底的对数|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|计算参数的以2为底的对数|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|计算自变量的以 e 为底的对数|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|将 _X 拆分为小数部分和整数部分。|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|将 _X 拆分为小数部分和整数部分。|
|[pow](concurrency-fast-math-namespace-functions.md#pow)|计算 _X 的次幂 _Y|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|计算 _X 的次幂 _Y|
|[圆满](concurrency-fast-math-namespace-functions.md#round)|将 _X 舍入到最接近的整数|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|将 _X 舍入到最接近的整数|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|返回参数平方根的倒数|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|返回参数平方根的倒数|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|返回参数的符号|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|返回参数的符号|
|[sin](concurrency-fast-math-namespace-functions.md#sin)|计算参数的正弦值|
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|计算 _X 的正弦值和余弦值|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|计算 _X 的正弦值和余弦值|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|计算参数的正弦值|
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|计算参数的双曲正弦值|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|计算参数的双曲正弦值|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|计算参数的平方根|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|计算参数的平方根|
|[tan](concurrency-fast-math-namespace-functions.md#tan)|计算参数的正切值|
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|计算参数的正切值|
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|计算参数的双曲正切值|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|计算参数的双曲正切值|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|将参数截断为整数组件|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|将参数截断为整数组件|

## <a name="requirements"></a>要求

**标头：** amp_math。h

**命名空间：** Concurrency：： fast_math

## <a name="see-also"></a>另请参阅

[并发命名空间（C++ AMP）](concurrency-namespace-cpp-amp.md)
