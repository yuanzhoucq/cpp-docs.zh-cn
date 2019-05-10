---
title: 'Concurrency:: precise_math 命名空间函数'
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
ms.openlocfilehash: 7690c0629e7035d0130f0a7dbdcabf3e959ae7b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180396"
---
# <a name="concurrencyprecisemath-namespace-functions"></a>Concurrency:: precise_math 命名空间函数

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[acosh](#acosh)|
|[acoshf](#acoshf)|[asin](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf](#ceilf)|
|[copysign](#copysign)|[copysignf](#copysignf)|[cos](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[cospi](#cospi)|[cospif](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|
|[erfinvf](#erfinvf)|[exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|
|[isinf](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[log](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[phi](#phi)|[phif](#phif)|
|[pow](#pow)|[powf](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[remainder](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[round](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[sin](#sin)|
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|
|[sinpif](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[tan](#tan)|[tanf](#tanf)|[tanh](#tanh)|
|[tanhf](#tanhf)|[tanpi](#tanpi)|[tanpif](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[trunc](#trunc)|
|[truncf](#truncf)|

##  <a name="acos"></a>acos

计算自变量的反余弦值

```
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反余弦值

##  <a name="acosf"></a>  acosf

计算自变量的反余弦值

```
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反余弦值

##  <a name="acosh"></a>  acosh

计算自变量的反双曲余弦值

```
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲余弦值

##  <a name="acoshf"></a>  acoshf

计算自变量的反双曲余弦值

```
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲余弦值

##  <a name="asin"></a>  asin

计算自变量的反正弦值

```
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正弦值

##  <a name="asinf"></a>  asinf

计算自变量的反正弦值

```
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正弦值

##  <a name="asinh"></a>  asinh

计算自变量的反双曲正弦值

```
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正弦值

##  <a name="asinhf"></a>  asinhf

计算自变量的反双曲正弦值

```
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正弦值

##  <a name="atan"></a>  atan

计算参数的反正切值

```
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正切值

##  <a name="atan2"></a>  atan2

计算 _Y/_X 的反正切值

```
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

##  <a name="atan2f"></a>  atan2f

计算 _Y/_X 的反正切值

```
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

##  <a name="atanf"></a>  atanf

计算参数的反正切值

```
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正切值

##  <a name="atanh"></a>  atanh

计算自变量的反双曲正切值

```
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正切值

##  <a name="atanhf"></a>  atanhf

计算自变量的反双曲正切值

```
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反双曲正切值

##  <a name="cbrt"></a>  cbrt

计算自变量的实立方根

```
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的实立方根

##  <a name="cbrtf"></a>  cbrtf

计算自变量的实立方根

```
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的实立方根

##  <a name="ceil"></a>  ceil

计算参数的上限

```
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的上限

##  <a name="ceilf"></a>  ceilf

计算参数的上限

```
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的上限

##  <a name="copysign"></a>  copysign

用 _X 的大小和 _Y 的符号生成一个值

```
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

##  <a name="copysignf"></a>  copysignf

用 _X 的大小和 _Y 的符号生成一个值

```
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

##  <a name="cos"></a>  cos

计算参数的余弦值

```
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的余弦值

##  <a name="cosf"></a>  cosf

计算参数的余弦值

```
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的余弦值

##  <a name="cosh"></a>  cosh

计算参数的双曲余弦值

```
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反双曲余弦值

##  <a name="coshf"></a>  coshf

计算参数的双曲余弦值

```
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反双曲余弦值

##  <a name="cospi"></a>  cospi

计算 pi 的余弦值\*_X

```
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi 的余弦值\*_X

##  <a name="cospif"></a>  cospif

计算 pi 的余弦值\*_X

```
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi 的余弦值\*_X

##  <a name="erf"></a>  erf

计算 _X 的错误函数

```
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的错误函数

##  <a name="erfc"></a>  erfc

计算 _X 的互补错误函数

```
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的互补错误函数

##  <a name="erfcf"></a>  erfcf

计算 _X 的互补错误函数

```
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的互补错误函数

##  <a name="erfcinv"></a>  erfcinv

计算 _X 的反互补错误函数

```
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反互补错误函数

##  <a name="erfcinvf"></a>  erfcinvf

计算 _X 的反互补错误函数

```
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反互补错误函数

##  <a name="erff"></a>  erff

计算 _X 的错误函数

```
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的错误函数

##  <a name="erfinv"></a>  erfinv

计算 _X 的反向错误函数

```
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反向错误函数

##  <a name="erfinvf"></a>  erfinvf

计算 _X 的反向错误函数

```
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的反向错误函数

##  <a name="exp10"></a>  exp10

计算基数 10 的自变量的指数

```
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 base 10 参数的指数

##  <a name="exp10f"></a>  exp10f

计算基数 10 的自变量的指数

```
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 base 10 参数的指数

##  <a name="expm1"></a>  expm1

计算参数的以 e 为底的指数，减去 1

```
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>参数

*exponent*<br/>
指数项*n*的数学表达式`e` <sup>n</sup>，其中`e`是自然对数的底数。

### <a name="return-value"></a>返回值

返回自变量的以 e 为底的指数，减去 1

##  <a name="expm1f"></a>  expm1f

计算参数的以 e 为底的指数，减去 1

```
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>参数

*exponent*<br/>
指数项*n*的数学表达式`e` <sup>n</sup>，其中`e`是自然对数的底数。

### <a name="return-value"></a>返回值

返回自变量的以 e 为底的指数，减去 1

##  <a name="exp"></a>  exp

计算以 e 为底的参数的指数

```
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的指数

##  <a name="expf"></a>  expf

计算以 e 为底的参数的指数

```
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的指数

##  <a name="exp2"></a>  exp2

计算 2 为底的参数的指数

```
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 2 为底的指数

##  <a name="exp2f"></a>  exp2f

计算 2 为底的参数的指数

```
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 2 为底的指数

##  <a name="fabs"></a>  fabs

返回自变量的绝对值

```
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的绝对值

##  <a name="fabsf"></a>  fabsf

返回自变量的绝对值

```
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的绝对值

## <a name="fdim"></a> fdim

计算参数之间的正数差。
```
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

_X 和 _Y 如果 _X 大于 _Y; 之间的差异否则为 + 0。

## <a name="fdimf"></a> fdimf

计算参数之间的正数差。
```
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

_X 和 _Y 如果 _X 大于 _Y; 之间的差异否则为 + 0。

##  <a name="floor"></a>  floor

计算参数的下限

```
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的下限

##  <a name="floorf"></a>  floorf

计算参数的下限

```
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的下限

## <a name="a-namefma-fma"></a><a name="fma"> fma

计算产品的第一个和第二个指定参数，然后将第三个指定的参数添加到结果;整个计算是作为单个操作执行的。
```
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
第一个浮点自变量。
*_Y*<br/>
第二个浮点自变量。
*_Z*<br/>
第三个浮点自变量。

### <a name="return-value"></a>返回值

该表达式的结果 (_X \* _Y) + _Z。 整个计算执行作为单个操作;也就是说，子表达式计算到无限精度并且仅对最终结果舍入。

## <a name="fmaf"></a> fmaf

计算产品的第一个和第二个指定参数，然后将第三个指定的参数添加到结果;整个计算是作为单个操作执行的。
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点自变量。
*_Y*<br/>
第二个浮点自变量。
*_Z*<br/>
第三个浮点自变量。

### <a name="return-value"></a>返回值

该表达式的结果 (_X \* _Y) + _Z。 整个计算执行作为单个操作;也就是说，子表达式计算到无限精度并且仅对最终结果舍入。

##  <a name="fmax"></a>  fmax

确定自变量的最大数值

```
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

返回自变量的最大数值

##  <a name="fmaxf"></a>  fmaxf

确定自变量的最大数值

```
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

返回自变量的最大数值

##  <a name="fmin"></a>  fmin

确定自变量的最小数值

```
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

返回自变量的最小数值

##  <a name="fminf"></a>  fminf

确定自变量的最小数值

```
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

返回自变量的最小数值

##  <a name="fmod"></a>  fmod 函数 (C++ a m P)

计算指定第一个参数除以第二个指定参数的余数。

```
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点自变量。

*_Y*<br/>
第二个浮点自变量。

### <a name="return-value"></a>返回值

其余`_X`除以`_Y`; 的值，即`_X`  -  `_Y` *n*，其中*n*均为整数，以便的量`_X`  -  `_Y` *n*小于的量`_Y`。

##  <a name="fmodf"></a>  fmodf

计算指定第一个参数除以第二个指定参数的余数。

```
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点自变量。

*_Y*<br/>
第二个浮点自变量。

### <a name="return-value"></a>返回值

其余`_X`除以`_Y`; 的值，即`_X`  -  `_Y` *n*，其中*n*均为整数，以便的量`_X`  -  `_Y` *n*小于的量`_Y`。

##  <a name="fpclassify"></a>  fpclassify

将参数值分类为 NaN、无穷大、正常、次正常、零

```
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回与自变量值相对应的数字分类宏的值。

##  <a name="frexp"></a>  frexp

获取的尾数和 _X 的指数

```
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

##  <a name="frexpf"></a>  frexpf

获取的尾数和 _X 的指数

```
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

##  <a name="hypot"></a>  hypot

计算 _X 和 _Y 平方和的平方根

```
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

##  <a name="hypotf"></a>  hypotf

计算 _X 和 _Y 平方和的平方根

```
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

##  <a name="ilogb"></a>  ilogb

以有符号整数值形式提取 _X 的指数

```
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

以有符号整数值形式返回 _X 的指数

##  <a name="ilogbf"></a>  ilogbf

以有符号整数值形式提取 _X 的指数

```
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

以有符号整数值形式返回 _X 的指数

##  <a name="isfinite"></a>  isfinite

确定参数是否具有有限的值

```
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有有限值时，返回一个非零值

##  <a name="isinf"></a>  isinf

确定参数是否是无穷

```
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有无限值时，返回一个非零值

##  <a name="isnan"></a>  isnan

确定参数是否是 NaN

```
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有 NaN 值时，返回一个非零值

##  <a name="isnormal"></a>  isnormal

确定自变量是否规范

```
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当参数具有规范值时，返回一个非零值

##  <a name="ldexp"></a>  ldexp

计算将实数从指定的尾数和指数。

```
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值尾数

*_Exp*<br/>
整数值指数

### <a name="return-value"></a>返回值

返回 _X \* 2 ^ 2^_exp

##  <a name="ldexpf"></a>  ldexpf

计算将实数从指定的尾数和指数。

```
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值尾数

*_Exp*<br/>
整数值指数

### <a name="return-value"></a>返回值

返回 _X \* 2 ^ 2^_exp

##  <a name="lgamma"></a>  lgamma

计算自变量伽玛绝对值的自然对数

```
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

##  <a name="lgammaf"></a>  lgammaf

计算自变量伽玛绝对值的自然对数

```
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

##  <a name="log"></a>  log

计算自变量的以 e 为底的对数

```
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的对数

##  <a name="log10"></a>  log10

计算自变量的以 10 为基数的对数

```
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

##  <a name="log10f"></a>  log10f

计算自变量的以 10 为基数的对数

```
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

##  <a name="log1p"></a>  log1p

计算 1 加参数的以 e 为底的对数

```
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 1加参数的以 e 为底的对数

##  <a name="log1pf"></a>  log1pf

计算 1 加参数的以 e 为底的对数

```
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 1加参数的以 e 为底的对数

##  <a name="log2"></a>  log2

计算参数的 2 为底对数

```
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

##  <a name="log2f"></a>  log2f

计算参数的 2 为底对数

```
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

##  <a name="logb"></a>  logb

以浮点格式的有符号整数值形式提取 _X 的指数

```
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的有符号指数

##  <a name="logbf"></a>  logbf

以浮点格式的有符号整数值形式提取 _X 的指数

```
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的有符号指数

##  <a name="logf"></a>  logf

计算自变量的以 e 为底的对数

```
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的对数

##  <a name="modf"></a>  modf

将拆分为小数部分指定的参数和整数部分。

```
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
[out]整数部分`_X`，作为浮点值。

### <a name="return-value"></a>返回值

有符号的小数部分的`_X`。

##  <a name="modff"></a>  modff

将拆分为小数部分指定的参数和整数部分。

```
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

*_Iptr*<br/>
整数部分`_X`，作为浮点值。

### <a name="return-value"></a>返回值

返回的有符号的小数部分`_X`。

##  <a name="nan"></a>  nan

返回一个静态 NaN

```
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

如果可以，用 _X 中指示的内容返回静态 NaN

##  <a name="nanf"></a>  nanf

返回一个静态 NaN

```
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

如果可以，用 _X 中指示的内容返回静态 NaN

##  <a name="nearbyint"></a>  nearbyint

通过使用当前舍入方向，将参数舍入为浮点格式的整数值。

```
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回舍入后的整数值。

##  <a name="nearbyintf"></a>  nearbyintf

通过使用当前舍入方向，将参数舍入为浮点格式的整数值。

```
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回舍入后的整数值。

##  <a name="nextafter"></a>  nextafter

在 _Y 方向上 _X 后确定函数的类型中的下一步可表示值

```
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

在 _Y 方向上 _X 后返回函数的类型中的下一个可表示值，

##  <a name="nextafterf"></a>  nextafterf

在 _Y 方向上 _X 后确定函数的类型中的下一步可表示值

```
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

在 _Y 方向上 _X 后返回函数的类型中的下一个可表示值，

##  <a name="phi"></a>  phi

返回自变量的累积分布函数

```
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的累积分布函数

##  <a name="phif"></a>  phif

返回自变量的累积分布函数

```
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的累积分布函数

##  <a name="pow"></a>  pow

计算 _X 的 _Y 次幂

```
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

##  <a name="powf"></a>  powf

计算 _X 的 _Y 次幂

```
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

##  <a name="probit"></a>  概率

返回自变量的反转累积分布函数

```
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反转累积分布函数

##  <a name="probitf"></a>  probitf

返回自变量的反转累积分布函数

```
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反转累积分布函数

##  <a name="rcbrt"></a>  rcbrt

返回自变量的立方根的倒数

```
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的立方根的倒数

##  <a name="rcbrtf"></a>  rcbrtf

返回自变量的立方根的倒数

```
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的立方根的倒数

##  <a name="remainder"></a>  remainder

计算余数：_X REM _Y

```
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

##  <a name="remainderf"></a>  remainderf

计算余数：_X REM _Y

```
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

##  <a name="remquo"></a>  remquo

计算指定第一个参数除以第二个指定参数的余数。 此外计算第一个指定参数除以第二个指定的参数的有效数字的有效数字的商，并返回商使用第三个参数中指定的位置。

```
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
第一个浮点自变量。

*_Y*<br/>
第二个浮点自变量。

*_Quo*<br/>
[out]一个整数，用于返回小数位数的商的地址`_X`小数位数除以`_Y`。

### <a name="return-value"></a>返回值

返回余数`_X`除以`_Y`。

##  <a name="remquof"></a>  remquof

计算指定第一个参数除以第二个指定参数的余数。 此外计算第一个指定参数除以第二个指定的参数的有效数字的有效数字的商，并返回商使用第三个参数中指定的位置。

```
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
第一个浮点自变量。

*_Y*<br/>
第二个浮点自变量。

*_Quo*<br/>
[out]一个整数，用于返回小数位数的商的地址`_X`小数位数除以`_Y`。

### <a name="return-value"></a>返回值

返回余数`_X`除以`_Y`。

##  <a name="round"></a>  舍入

将 _X 四舍五入为最接近的整数

```
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回最接近 _X 的整数

##  <a name="roundf"></a>  roundf

将 _X 四舍五入为最接近的整数

```
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回最接近 _X 的整数

##  <a name="rsqrt"></a>  rsqrt

返回自变量的平方根的倒数

```
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根的倒数

##  <a name="rsqrtf"></a>  rsqrtf

返回自变量的平方根的倒数

```
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根的倒数

##  <a name="scalb"></a>  scalb

用 _X 乘以 FLT_RADIX 的 _Y 次方

```
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

返回 _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbf"></a>  scalbf

用 _X 乘以 FLT_RADIX 的 _Y 次方

```
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

返回 _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbn"></a>  scalbn

用 _X 乘以 FLT_RADIX 的 _Y 次方

```
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

返回 _X \* (FLT_RADIX ^ _Y)

##  <a name="scalbnf"></a>  scalbnf

用 _X 乘以 FLT_RADIX 的 _Y 次方

```
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

返回 _X \* (FLT_RADIX ^ _Y)

##  <a name="signbit"></a>  signbit

确定 _X 的符号是否为负号

```
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当 _X 的符号为负号时，返回一个非零值

##  <a name="signbitf"></a>  signbitf

确定 _X 的符号是否为负号

```
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当 _X 的符号为负号时，返回一个非零值

##  <a name="sin"></a>  sin

计算参数的正弦值

```
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正弦值

##  <a name="sinf"></a>  sinf

计算参数的正弦值

```
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正弦值

##  <a name="sincos"></a>  sincos

计算 _X 的正弦和余弦值

```
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

##  <a name="sincosf"></a>  sincosf

计算 _X 的正弦和余弦值

```
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

##  <a name="sinh"></a>  sinh

计算参数的双曲正弦值

```
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正弦值

##  <a name="sinhf"></a>  sinhf

计算参数的双曲正弦值

```
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正弦值

##  <a name="sinpi"></a>  sinpi

计算 pi 的正弦值\*_X

```
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi 的正弦值\*_X

##  <a name="sinpif"></a>  sinpif

计算 pi 的正弦值\*_X

```
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi 的正弦值\*_X

##  <a name="sqrt"></a>  sqrt

计算参数的平方根

```
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根

##  <a name="sqrtf"></a>  sqrtf

计算参数的平方根

```
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根

##  <a name="tan"></a>  tan

计算参数的正切值

```
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正切值

##  <a name="tanf"></a>  tanf

计算参数的正切值

```
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正切值

##  <a name="tanh"></a>  tanh

计算参数的双曲正切值

```
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正切值

##  <a name="tanhf"></a>  tanhf

计算参数的双曲正切值

```
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正切值

##  <a name="tanpi"></a>  tanpi

计算 pi 的正切值\*_X

```
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi 的正切值\*_X

##  <a name="tanpif"></a>  tanpif

计算 pi 的正切值\*_X

```
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 pi 的正切值\*_X

##  <a name="tgamma"></a>  tgamma

计算 _X 的伽玛函数

```
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的伽玛函数的结果

##  <a name="tgammaf"></a>  tgammaf

计算 _X 的伽玛函数

```
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回 _X 的伽玛函数的结果

##  <a name="trunc"></a>  trunc

将截断为整数部分参数

```
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的整数部分

##  <a name="truncf"></a>  truncf

将截断为整数部分参数

```
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的整数部分

## <a name="see-also"></a>请参阅

[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)
