---
title: Concurrency::fast_math 命名空间函数
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math::acos
- amp_math/Concurrency::fast_math::asin
- amp_math/Concurrency::fast_math::asinf
- amp_math/Concurrency::fast_math::atan2
- amp_math/Concurrency::fast_math::atan2f
- amp_math/Concurrency::fast_math::ceil
- amp_math/Concurrency::fast_math::ceilf
- amp_math/Concurrency::fast_math::cosf
- amp_math/Concurrency::fast_math::cosh
- amp_math/Concurrency::fast_math::exp
- amp_math/Concurrency::fast_math::exp2
- amp_math/Concurrency::fast_math::expf
- amp_math/Concurrency::fast_math::fabs
- amp_math/Concurrency::fast_math::floor
- amp_math/Concurrency::fast_math::floorf
- amp_math/Concurrency::fast_math::fmaxf
- amp_math/Concurrency::fast_math::fmin
- amp_math/Concurrency::fast_math::fmod
- amp_math/Concurrency::fast_math::fmodf
- amp_math/Concurrency::fast_math::frexpf
- amp_math/Concurrency::fast_math::isfinite
- amp_math/Concurrency::fast_math::isnan
- amp_math/Concurrency::fast_math::ldexp
- amp_math/Concurrency::fast_math::log
- amp_math/Concurrency::fast_math::log10
- amp_math/Concurrency::fast_math::log2
- amp_math/Concurrency::fast_math::log2f
- amp_math/Concurrency::fast_math::modf
- amp_math/Concurrency::fast_math::modff
- amp_math/Concurrency::fast_math::powf
- amp_math/Concurrency::fast_math::round
- amp_math/Concurrency::fast_math::rsqrt
- amp_math/Concurrency::fast_math::rsqrtf
- amp_math/Concurrency::fast_math::signbitf
- amp_math/Concurrency::fast_math::sin
- amp_math/Concurrency::fast_math::sincosf
- amp_math/Concurrency::fast_math::sinf
- amp_math/Concurrency::fast_math::sinhf
- amp_math/Concurrency::fast_math::sqrt
- amp_math/Concurrency::fast_math::tan
- amp_math/Concurrency::fast_math::tanf
- amp_math/Concurrency::fast_math::tanhf
- amp_math/Concurrency::fast_math::trunc
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
ms.openlocfilehash: cd0882b072cfe26cd83e63024ae6837dc962ebf9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376399"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math 命名空间函数

