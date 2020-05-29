---
title: Concurrency::precise_math 命名空间函数
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: ee6ab2313fbdc288ebba1b3fdacf192b7b578eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321848"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math 命名空间函数

||||
|-|-|-|
|[阿科斯](#acos)|[acosf](#acosf)|[阿科什](#acosh)|
|[acoshf](#acoshf)|[阿辛](#asin)|[asinf](#asinf)|
|[阿辛](#asinh)|[asinhf](#asinhf)|[阿坦](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[阿坦](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[塞伊尔](#ceil)|[ceilf](#ceilf)|
|[copysign](#copysign)|[copysignf](#copysignf)|[因为](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[科斯皮](#cospi)|[科斯皮夫](#cospif)|[埃尔夫](#erf)|
|[埃尔夫克](#erfc)|[erfcf](#erfcf)|[埃尔夫夫夫](#erfcinv)|
|[埃尔夫辛夫夫](#erfcinvf)|[erff](#erff)|[埃尔菲夫](#erfinv)|
|[埃尔芬夫夫](#erfinvf)|[exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[地板](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[弗莫德](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[弗雷克斯普夫](#frexpf)|[假说](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[是有限的](#isfinite)|
|[是因夫](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[尔德克斯普夫](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[日志](#log)|[日志10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[日志2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[之后](#nextafter)|
|[下一个后](#nextafterf)|[披](#phi)|[菲夫](#phif)|
|[战俘](#pow)|[powf](#powf)|[普罗比特](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[剩余](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[轮](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[鳞状](#scalb)|
|[卡尔布布](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[符号比夫](#signbitf)|[罪](#sin)|
|[辛科斯](#sincos)|[辛科斯夫](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[辛皮](#sinpi)|
|[辛菲夫](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[潭](#tan)|[tanf](#tanf)|[坦赫](#tanh)|
|[tanhf](#tanhf)|[坦皮](#tanpi)|[坦菲夫](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[特鲁恩](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a><a name="acos"></a>阿科斯

计算参数的弧形

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
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

## <a name="acosh"></a><a name="acosh"></a>阿科什

计算自变量的反双曲余弦值

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲余弦值

## <a name="acoshf"></a><a name="acoshf"></a>阿科什夫

计算自变量的反双曲余弦值

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲余弦值

## <a name="asin"></a><a name="asin"></a>阿辛

计算参数的弧形

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
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

## <a name="asinh"></a><a name="asinh"></a>阿辛

计算自变量的反双曲正弦值

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正弦值

## <a name="asinhf"></a><a name="asinhf"></a>阿辛夫

计算自变量的反双曲正弦值

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正弦值

## <a name="atan"></a><a name="atan"></a>阿坦

计算参数的反正切值

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
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

inline double atan2(
    double _Y,
    double _X) restrict(amp);
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

## <a name="atanh"></a><a name="atanh"></a>阿坦

计算自变量的反双曲正切值

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正切值

## <a name="atanhf"></a><a name="atanhf"></a>阿坦hf

计算自变量的反双曲正切值

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正切值

## <a name="cbrt"></a><a name="cbrt"></a>cbrt

计算自变量的实立方根

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的实立方根

## <a name="cbrtf"></a><a name="cbrtf"></a>cbrtf

计算自变量的实立方根

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的实立方根

## <a name="ceil"></a><a name="ceil"></a>塞伊尔

计算参数的上限

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
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

## <a name="copysign"></a><a name="copysign"></a>复制符号

用 _X 的大小和 _Y 的符号生成一个值

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回一个值，它具有 _X 的大小和 _Y 的符号

## <a name="copysignf"></a><a name="copysignf"></a>复制符号f

用 _X 的大小和 _Y 的符号生成一个值

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回一个值，它具有 _X 的大小和 _Y 的符号

## <a name="cos"></a><a name="cos"></a>因为

计算参数的余弦值

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的余弦值

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

## <a name="cosh"></a><a name="cosh"></a>科什

计算参数的双曲性抛物值

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反双曲余弦值

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

## <a name="cospi"></a><a name="cospi"></a>科斯皮

计算 pi \* _X的可数值

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi \* _X的可数值

## <a name="cospif"></a><a name="cospif"></a>科斯皮夫

计算 pi \* _X的可数值

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi \* _X的可数值

## <a name="erf"></a><a name="erf"></a>埃尔夫

计算 _X 的错误函数

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的错误函数

## <a name="erfc"></a><a name="erfc"></a>埃尔夫克

计算 _X 的互补错误函数

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的互补错误函数

## <a name="erfcf"></a><a name="erfcf"></a>埃尔夫夫

计算 _X 的互补错误函数

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的互补错误函数

## <a name="erfcinv"></a><a name="erfcinv"></a>埃尔夫夫夫

计算 _X 的反互补错误函数

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反互补错误函数

## <a name="erfcinvf"></a><a name="erfcinvf"></a>埃尔夫辛夫夫

计算 _X 的反互补错误函数

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反互补错误函数

## <a name="erff"></a><a name="erff"></a>埃尔夫

计算 _X 的错误函数

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的错误函数

## <a name="erfinv"></a><a name="erfinv"></a>埃尔菲夫

计算 _X 的反向错误函数

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反向错误函数

## <a name="erfinvf"></a><a name="erfinvf"></a>埃尔芬夫夫

计算 _X 的反向错误函数

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反向错误函数

## <a name="exp10"></a><a name="exp10"></a>exp10

计算参数的基-10 指数

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的基-10 指数

## <a name="exp10f"></a><a name="exp10f"></a>exp10f

计算参数的基-10 指数

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的基-10 指数

## <a name="expm1"></a><a name="expm1"></a>expm1

计算参数的以 e 为底的指数，减去 1

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>参数

*指数*<br/>
数学表达式`e` <sup>n</sup>的指数项*n，* 其中`e`是自然对数的基点。

### <a name="return-value"></a>返回值

返回自变量的以 e 为底的指数，减去 1

## <a name="expm1f"></a><a name="expm1f"></a>expm1f

计算参数的以 e 为底的指数，减去 1

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>参数

*指数*<br/>
数学表达式`e` <sup>n</sup>的指数项*n，* 其中`e`是自然对数的基点。

### <a name="return-value"></a>返回值

返回自变量的以 e 为底的指数，减去 1

## <a name="exp"></a><a name="exp"></a>exp

计算参数的基-e 指数

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的指数

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

## <a name="exp2"></a><a name="exp2"></a>exp2

计算参数的基-2 指数

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
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

## <a name="fabs"></a><a name="fabs"></a>晶圆厂

返回参数的绝对值

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

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

## <a name="fdim"></a><a name="fdim"></a>外国直接投资姆

计算参数之间的正差。

```cpp
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值 *_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

如果_X大于_Y，则_X和_Y之间的差异;否则，|0。

## <a name="fdimf"></a><a name="fdimf"></a>卢夫菲夫

计算参数之间的正差。

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值 *_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

如果_X大于_Y，则_X和_Y之间的差异;否则，|0。

## <a name="floor"></a><a name="floor"></a>地板

计算参数的楼层

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
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

## <a name="a-namefma-fma"></a><a name="fma">fma

计算第一个和第二个指定参数的组成，然后将第三个指定的参数添加到结果;整个计算作为单个操作执行。

```cpp
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点参数。
*_Y*<br/>
第二个浮点参数。
*_Z*<br/>
第三个浮点参数。

### <a name="return-value"></a>返回值

表达式（_X_Y） \* = _Z的结果。 整个计算作为单个操作执行;也就是说，子表达式计算为无限精度，并且只有最终结果四舍五入。

## <a name="fmaf"></a><a name="fmaf"></a>费夫

计算第一个和第二个指定参数的组成，然后将第三个指定的参数添加到结果;整个计算作为单个操作执行。

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点参数。
*_Y*<br/>
第二个浮点参数。
*_Z*<br/>
第三个浮点参数。

### <a name="return-value"></a>返回值

表达式（_X_Y） \* = _Z的结果。 整个计算作为单个操作执行;也就是说，子表达式计算为无限精度，并且只有最终结果四舍五入。

## <a name="fmax"></a><a name="fmax"></a>fmax

确定参数的最大数值

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

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
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

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

## <a name="fmod-function-c-amp"></a><a name="fmod"></a>fmod 功能（C++ AMP）

计算第一个指定参数的其余部分除以第二个指定参数。

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点参数。

*_Y*<br/>
第二个浮点参数。

### <a name="return-value"></a>返回值

其余除`_X`以`_Y`：`_X` - `_Y`即 n*的值，* 其中*n*是一个整体整数，因此`_X` - `_Y`*n*的幅度小于 的`_Y`幅度。

## <a name="fmodf"></a><a name="fmodf"></a>fmodf

计算第一个指定参数的其余部分除以第二个指定参数。

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点参数。

*_Y*<br/>
第二个浮点参数。

### <a name="return-value"></a>返回值

其余除`_X`以`_Y`：`_X` - `_Y`即 n*的值，* 其中*n*是一个整体整数，因此`_X` - `_Y`*n*的幅度小于 的`_Y`幅度。

## <a name="fpclassify"></a><a name="fpclassify"></a>fp分类

将参数值分类为 NaN、无穷大、正常、次正常、零

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回与自变量值相对应的数字分类宏的值。

## <a name="frexp"></a><a name="frexp"></a>弗雷费浦

获取_X的曼蒂萨和指数

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
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

## <a name="hypot"></a><a name="hypot"></a>假说

计算 _X 和 _Y 平方和的平方根

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 和 _Y 平方和的平方根

## <a name="hypotf"></a><a name="hypotf"></a>hypotf

计算 _X 和 _Y 平方和的平方根

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 和 _Y 平方和的平方根

## <a name="ilogb"></a><a name="ilogb"></a>伊洛格布

以有符号整数值形式提取 _X 的指数

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

以有符号整数值形式返回 _X 的指数

## <a name="ilogbf"></a><a name="ilogbf"></a>伊洛格布布

以有符号整数值形式提取 _X 的指数

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

以有符号整数值形式返回 _X 的指数

## <a name="isfinite"></a><a name="isfinite"></a>是有限的

确定参数是否具有有限值

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
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

inline int isinf(double _X) restrict(amp);
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

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有 NaN 值时，返回一个非零值

## <a name="isnormal"></a><a name="isnormal"></a>是正常现象

确定自变量是否规范

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当参数具有规范值时，返回一个非零值

## <a name="ldexp"></a><a name="ldexp"></a>尔德莫

从指定的指数和指数计算实数。

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值，曼蒂萨

*_Exp*<br/>
整数值，指数

### <a name="return-value"></a>返回值

返回_X \* 2+_Exp

## <a name="ldexpf"></a><a name="ldexpf"></a>尔德克斯普夫

从指定的指数和指数计算实数。

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值，曼蒂萨

*_Exp*<br/>
整数值，指数

### <a name="return-value"></a>返回值

返回_X \* 2+_Exp

## <a name="lgamma"></a><a name="lgamma"></a>卢马马

计算自变量伽玛绝对值的自然对数

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Sign*<br/>
返回符号

### <a name="return-value"></a>返回值

返回参数伽玛绝对值的自然对数

## <a name="lgammaf"></a><a name="lgammaf"></a>卢加马夫

计算自变量伽玛绝对值的自然对数

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Sign*<br/>
返回符号

### <a name="return-value"></a>返回值

返回参数伽玛绝对值的自然对数

## <a name="log"></a><a name="log"></a>日志

计算参数的基数-e对数

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
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

inline double log10(double _X) restrict(amp);
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

## <a name="log1p"></a><a name="log1p"></a>日志1p

计算 1 加参数的以 e 为底的对数

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 1加参数的以 e 为底的对数

## <a name="log1pf"></a><a name="log1pf"></a>日志1pf

计算 1 加参数的以 e 为底的对数

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 1加参数的以 e 为底的对数

## <a name="log2"></a><a name="log2"></a>日志2

计算参数的基 2 对数

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

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

## <a name="logb"></a><a name="logb"></a>日志

以浮点格式的有符号整数值形式提取 _X 的指数

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的有符号指数

## <a name="logbf"></a><a name="logbf"></a>logbf

以浮点格式的有符号整数值形式提取 _X 的指数

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的有符号指数

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

将指定的参数拆分为小数和整数部分。

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Iptr*<br/>
[出]的整数部分`_X`作为浮点值。

### <a name="return-value"></a>返回值

的符号小数部分`_X`。

## <a name="modff"></a><a name="modff"></a>莫德夫

将指定的参数拆分为小数和整数部分。

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Iptr*<br/>
的整数部分`_X`作为浮点值。

### <a name="return-value"></a>返回值

返回`_X`的已签名小数部分。

## <a name="nan"></a><a name="nan"></a>南

返回一个静态 NaN

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

如果可以，用 _X 中指示的内容返回静态 NaN

## <a name="nanf"></a><a name="nanf"></a>南夫

返回一个静态 NaN

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

如果可以，用 _X 中指示的内容返回静态 NaN

## <a name="nearbyint"></a><a name="nearbyint"></a>附近

通过使用当前舍入方向，将参数舍入为浮点格式的整数值。

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回舍入后的整数值。

## <a name="nearbyintf"></a><a name="nearbyintf"></a>附近

通过使用当前舍入方向，将参数舍入为浮点格式的整数值。

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回舍入后的整数值。

## <a name="nextafter"></a><a name="nextafter"></a>之后

在_X后，确定函数类型的下一个可表示值_Y

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回函数类型中的下一个可表示值，_X_Y

## <a name="nextafterf"></a><a name="nextafterf"></a>下一个后

在_X后，确定函数类型的下一个可表示值_Y

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回函数类型中的下一个可表示值，_X_Y

## <a name="phi"></a><a name="phi"></a>披

返回参数的累积分布函数

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的累积分布函数

## <a name="phif"></a><a name="phif"></a>菲夫

返回参数的累积分布函数

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的累积分布函数

## <a name="pow"></a><a name="pow"></a>战俘

计算_X提升到_Y功率

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值，底数

*_Y*<br/>
浮点值，指数

### <a name="return-value"></a>返回值

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

## <a name="probit"></a><a name="probit"></a>普罗比特

返回参数的反向累积分布函数

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反向累积分布函数

## <a name="probitf"></a><a name="probitf"></a>probitf

返回参数的反向累积分布函数

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反向累积分布函数

## <a name="rcbrt"></a><a name="rcbrt"></a>rcbrt

返回参数的多维数据集根的对等

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的多维数据集根的对等

## <a name="rcbrtf"></a><a name="rcbrtf"></a>rcbrtf

返回参数的多维数据集根的对等

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的多维数据集根的对等

## <a name="remainder"></a><a name="remainder"></a>剩余

计算余数：_X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X REM _Y

## <a name="remainderf"></a><a name="remainderf"></a>余夫

计算余数：_X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X REM _Y

## <a name="remquo"></a><a name="remquo"></a>雷姆库

计算第一个指定参数的其余部分除以第二个指定参数。 还计算第一个指定参数的符号的商，除以第二个指定参数的符号，并使用第三个参数中指定的位置返回商。

```cpp
inline float remquo(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);

inline double remquo(
    double _X,
    double _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点参数。

*_Y*<br/>
第二个浮点参数。

*_Quo*<br/>
[出]用于返回`_X`除以的小数位除以 的小数位的小数位的商数的地址`_Y`。

### <a name="return-value"></a>返回值

返回除以`_X`的剩余部分`_Y`。

## <a name="remquof"></a><a name="remquof"></a>雷姆库乌姆

计算第一个指定参数的其余部分除以第二个指定参数。 还计算第一个指定参数的符号的商，除以第二个指定参数的符号，并使用第三个参数中指定的位置返回商。

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点参数。

*_Y*<br/>
第二个浮点参数。

*_Quo*<br/>
[出]用于返回`_X`除以的小数位除以 的小数位的小数位的商数的地址`_Y`。

### <a name="return-value"></a>返回值

返回除以`_X`的剩余部分`_Y`。

## <a name="round"></a><a name="round"></a>轮

舍_X到最接近的整数

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
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

inline double rsqrt(double _X) restrict(amp);
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

## <a name="scalb"></a><a name="scalb"></a>鳞状

用 _X 乘以 FLT_RADIX 的 _Y 次方

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回_X（FLT_RADIX \* = _Y）

## <a name="scalbf"></a><a name="scalbf"></a>卡尔布布

用 _X 乘以 FLT_RADIX 的 _Y 次方

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
浮点值

### <a name="return-value"></a>返回值

返回_X（FLT_RADIX \* = _Y）

## <a name="scalbn"></a><a name="scalbn"></a>斯万布

用 _X 乘以 FLT_RADIX 的 _Y 次方

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回_X（FLT_RADIX \* = _Y）

## <a name="scalbnf"></a><a name="scalbnf"></a>卡尔本夫

用 _X 乘以 FLT_RADIX 的 _Y 次方

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Y*<br/>
整数值

### <a name="return-value"></a>返回值

返回_X（FLT_RADIX \* = _Y）

## <a name="signbit"></a><a name="signbit"></a>符号位

确定 _X 的符号是否为负号

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
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

inline double sin(double _X) restrict(amp);
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
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);

inline void sincos(
    double _X,
    _Out_ double* _S,
    _Out_ double* _C) restrict(amp);
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
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
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

inline double sinh(double _X) restrict(amp);
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

## <a name="sinpi"></a><a name="sinpi"></a>辛皮

计算 pi \* _X的子值

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi \* _X的子值

## <a name="sinpif"></a><a name="sinpif"></a>辛菲夫

计算 pi \* _X的子值

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi \* _X的子值

## <a name="sqrt"></a><a name="sqrt"></a>sqrt

计算参数的平方根

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
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

inline double tan(double _X) restrict(amp);
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

inline double tanh(double _X) restrict(amp);
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

## <a name="tanpi"></a><a name="tanpi"></a>坦皮

计算 pi\*的切线值_X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi\*的切线值_X

## <a name="tanpif"></a><a name="tanpif"></a>坦菲夫

计算 pi\*的切线值_X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi\*的切线值_X

## <a name="tgamma"></a><a name="tgamma"></a>特伽马

计算 _X 的伽玛函数

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的伽玛函数的结果

## <a name="tgammaf"></a><a name="tgammaf"></a>特加马夫

计算 _X 的伽玛函数

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的伽玛函数的结果

## <a name="trunc"></a><a name="trunc"></a>特鲁恩

将参数截断到整数组件

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
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

## <a name="see-also"></a>另请参阅

[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)
