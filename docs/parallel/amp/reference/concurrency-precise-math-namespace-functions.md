---
title: "Concurrency:: precise_math 命名空间函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 73273a58f73860c77810a6ab59def560962f9539
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyprecisemath-namespace-functions"></a>Concurrency:: precise_math 命名空间函数
||||  
|-|-|-|  
|[acos 函数](#acos)|[acosf 函数](#acosf)|[acosh 函数](#acosh)|  
|[acoshf 函数](#acoshf)|[asin 函数](#asin)|[asinf 函数](#asinf)|  
|[asinh 函数](#asinh)|[asinhf 函数](#asinhf)|[atan 函数](#atan)|  
|[atan2 函数](#atan2)|[atan2f 函数](#atan2f)|[atanf 函数](#atanf)|  
|[atanh 函数](#atanh)|[atanhf 函数](#atanhf)|[cbrt 函数](#cbrt)|  
|[cbrtf 函数](#cbrtf)|[ceil 函数](#ceil)|[ceilf 函数](#ceilf)|  
|[copysign 函数](#copysign)|[copysignf 函数](#copysignf)|[cos 函数](#cos)|  
|[cosf 函数](#cosf)|[cosh 函数](#cosh)|[coshf 函数](#coshf)|  
|[cospi 函数](#cospi)|[cospif 函数](#cospif)|[erf 函数](#erf)|  
|[erfc 函数](#erfc)|[erfcf 函数](#erfcf)|[erfcinv 函数](#erfcinv)|  
|[erfcinvf 函数](#erfcinvf)|[erff 函数](#erff)|[erfinv 函数](#erfinv)|  
|[erfinvf 函数](#erfinvf)|[exp 函数](#exp)|[exp10 函数](#exp10)|  
|[exp10f 函数](#exp10f)|[exp2 函数](#exp2)|[exp2f 函数](#exp2f)|  
|[expf 函数](#expf)|[expm1 函数](#expm1)|[expm1f 函数](#expm1f)|  
|[fabs 函数](#fabs)|[fabsf 函数](#fabsf)|[floor 函数](#floor)| 
|[fdim 函数](#fdim)|[fdimf 函数](#fdimf)|| 
|[floorf 函数](#floorf)|[fma 函数](#fma)|[fmaf 函数](#fmaf)|
[fmax 函数](#fmax)|[fmaxf 函数](#fmaxf)|| 
|[fmin 函数](#fmin)|[fminf 函数](#fminf)|[fmod 函数](#fmod)|  
|[fmodf 函数](#fmodf)|[fpclassify 函数](#fpclassify)|[frexp 函数](#frexp)|  
|[frexpf 函数](#frexpf)|[hypot 函数](#hypot)|[hypotf 函数](#hypotf)|  
|[ilogb 函数](#ilogb)|[ilogbf 函数](#ilogbf)|[isfinite 函数](#isfinite)|  
|[isinf 函数](#isinf)|[isnan 函数](#isnan)|[isnormal 函数](#isnormal)|  
|[ldexp 函数](#ldexp)|[ldexpf 函数](#ldexpf)|[lgamma 函数](#lgamma)|  
|[lgammaf 函数](#lgammaf)|[log 函数](#log)|[log10 函数](#log10)|  
|[log10f 函数](#log10f)|[log1p 函数](#log1p)|[log1pf 函数](#log1pf)|  
|[log2 函数](#log2)|[log2f 函数](#log2f)|[logb 函数](#logb)|  
|[logbf 函数](#logbf)|[logf 函数](#logf)|[modf 函数](#modf)|  
|[modff 函数](#modff)|[nan 函数](#nan)|[nanf 函数](#nanf)|  
|[nearbyint 函数](#nearbyint)|[nearbyintf 函数](#nearbyintf)|[nextafter 函数](#nextafter)|  
|[nextafterf 函数](#nextafterf)|[phi 函数](#phi)|[phif 函数](#phif)|  
|[pow 函数](#pow)|[powf 函数](#powf)|[probit 函数](#probit)|  
|[probitf 函数](#probitf)|[rcbrt 函数](#rcbrt)|[rcbrtf 函数](#rcbrtf)|  
|[remainder 函数](#remainder)|[remainderf 函数](#remainderf)|[remquo 函数](#remquo)|  
|[remquof 函数](#remquof)|[round 函数](#round)|[roundf 函数](#roundf)|  
|[rsqrt 函数](#rsqrt)|[rsqrtf 函数](#rsqrtf)|[scalb 函数](#scalb)|  
|[scalbf 函数](#scalbf)|[scalbn 函数](#scalbn)|[scalbnf 函数](#scalbnf)|  
|[signbit 函数](#signbit)|[signbitf 函数](#signbitf)|[sin 函数](#sin)|  
|[sincos 函数](#sincos)|[sincosf 函数](#sincosf)|[sinf 函数](#sinf)|  
|[sinh 函数](#sinh)|[sinhf 函数](#sinhf)|[sinpi 函数](#sinpi)|  
|[sinpif 函数](#sinpif)|[sqrt 函数](#sqrt)|[sqrtf 函数](#sqrtf)|  
|[tan 函数](#tan)|[tanf 函数](#tanf)|[tanh 函数](#tanh)|  
|[tanhf 函数](#tanhf)|[tanpi 函数](#tanpi)|[tanpif 函数](#tanpif)|  
|[tgamma 函数](#tgamma)|[tgammaf 函数](#tgammaf)|[trunc 函数](#trunc)|  
|[truncf 函数](#truncf)|  
  
##  <a name="a-nameacosa--acos-function"></a><a name="acos"></a>acos 函数  
 计算参数的反余弦值  
  
```  
inline float acos(float _X) restrict(amp);

 
inline double acos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反余弦值  
  
##  <a name="a-nameacosfa--acosf-function"></a><a name="acosf"></a>acosf 函数  
 计算参数的反余弦值  
  
```  
inline float acosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反余弦值  
  
##  <a name="a-nameacosha--acosh-function"></a><a name="acosh"></a>acosh 函数  
 计算自变量的反双曲余弦值  
  
```  
inline float acosh(float _X) restrict(amp);

 
inline double acosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲余弦值  
  
##  <a name="a-nameacoshfa--acoshf-function"></a><a name="acoshf"></a>acoshf 函数  
 计算自变量的反双曲余弦值  
  
```  
inline float acoshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲余弦值  
  
##  <a name="a-nameasina--asin-function"></a><a name="asin"></a>asin 函数  
 计算参数的反正弦值  
  
```  
inline float asin(float _X) restrict(amp);

 
inline double asin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反正弦值  
  
##  <a name="a-nameasinfa--asinf-function"></a><a name="asinf"></a>asinf 函数  
 计算参数的反正弦值  
  
```  
inline float asinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反正弦值  
  
##  <a name="a-nameasinha--asinh-function"></a><a name="asinh"></a>asinh 函数  
 计算自变量的反双曲正弦值  
  
```  
inline float asinh(float _X) restrict(amp);

 
inline double asinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲正弦值  
  
##  <a name="a-nameasinhfa--asinhf-function"></a><a name="asinhf"></a>asinhf 函数  
 计算自变量的反双曲正弦值  
  
```  
inline float asinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲正弦值  
  
##  <a name="a-nameatana--atan-function"></a><a name="atan"></a>atan 函数  
 计算参数的反正切值  
  
```  
inline float atan(float _X) restrict(amp);

 
inline double atan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反正切值  
  
##  <a name="a-nameatan2a--atan2-function"></a><a name="atan2"></a>atan2 函数  
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
 `_Y`  
 浮点值  
  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _Y/_X 的反正切值  
  
##  <a name="a-nameatan2fa--atan2f-function"></a><a name="atan2f"></a>atan2f 函数  
 计算 _Y/_X 的反正切值  
  
```  
inline float atan2f(
    float _Y,  
    float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Y`  
 浮点值  
  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _Y/_X 的反正切值  
  
##  <a name="a-nameatanfa--atanf-function"></a><a name="atanf"></a>atanf 函数  
 计算参数的反正切值  
  
```  
inline float atanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反正切值  
  
##  <a name="a-nameatanha--atanh-function"></a><a name="atanh"></a>atanh 函数  
 计算自变量的反双曲正切值  
  
```  
inline float atanh(float _X) restrict(amp);

 
inline double atanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲正切值  
  
##  <a name="a-nameatanhfa--atanhf-function"></a><a name="atanhf"></a>atanhf 函数  
 计算自变量的反双曲正切值  
  
```  
inline float atanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲正切值  
  
##  <a name="a-namecbrta--cbrt-function"></a><a name="cbrt"></a>cbrt 函数  
 计算自变量的实立方根  
  
```  
inline float cbrt(float _X) restrict(amp);

 
inline double cbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的实立方根  
  
##  <a name="a-namecbrtfa--cbrtf-function"></a><a name="cbrtf"></a>cbrtf 函数  
 计算自变量的实立方根  
  
```  
inline float cbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的实立方根  
  
##  <a name="a-nameceila--ceil-function"></a><a name="ceil"></a>ceil 函数  
 计算参数的上限  
  
```  
inline float ceil(float _X) restrict(amp);

 
inline double ceil(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的上限  
  
##  <a name="a-nameceilfa--ceilf-function"></a><a name="ceilf"></a>ceilf 函数  
 计算参数的上限  
  
```  
inline float ceilf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的上限  
  
##  <a name="a-namecopysigna--copysign-function"></a><a name="copysign"></a>copysign 函数  
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
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回一个值，它具有 _X 的大小和 _Y 的符号  
  
##  <a name="a-namecopysignfa--copysignf-function"></a><a name="copysignf"></a>copysignf 函数  
 用 _X 的大小和 _Y 的符号生成一个值  
  
```  
inline float copysignf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回一个值，它具有 _X 的大小和 _Y 的符号  
  
##  <a name="a-namecosa--cos-function"></a><a name="cos"></a>cos 函数  
 计算参数的余弦值  
  
```  
inline float cos(float _X) restrict(amp);

 
inline double cos(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的余弦值  
  
##  <a name="a-namecosfa--cosf-function"></a><a name="cosf"></a>cosf 函数  
 计算参数的余弦值  
  
```  
inline float cosf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的余弦值  
  
##  <a name="a-namecosha--cosh-function"></a><a name="cosh"></a>cosh 函数  
 计算参数的双曲余弦值  
  
```  
inline float cosh(float _X) restrict(amp);

 
inline double cosh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲余弦值  
  
##  <a name="a-namecoshfa--coshf-function"></a><a name="coshf"></a>coshf 函数  
 计算参数的双曲余弦值  
  
```  
inline float coshf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲余弦值  
  
##  <a name="a-namecospia--cospi-function"></a><a name="cospi"></a>cospi 函数  
 计算 pi * _X 的余弦值  
  
```  
inline float cospi(float _X) restrict(amp);

 
inline double cospi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 pi * _X 的余弦值  
  
##  <a name="a-namecospifa--cospif-function"></a><a name="cospif"></a>cospif 函数  
 计算 pi * _X 的余弦值  
  
```  
inline float cospif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 pi * _X 的余弦值  
  
##  <a name="a-nameerfa--erf-function"></a><a name="erf"></a>erf 函数  
 计算 _X 的错误函数  
  
```  
inline float erf(float _X) restrict(amp);

 
inline double erf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的错误函数  
  
##  <a name="a-nameerfca--erfc-function"></a><a name="erfc"></a>erfc 函数  
 计算 _X 的互补错误函数  
  
```  
inline float erfc(float _X) restrict(amp);

 
inline double erfc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的互补错误函数  
  
##  <a name="a-nameerfcfa--erfcf-function"></a><a name="erfcf"></a>erfcf 函数  
 计算 _X 的互补错误函数  
  
```  
inline float erfcf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的互补错误函数  
  
##  <a name="a-nameerfcinva--erfcinv-function"></a><a name="erfcinv"></a>erfcinv 函数  
 计算 _X 的反互补错误函数  
  
```  
inline float erfcinv(float _X) restrict(amp);

 
inline double erfcinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的反互补错误函数  
  
##  <a name="a-nameerfcinvfa--erfcinvf-function"></a><a name="erfcinvf"></a>erfcinvf 函数  
 计算 _X 的反互补错误函数  
  
```  
inline float erfcinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的反互补错误函数  
  
##  <a name="a-nameerffa--erff-function"></a><a name="erff"></a>erff 函数  
 计算 _X 的错误函数  
  
```  
inline float erff(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的错误函数  
  
##  <a name="a-nameerfinva--erfinv-function"></a><a name="erfinv"></a>erfinv 函数  
 计算 _X 的反向错误函数  
  
```  
inline float erfinv(float _X) restrict(amp);

 
inline double erfinv(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的反向错误函数  
  
##  <a name="a-nameerfinvfa--erfinvf-function"></a><a name="erfinvf"></a>erfinvf 函数  
 计算 _X 的反向错误函数  
  
```  
inline float erfinvf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的反向错误函数  
  
##  <a name="a-nameexp10a--exp10-function"></a><a name="exp10"></a>exp10 函数  
 计算的以&10; 为基数的参数的指数  
  
```  
inline float exp10(float _X) restrict(amp);

 
inline double exp10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回的以&10; 为基数参数的指数  
  
##  <a name="a-nameexp10fa--exp10f-function"></a><a name="exp10f"></a>exp10f 函数  
 计算的以&10; 为基数的参数的指数  
  
```  
inline float exp10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回的以&10; 为基数参数的指数  
  
##  <a name="a-nameexpm1a--expm1-function"></a><a name="expm1"></a>expm1 函数  
 计算自变量的以 e 为底的指数，减去 1  
  
```  
inline float expm1(float exponent) restrict(amp);

 
inline double expm1(double exponent) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `exponent`  
 指数项*n*的数学表达式`e` <sup>n</sup>，其中`e`是自然对数的底数。  
  
### <a name="return-value"></a>返回值  
 返回自变量的以 e 为底的指数，减去 1  
  
##  <a name="a-nameexpm1fa--expm1f-function"></a><a name="expm1f"></a>expm1f 函数  
 计算自变量的以 e 为底的指数，减去 1  
  
```  
inline float expm1f(float exponent) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `exponent`  
 指数项*n*的数学表达式`e` <sup>n</sup>，其中`e`是自然对数的底数。  
  
### <a name="return-value"></a>返回值  
 返回自变量的以 e 为底的指数，减去 1  
  
##  <a name="a-nameexpa--exp-function"></a><a name="exp"></a>exp 函数  
 计算以 e 为底的参数的指数  
  
```  
inline float exp(float _X) restrict(amp);

 
inline double exp(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以 e 为底的指数  
  
##  <a name="a-nameexpfa--expf-function"></a><a name="expf"></a>expf 函数  
 计算以 e 为底的参数的指数  
  
```  
inline float expf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以 e 为底的指数  
  
##  <a name="a-nameexp2a--exp2-function"></a><a name="exp2"></a>exp2 函数  
 计算&2; 为底的参数的指数  
  
```  
inline float exp2(float _X) restrict(amp);

 
inline double exp2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以&2; 为底的指数  
  
##  <a name="a-nameexp2fa--exp2f-function"></a><a name="exp2f"></a>exp2f 函数  
 计算&2; 为底的参数的指数  
  
```  
inline float exp2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以&2; 为底的指数  
  
##  <a name="a-namefabsa--fabs-function"></a><a name="fabs"></a>fabs 函数  
 返回参数的绝对值  
  
```  
inline float fabs(float _X) restrict(amp);

 
inline double fabs(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的绝对值  
  
##  <a name="a-namefabsfa--fabsf-function"></a><a name="fabsf"></a>fabsf 函数  
 返回参数的绝对值  
  
```  
inline float fabsf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的绝对值  

## <a name="a-namefdima-fdim-function"></a><a name="fdim"></a>fdim 函数  
计算参数之间的正数差异。
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
`_X`浮点值`_Y`浮点值


### <a name="return-value"></a>返回值
_X 和 _Y 如果 _X 大于 _Y; 之间的差异否则为 +&0;。
 
## <a name="a-namefdimfa-fdimf-function"></a><a name="fdimf"></a>fdimf 函数
计算参数之间的正数差异。
```
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```
### <a name="parameters"></a>参数
`_X`浮点值`_Y`浮点值

### <a name="return-value"></a>返回值
_X 和 _Y 如果 _X 大于 _Y; 之间的差异否则为 +&0;。 
  
##  <a name="a-namefloora--floor-function"></a><a name="floor"></a>floor 函数  
 计算参数的下限  
  
```  
inline float floor(float _X) restrict(amp);

 
inline double floor(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的下限  
  
##  <a name="a-namefloorfa--floorf-function"></a><a name="floorf"></a>floorf 函数  
 计算参数的下限  
  
```  
inline float floorf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的下限  

## <a name="a-namefma-fma-function"></a><a name="fma">fma 函数  
计算的积的第一个和第二个指定的参数，然后将第三个指定的参数添加到结果;作为单个操作执行整个计算。
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
`_X`第一个浮点参数。
`_Y`第二个浮点参数。
`_Z`第三个浮点参数。

### <a name="return-value"></a>返回值
该表达式的结果 (_X * _Y) + _Z。 作为单个操作; 执行整个计算也就是说，子表达式计算到无限精度和最终的结果将舍入。 

## <a name="a-namefmafa-fmaf-function"></a><a name="fmaf"></a>fmaf 函数  
计算的积的第一个和第二个指定的参数，然后将第三个指定的参数添加到结果;作为单个操作执行整个计算。
```
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```  
### <a name="parameters"></a>参数
`_X`第一个浮点参数。
`_Y`第二个浮点参数。
`_Z`第三个浮点参数。

### <a name="return-value"></a>返回值
该表达式的结果 (_X * _Y) + _Z。 作为单个操作; 执行整个计算也就是说，子表达式计算到无限精度和最终的结果将舍入。
  
##  <a name="a-namefmaxa--fmax-function"></a><a name="fmax"></a>fmax 函数  
 确定参数的最大数值  
  
```  
inline float fmax(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmax(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的最大数值  
  
##  <a name="a-namefmaxfa--fmaxf-function"></a><a name="fmaxf"></a>fmaxf 函数  
 确定参数的最大数值  
  
```  
inline float fmaxf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的最大数值  
  
##  <a name="a-namefmina--fmin-function"></a><a name="fmin"></a>fmin 函数  
 确定参数的最小数值  
  
```  
inline float fmin(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmin(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的最小数值  
  
##  <a name="a-namefminfa--fminf-function"></a><a name="fminf"></a>fminf 函数  
 确定参数的最小数值  
  
```  
inline float fminf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的最小数值  
  
##  <a name="a-namefmoda--fmod-function-c-amp"></a><a name="fmod"></a>fmod 函数 (c + + AMP)  
 计算除以第二个指定的参数的第一个指定参数的其余部分。  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);

 
inline double fmod(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 第一个浮点参数。  
  
 `_Y`  
 第二个浮点参数。  
  
### <a name="return-value"></a>返回值  
 其余部分`_X`除以`_Y`; 的值，即`_X`  -  `_Y` *n*，其中*n*是整数，以便程度`_X`  -  `_Y` *n*小于程度`_Y`。  
  
##  <a name="a-namefmodfa--fmodf-function"></a><a name="fmodf"></a>fmodf 函数  
 计算除以第二个指定的参数的第一个指定参数的其余部分。  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 第一个浮点参数。  
  
 `_Y`  
 第二个浮点参数。  
  
### <a name="return-value"></a>返回值  
 其余部分`_X`除以`_Y`; 的值，即`_X`  -  `_Y` *n*，其中*n*是整数，以便程度`_X`  -  `_Y` *n*小于程度`_Y`。  
  
##  <a name="a-namefpclassifya--fpclassify-function"></a><a name="fpclassify"></a>fpclassify 函数  
 将自变量值分类为 NaN、无穷大、正常、次正常、零  
  
```  
inline int fpclassify(float _X) restrict(amp);

 
inline int fpclassify(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回与自变量值相对应的数字分类宏的值。  
  
##  <a name="a-namefrexpa--frexp-function"></a><a name="frexp"></a>frexp 函数  
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
 `_X`  
 浮点值  
  
 `_Exp`  
 以浮点值形式返回 _X 的整数指数。  
  
### <a name="return-value"></a>返回值  
 返回尾数 _X  
  
##  <a name="a-namefrexpfa--frexpf-function"></a><a name="frexpf"></a>frexpf 函数  
 获取的尾数和 _X 的指数  
  
```  
inline float frexpf(
    float _X,  
    _Out_ int* _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Exp`  
 以浮点值形式返回 _X 的整数指数。  
  
### <a name="return-value"></a>返回值  
 返回尾数 _X  
  
##  <a name="a-namehypota--hypot-function"></a><a name="hypot"></a>hypot 函数  
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
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 和 _Y 平方和的平方根  
  
##  <a name="a-namehypotfa--hypotf-function"></a><a name="hypotf"></a>hypotf 函数  
 计算 _X 和 _Y 平方和的平方根  
  
```  
inline float hypotf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 和 _Y 平方和的平方根  
  
##  <a name="a-nameilogba--ilogb-function"></a><a name="ilogb"></a>ilogb 函数  
 以有符号整数值形式提取 _X 的指数  
  
```  
inline int ilogb(float _X) restrict(amp);

 
inline int ilogb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 以有符号整数值形式返回 _X 的指数  
  
##  <a name="a-nameilogbfa--ilogbf-function"></a><a name="ilogbf"></a>ilogbf 函数  
 以有符号整数值形式提取 _X 的指数  
  
```  
inline int ilogbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 以有符号整数值形式返回 _X 的指数  
  
##  <a name="a-nameisfinitea--isfinite-function"></a><a name="isfinite"></a>isfinite 函数  
 确定参数是否具有有限值  
  
```  
inline int isfinite(float _X) restrict(amp);

 
inline int isfinite(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 当且仅当自变量具有有限值时，返回一个非零值  
  
##  <a name="a-nameisinfa--isinf-function"></a><a name="isinf"></a>isinf 函数  
 确定参数是否为无穷大  
  
```  
inline int isinf(float _X) restrict(amp);

 
inline int isinf(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 当且仅当自变量具有无限值时，返回一个非零值  
  
##  <a name="a-nameisnana--isnan-function"></a><a name="isnan"></a>isnan 函数  
 确定参数是否为 NaN  
  
```  
inline int isnan(float _X) restrict(amp);

 
inline int isnan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 当且仅当自变量具有 NaN 值时，返回一个非零值  
  
##  <a name="a-nameisnormala--isnormal-function"></a><a name="isnormal"></a>isnormal 函数  
 确定自变量是否规范  
  
```  
inline int isnormal(float _X) restrict(amp);

 
inline int isnormal(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 当且仅当自变量具有规范值时，返回一个非零值  
  
##  <a name="a-nameldexpa--ldexp-function"></a><a name="ldexp"></a>ldexp 函数  
 计算指定的尾数和指数之间的实数。  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);

 
inline double ldexp(
    double _X,  
    double _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值尾数  
  
 `_Exp`  
 整数值指数  
  
### <a name="return-value"></a>返回值  
 返回 _X * 2 ^ _Exp  
  
##  <a name="a-nameldexpfa--ldexpf-function"></a><a name="ldexpf"></a>ldexpf 函数  
 计算指定的尾数和指数之间的实数。  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值尾数  
  
 `_Exp`  
 整数值指数  
  
### <a name="return-value"></a>返回值  
 返回 _X * 2 ^ _Exp  
  
##  <a name="a-namelgammaa--lgamma-function"></a><a name="lgamma"></a>lgamma 函数  
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
 `_X`  
 浮点值  
  
 `_Sign`  
 返回符号  
  
### <a name="return-value"></a>返回值  
 返回自变量伽玛绝对值的自然对数  
  
##  <a name="a-namelgammafa--lgammaf-function"></a><a name="lgammaf"></a>lgammaf 函数  
 计算自变量伽玛绝对值的自然对数  
  
```  
inline float lgammaf(
    float _X,  
    _Out_ int* _Sign) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Sign`  
 返回符号  
  
### <a name="return-value"></a>返回值  
 返回自变量伽玛绝对值的自然对数  
  
##  <a name="a-nameloga--log-function"></a><a name="log"></a>log 函数  
 计算参数的以 e 为底对数  
  
```  
inline float log(float _X) restrict(amp);

 
inline double log(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以 e 为底的对数  
  
##  <a name="a-namelog10a--log10-function"></a><a name="log10"></a>log10 函数  
 计算参数的以&10; 为基数的对数  
  
```  
inline float log10(float _X) restrict(amp);

 
inline double log10(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以&10; 为底的对数  
  
##  <a name="a-namelog10fa--log10f-function"></a><a name="log10f"></a>log10f 函数  
 计算参数的以&10; 为基数的对数  
  
```  
inline float log10f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以&10; 为底的对数  
  
##  <a name="a-namelog1pa--log1p-function"></a><a name="log1p"></a>log1p 函数  
 计算 1 加自变量的以 e 为底的对数  
  
```  
inline float log1p(float _X) restrict(amp);

 
inline double log1p(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 1加自变量的以 e 为底的对数  
  
##  <a name="a-namelog1pfa--log1pf-function"></a><a name="log1pf"></a>log1pf 函数  
 计算 1 加自变量的以 e 为底的对数  
  
```  
inline float log1pf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 1加自变量的以 e 为底的对数  
  
##  <a name="a-namelog2a--log2-function"></a><a name="log2"></a>log2 函数  
 计算参数的&2; 为底对数  
  
```  
inline float log2(float _X) restrict(amp);

 
inline double log2(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以&10; 为底的对数  
  
##  <a name="a-namelog2fa--log2f-function"></a><a name="log2f"></a>log2f 函数  
 计算参数的&2; 为底对数  
  
```  
inline float log2f(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以&10; 为底的对数  
  
##  <a name="a-namelogba--logb-function"></a><a name="logb"></a>logb 函数  
 以浮点格式的有符号整数值形式提取 _X 的指数  
  
```  
inline float logb(float _X) restrict(amp);

 
inline double logb(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的有符号指数  
  
##  <a name="a-namelogbfa--logbf-function"></a><a name="logbf"></a>logbf 函数  
 以浮点格式的有符号整数值形式提取 _X 的指数  
  
```  
inline float logbf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的有符号指数  
  
##  <a name="a-namelogfa--logf-function"></a><a name="logf"></a>logf 函数  
 计算参数的以 e 为底对数  
  
```  
inline float logf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量以 e 为底的对数  
  
##  <a name="a-namemodfa--modf-function"></a><a name="modf"></a>modf 函数  
 将拆分为小数部分组成的指定的参数和整数部分。  
  
```  
inline float modf(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);

 
inline double modf(
    double _X,  
    _Out_ double* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Iptr`（输出参数）  
 整数部分`_X`，浮点值。  
  
### <a name="return-value"></a>返回值  
 有符号小数部分`_X`。  
  
##  <a name="a-namemodffa--modff-function"></a><a name="modff"></a>modff 函数  
 将拆分为小数部分组成的指定的参数和整数部分。  
  
```  
inline float modff(
    float _X,  
    _Out_ float* _Iptr) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Iptr`  
 整数部分`_X`，浮点值。  
  
### <a name="return-value"></a>返回值  
 返回的有符号小数部分`_X`。  
  
##  <a name="a-namenana--nan-function"></a><a name="nan"></a>nan 函数  
 返回一个静态 NaN  
  
```  
inline double nan(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 如果可以，用 _X 中指示的内容返回静态 NaN  
  
##  <a name="a-namenanfa--nanf-function"></a><a name="nanf"></a>nanf 函数  
 返回一个静态 NaN  
  
```  
inline float nanf(int _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
### <a name="return-value"></a>返回值  
 如果可以，用 _X 中指示的内容返回静态 NaN  
  
##  <a name="a-namenearbyinta--nearbyint-function"></a><a name="nearbyint"></a>nearbyint 函数  
 通过使用当前舍入方向，将自变量舍入为浮点格式的整数值。  
  
```  
inline float nearbyint(float _X) restrict(amp);

 
inline double nearbyint(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回舍入后的整数值。  
  
##  <a name="a-namenearbyintfa--nearbyintf-function"></a><a name="nearbyintf"></a>nearbyintf 函数  
 通过使用当前舍入方向，将自变量舍入为浮点格式的整数值。  
  
```  
inline float nearbyintf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回舍入后的整数值。  
  
##  <a name="a-namenextaftera--nextafter-function"></a><a name="nextafter"></a>nextafter 函数  
 确定该函数的类型中的下一步可表示值之后 _Y 方向的 _X  
  
```  
inline float nextafter(
    float _X,  
    float _Y) restrict(amp);

 
inline double nextafter(
    double _X,  
    double _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 后 _X _Y 方向中的一种函数，返回下一个可表示值，  
  
##  <a name="a-namenextafterfa--nextafterf-function"></a><a name="nextafterf"></a>nextafterf 函数  
 确定该函数的类型中的下一步可表示值之后 _Y 方向的 _X  
  
```  
inline float nextafterf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 后 _X _Y 方向中的一种函数，返回下一个可表示值，  
  
##  <a name="a-namephia--phi-function"></a><a name="phi"></a>phi 函数  
 返回参数的累积分布函数  
  
```  
inline float phi(float _X) restrict(amp);

 
inline double phi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的累积分布函数  
  
##  <a name="a-namephifa--phif-function"></a><a name="phif"></a>phif 函数  
 返回参数的累积分布函数  
  
```  
inline float phif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的累积分布函数  
  
##  <a name="a-namepowa--pow-function"></a><a name="pow"></a>pow 函数  
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
 `_X`  
 浮点值，底数  
  
 `_Y`  
 浮点值，指数  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-namepowfa--powf-function"></a><a name="powf"></a>powf 函数  
 计算 _X 的 _Y 次幂  
  
```  
inline float powf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值，底数  
  
 `_Y`  
 浮点值，指数  
  
### <a name="return-value"></a>返回值  
  
##  <a name="a-nameprobita--probit-function"></a><a name="probit"></a>probit 函数  
 返回参数的反转累积分布函数  
  
```  
inline float probit(float _X) restrict(amp);

 
inline double probit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的反转累积分布函数  
  
##  <a name="a-nameprobitfa--probitf-function"></a><a name="probitf"></a>probitf 函数  
 返回参数的反转累积分布函数  
  
```  
inline float probitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的反转累积分布函数  
  
##  <a name="a-namercbrta--rcbrt-function"></a><a name="rcbrt"></a>rcbrt 函数  
 返回参数的立方根的倒数  
  
```  
inline float rcbrt(float _X) restrict(amp);

 
inline double rcbrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的立方根的倒数  
  
##  <a name="a-namercbrtfa--rcbrtf-function"></a><a name="rcbrtf"></a>rcbrtf 函数  
 返回参数的立方根的倒数  
  
```  
inline float rcbrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的立方根的倒数  
  
##  <a name="a-nameremaindera--remainder-function"></a><a name="remainder"></a>remainder 函数  
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
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X REM _Y  
  
##  <a name="a-nameremainderfa--remainderf-function"></a><a name="remainderf"></a>remainderf 函数  
 计算余数：_X REM _Y  
  
```  
inline float remainderf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X REM _Y  
  
##  <a name="a-nameremquoa--remquo-function"></a><a name="remquo"></a>remquo 函数  
 计算除以第二个指定的参数的第一个指定参数的其余部分。 此外计算除以第二个指定的参数的有效位数的第一个指定参数的有效位数的商，并返回商使用第三个参数中指定的位置。  
  
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
 `_X`  
 第一个浮点参数。  
  
 `_Y`  
 第二个浮点参数。  
  
 `_Quo`（输出参数）  
 一个整数，用于返回的小数位数的商的地址`_X`除以的小数部分位`_Y`。  
  
### <a name="return-value"></a>返回值  
 返回的其余部分`_X`除以`_Y`。  
  
##  <a name="a-nameremquofa--remquof-function"></a><a name="remquof"></a>remquof 函数  
 计算除以第二个指定的参数的第一个指定参数的其余部分。 此外计算除以第二个指定的参数的有效位数的第一个指定参数的有效位数的商，并返回商使用第三个参数中指定的位置。  
  
```  
inline float remquof(
    float _X,  
    float _Y,  
    _Out_ int* _Quo) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 第一个浮点参数。  
  
 `_Y`  
 第二个浮点参数。  
  
 `_Quo`（输出参数）  
 一个整数，用于返回的小数位数的商的地址`_X`除以的小数部分位`_Y`。  
  
### <a name="return-value"></a>返回值  
 返回的其余部分`_X`除以`_Y`。  
  
##  <a name="a-namerounda--round-function"></a><a name="round"></a>round 函数  
 将舍入为最接近整数的 _X  
  
```  
inline float round(float _X) restrict(amp);

 
inline double round(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回最接近 _X 的整数  
  
##  <a name="a-nameroundfa--roundf-function"></a><a name="roundf"></a>roundf 函数  
 将舍入为最接近整数的 _X  
  
```  
inline float roundf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回最接近 _X 的整数  
  
##  <a name="a-namersqrta--rsqrt-function"></a><a name="rsqrt"></a>rsqrt 函数  
 返回参数的平方根的倒数  
  
```  
inline float rsqrt(float _X) restrict(amp);

 
inline double rsqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的平方根的倒数  
  
##  <a name="a-namersqrtfa--rsqrtf-function"></a><a name="rsqrtf"></a>rsqrtf 函数  
 返回参数的平方根的倒数  
  
```  
inline float rsqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数的平方根的倒数  
  
##  <a name="a-namescalba--scalb-function"></a><a name="scalb"></a>scalb 函数  
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
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbfa--scalbf-function"></a><a name="scalbf"></a>scalbf 函数  
 用 _X 乘以 FLT_RADIX 的 _Y 次方  
  
```  
inline float scalbf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbna--scalbn-function"></a><a name="scalbn"></a>scalbn 函数  
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
 `_X`  
 浮点值  
  
 `_Y`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namescalbnfa--scalbnf-function"></a><a name="scalbnf"></a>scalbnf 函数  
 用 _X 乘以 FLT_RADIX 的 _Y 次方  
  
```  
inline float scalbnf(
    float _X,  
    int _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 整数值  
  
### <a name="return-value"></a>返回值  
 返回 _X * (FLT_RADIX ^ _Y)  
  
##  <a name="a-namesignbita--signbit-function"></a><a name="signbit"></a>signbit 函数  
 确定 _X 的符号是否为负号  
  
```  
inline int signbit(float _X) restrict(amp);

 
inline int signbit(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 当且仅当 _X 的符号为负号时，返回一个非零值  
  
##  <a name="a-namesignbitfa--signbitf-function"></a><a name="signbitf"></a>signbitf 函数  
 确定 _X 的符号是否为负号  
  
```  
inline int signbitf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 当且仅当 _X 的符号为负号时，返回一个非零值  
  
##  <a name="a-namesina--sin-function"></a><a name="sin"></a>sin 函数  
 计算参数的正弦值  
  
```  
inline float sin(float _X) restrict(amp);

 
inline double sin(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的正弦值  
  
##  <a name="a-namesinfa--sinf-function"></a><a name="sinf"></a>sinf 函数  
 计算参数的正弦值  
  
```  
inline float sinf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的正弦值  
  
##  <a name="a-namesincosa--sincos-function"></a><a name="sincos"></a>sincos 函数  
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
 `_X`  
 浮点值  
  
 `_S`  
 返回 _X 的正弦值  
  
 `_C`  
 返回 _X 的余弦值  
  
##  <a name="a-namesincosfa--sincosf-function"></a><a name="sincosf"></a>sincosf 函数  
 计算 _X 的正弦和余弦值  
  
```  
inline void sincosf(
    float _X,  
    _Out_ float* _S,  
    _Out_ float* _C) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_S`  
 返回 _X 的正弦值  
  
 `_C`  
 返回 _X 的余弦值  
  
##  <a name="a-namesinha--sinh-function"></a><a name="sinh"></a>sinh 函数  
 计算参数的双曲正弦值  
  
```  
inline float sinh(float _X) restrict(amp);

 
inline double sinh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的双曲正弦值  
  
##  <a name="a-namesinhfa--sinhf-function"></a><a name="sinhf"></a>sinhf 函数  
 计算参数的双曲正弦值  
  
```  
inline float sinhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的双曲正弦值  
  
##  <a name="a-namesinpia--sinpi-function"></a><a name="sinpi"></a>sinpi 函数  
 计算 pi * _X 的正弦值  
  
```  
inline float sinpi(float _X) restrict(amp);

 
inline double sinpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 pi * _X 的正弦值  
  
##  <a name="a-namesinpifa--sinpif-function"></a><a name="sinpif"></a>sinpif 函数  
 计算 pi * _X 的正弦值  
  
```  
inline float sinpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 pi * _X 的正弦值  
  
##  <a name="a-namesqrta--sqrt-function"></a><a name="sqrt"></a>sqrt 函数  
 计算自变量的平方根  
  
```  
inline float sqrt(float _X) restrict(amp);

 
inline double sqrt(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的平方根  
  
##  <a name="a-namesqrtfa--sqrtf-function"></a><a name="sqrtf"></a>sqrtf 函数  
 计算自变量的平方根  
  
```  
inline float sqrtf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的平方根  
  
##  <a name="a-nametana--tan-function"></a><a name="tan"></a>tan 函数  
 计算参数的正切值  
  
```  
inline float tan(float _X) restrict(amp);

 
inline double tan(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的正切值  
  
##  <a name="a-nametanfa--tanf-function"></a><a name="tanf"></a>tanf 函数  
 计算参数的正切值  
  
```  
inline float tanf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的正切值  
  
##  <a name="a-nametanha--tanh-function"></a><a name="tanh"></a>tanh 函数  
 计算参数的双曲正切值  
  
```  
inline float tanh(float _X) restrict(amp);

 
inline double tanh(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的双曲正切值  
  
##  <a name="a-nametanhfa--tanhf-function"></a><a name="tanhf"></a>tanhf 函数  
 计算参数的双曲正切值  
  
```  
inline float tanhf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的双曲正切值  
  
##  <a name="a-nametanpia--tanpi-function"></a><a name="tanpi"></a>tanpi 函数  
 计算 pi * _X 的正切值  
  
```  
inline float tanpi(float _X) restrict(amp);

 
inline double tanpi(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 pi * _X 的正切值  
  
##  <a name="a-nametanpifa--tanpif-function"></a><a name="tanpif"></a>tanpif 函数  
 计算 pi * _X 的正切值  
  
```  
inline float tanpif(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 pi * _X 的正切值  
  
##  <a name="a-nametgammaa--tgamma-function"></a><a name="tgamma"></a>tgamma 函数  
 计算 _X 的伽玛函数  
  
```  
inline float tgamma(float _X) restrict(amp);

 
inline double tgamma(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的伽玛函数的结果  
  
##  <a name="a-nametgammafa--tgammaf-function"></a><a name="tgammaf"></a>tgammaf 函数  
 计算 _X 的伽玛函数  
  
```  
inline float tgammaf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X 的伽玛函数的结果  
  
##  <a name="a-nametrunca--trunc-function"></a><a name="trunc"></a>trunc 函数  
 将截断的整数部分的参数  
  
```  
inline float trunc(float _X) restrict(amp);

 
inline double trunc(double _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的整数部分  
  
##  <a name="a-nametruncfa--truncf-function"></a><a name="truncf"></a>truncf 函数  
 将截断的整数部分的参数  
  
```  
inline float truncf(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的整数部分  
  
## <a name="see-also"></a>另请参阅  
 [Concurrency:: precise_math Namespace](concurrency-precise-math-namespace.md)