||||
|-|-|-|
|[阿科斯](#acos)|[acosf](#acosf)|[阿辛](#asin)|
|[asinf](#asinf)|[阿坦](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[塞伊尔](#ceil)|
|[ceilf](#ceilf)|[因为](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[地板](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[弗莫德](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[弗雷克斯普夫](#frexpf)|
|[是有限的](#isfinite)|[是因夫](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[尔德克斯普夫](#ldexpf)|[日志](#log)|
|[日志10](#log10)|[log10f](#log10f)|[日志2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[战俘](#pow)|[powf](#powf)|
|[轮](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[符号比夫](#signbitf)|
|[罪](#sin)|[辛科斯](#sincos)|[辛科斯夫](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[潭](#tan)|
|[tanf](#tanf)|[坦赫](#tanh)|[tanhf](#tanhf)|
|[特鲁恩](#trunc)|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>阿科斯

计算参数的弧形

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反余弦值

## <a name="acosf"></a><a name="acosf"></a>阿科斯夫

计算参数的弧形

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反余弦值

## <a name="asin"></a><a name="asin"></a>阿辛

计算参数的弧形

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正弦值

## <a name="asinf"></a><a name="asinf"></a>阿辛夫

计算参数的弧形

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正弦值

## <a name="atan"></a><a name="atan"></a>阿坦

计算参数的反正切值

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正切值

## <a name="atan2"></a><a name="atan2"></a>阿坦2

计算_Y/_X的弧形

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_Y*<br/>
浮点值

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _Y/_X 的反正切值

## <a name="atan2f"></a><a name="atan2f"></a>阿坦2f

计算_Y/_X的弧形

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_Y*<br/>
浮点值

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _Y/_X 的反正切值

## <a name="atanf"></a><a name="atanf"></a>阿坦夫

计算参数的反正切值

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正切值

## <a name="ceil"></a><a name="ceil"></a>塞伊尔

计算参数的上限

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的上限

## <a name="ceilf"></a><a name="ceilf"></a>切尔夫

计算参数的上限

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的上限

## <a name="cosf"></a><a name="cosf"></a>科斯夫

计算参数的余弦值

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的余弦值

## <a name="coshf"></a><a name="coshf"></a>科斯夫

计算参数的双曲性抛物值

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反双曲余弦值

## <a name="cos"></a><a name="cos"></a>因为

计算参数的余弦值

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的余弦值

## <a name="cosh"></a><a name="cosh"></a>科什

计算参数的双曲性抛物值

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反双曲余弦值

## <a name="exp"></a><a name="exp"></a>exp

计算参数的基-e 指数

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的指数

## <a name="exp2"></a><a name="exp2"></a>exp2

计算参数的基-2 指数

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 2 为底的指数

## <a name="exp2f"></a><a name="exp2f"></a>exp2f

计算参数的基-2 指数

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 2 为底的指数

## <a name="expf"></a><a name="expf"></a>expf

计算参数的基-e 指数

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的指数

## <a name="fabs"></a><a name="fabs"></a>晶圆厂

返回参数的绝对值

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的绝对值

## <a name="fabsf"></a><a name="fabsf"></a>法布斯夫

返回参数的绝对值

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的绝对值

## <a name="floor"></a><a name="floor"></a>地板

计算参数的楼层

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的下限

## <a name="floorf"></a><a name="floorf"></a>地板

计算参数的楼层

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的下限

## <a name="fmax"></a><a name="fmax"></a>fmax

确定参数的最大数值

```cpp
inline float max(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的最大数值

## <a name="fmaxf"></a><a name="fmaxf"></a>fmaxf

确定参数的最大数值

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的最大数值

## <a name="fmin"></a><a name="fmin"></a>fmin

确定参数的最小数值

```cpp
inline float min(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的最小数值

## <a name="fminf"></a><a name="fminf"></a>fminf

确定参数的最小数值

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的最小数值

## <a name="fmod"></a><a name="fmod"></a>弗莫德

计算_X/_Y的浮点余数

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X/_Y 的浮点余数

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

计算 _X/_Y 的浮点余数。

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X/_Y 的浮点余数

## <a name="frexp"></a><a name="frexp"></a>弗雷费浦

获取_X的曼蒂萨和指数

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Exp*<br/>
以浮点值形式返回 _X 的整数指数。

### <a name="return-value"></a>返回值

返回尾数 _X

## <a name="frexpf"></a><a name="frexpf"></a>弗雷克斯普夫

获取_X的曼蒂萨和指数

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Exp*<br/>
以浮点值形式返回 _X 的整数指数。

### <a name="return-value"></a>返回值

返回尾数 _X

## <a name="isfinite"></a><a name="isfinite"></a>是有限的

确定参数是否具有有限值

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有有限值时，返回一个非零值

## <a name="isinf"></a><a name="isinf"></a>是因夫

确定参数是否为无穷大

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有无限值时，返回一个非零值

## <a name="isnan"></a><a name="isnan"></a>isnan

确定参数是否为 NaN

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有 NaN 值时，返回一个非零值

## <a name="ldexp"></a><a name="ldexp"></a>尔德莫

计算来自曼蒂萨和指数的实数

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值，尾数

*_Exp*<br/>
整数指数

### <a name="return-value"></a>返回值

返回_X \* 2+_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>尔德克斯普夫

计算来自曼蒂萨和指数的实数

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值，尾数

*_Exp*<br/>
整数指数

### <a name="return-value"></a>返回值

返回_X \* 2+_Exp

## <a name="log"></a><a name="log"></a>日志

计算参数的基数-e对数

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的对数

## <a name="log10"></a><a name="log10"></a>日志10

计算参数的基数-10对数

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

## <a name="log10f"></a><a name="log10f"></a>日志10f

计算参数的基数-10对数

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

## <a name="log2"></a><a name="log2"></a>日志2

计算参数的基 2 对数

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的基 2 对数

## <a name="log2f"></a><a name="log2f"></a>日志2f

计算参数的基 2 对数

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

## <a name="logf"></a><a name="logf"></a>logf

计算参数的基数-e对数

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的对数

## <a name="modf"></a><a name="modf"></a>modf

将_X拆分为小数和整数零件。

```cpp
inline float modf(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Ip*<br/>
接收值的整数部分

### <a name="return-value"></a>返回值

返回 _X 的有符号小数部分。

## <a name="modff"></a><a name="modff"></a>莫德夫

将_X拆分为小数和整数零件。

```cpp
inline float modff(
    float _X,
    float* _Ip) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Ip*<br/>
接收值的整数部分

### <a name="return-value"></a>返回值

返回 _X 的有符号小数部分。

## <a name="pow"></a><a name="pow"></a>战俘

计算_X提升到_Y功率

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值，底数

*_Y*<br/>
浮点值，指数

### <a name="return-value"></a>返回值

返回_X的值，以_Y

## <a name="powf"></a><a name="powf"></a>波夫

计算_X提升到_Y功率

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值，底数

*_Y*<br/>
浮点值，指数

### <a name="return-value"></a>返回值

## <a name="round"></a><a name="round"></a>轮

舍_X到最接近的整数

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回最接近 _X 的整数

## <a name="roundf"></a><a name="roundf"></a>圆夫

舍_X到最接近的整数

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回最接近 _X 的整数

## <a name="rsqrt"></a><a name="rsqrt"></a>rsqrt

返回参数的平方根的对等项

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的平方根的对等项

## <a name="rsqrtf"></a><a name="rsqrtf"></a>rsqrtf

返回参数的平方根的对等项

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的平方根的对等项

## <a name="signbit"></a><a name="signbit"></a>符号位

确定 _X 的符号是否为负号

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当 _X 的符号为负号时，返回一个非零值

## <a name="signbitf"></a><a name="signbitf"></a>符号比夫

确定 _X 的符号是否为负号

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当 _X 的符号为负号时，返回一个非零值

## <a name="sin"></a><a name="sin"></a>罪

计算参数的子值

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正弦值

## <a name="sinf"></a><a name="sinf"></a>辛夫

计算参数的子值

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正弦值

## <a name="sincos"></a><a name="sincos"></a>辛科斯

计算_X的子值和可次值

```cpp
inline void sincos(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_S*<br/>
返回 _X 的正弦值

*_C*<br/>
返回 _X 的余弦值

## <a name="sincosf"></a><a name="sincosf"></a>辛科斯夫

计算_X的子值和可次值

```cpp
inline void sincosf(
    float _X,
    float* _S,
    float* _C) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_S*<br/>
返回 _X 的正弦值

*_C*<br/>
返回 _X 的余弦值

## <a name="sinh"></a><a name="sinh"></a>辛赫

计算参数的双曲子值

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正弦值

## <a name="sinhf"></a><a name="sinhf"></a>辛夫

计算参数的双曲子值

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正弦值

## <a name="sqrt"></a><a name="sqrt"></a>sqrt

计算参数的平方根

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根

## <a name="sqrtf"></a><a name="sqrtf"></a>斯克尔夫

计算参数的平方根

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根

## <a name="tan"></a><a name="tan"></a>潭

计算参数的切线值

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正切值

## <a name="tanf"></a><a name="tanf"></a>坦夫

计算参数的切线值

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正切值

## <a name="tanh"></a><a name="tanh"></a>坦赫

计算参数的双曲切线值

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正切值

## <a name="tanhf"></a><a name="tanhf"></a>坦夫

计算参数的双曲切线值

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正切值

## <a name="trunc"></a><a name="trunc"></a>特鲁恩

将参数截断到整数组件

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的整数部分

## <a name="truncf"></a><a name="truncf"></a>特伦CF

将参数截断到整数组件

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的整数部分

## <a name="requirements"></a>要求

**标题：** amp_math.h**命名空间：** 并发：：fast_math

## <a name="see-also"></a>另请参阅

[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)
