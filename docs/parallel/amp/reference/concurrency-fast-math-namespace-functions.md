---
title: "Concurrency:: fast_math 命名空间函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5763d62-795b-4de6-a7a5-c7115f158708
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 4a01f48a7d087281ab1e9222d1077e92ab8b0d6c
ms.openlocfilehash: 0545a57c492f5c1872c71c04c99b54f86b644102
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencyfastmath-namespace-functions"></a>Concurrency:: fast_math 命名空间函数
||||  
|-|-|-|  
|[acos 函数](#acos)|[acosf 函数](#acosf)|[asin 函数](#asin)|  
|[asinf 函数](#asinf)|[atan 函数](#atan)|[atan2 函数](#atan2)|  
|[atan2f 函数](#atan2f)|[atanf 函数](#atanf)|[ceil 函数](#ceil)|  
|[ceilf 函数](#ceilf)|[cos 函数](#cos)|[cosf 函数](#cosf)|  
|[cosh 函数](#cosh)|[coshf 函数](#coshf)|[exp 函数](#exp)|  
|[exp2 函数](#exp2)|[exp2f 函数](#exp2f)|[expf 函数](#expf)|  
|[fabs 函数](#fabs)|[fabsf 函数](#fabsf)|[floor 函数](#floor)|  
|[floorf 函数](#floorf)|[fmax 函数](#fmax)|[fmaxf 函数](#fmaxf)|  
|[fmin 函数](#fmin)|[fminf 函数](#fminf)|[fmod 函数](#fmod)|  
|[fmodf 函数](#fmodf)|[frexp 函数](#frexp)|[frexpf 函数](#frexpf)|  
|[isfinite 函数](#isfinite)|[isinf 函数](#isinf)|[isnan 函数](#isnan)|  
|[ldexp 函数](#ldexp)|[ldexpf 函数](#ldexpf)|[log 函数](#log)|  
|[log10 函数](#log10)|[log10f 函数](#log10f)|[log2 函数](#log2)|  
|[log2f 函数](#log2f)|[logf 函数](#logf)|[modf 函数](#modf)|  
|[modff 函数](#modff)|[pow 函数](#pow)|[powf 函数](#powf)|  
|[round 函数](#round)|[roundf 函数](#roundf)|[rsqrt 函数](#rsqrt)|  
|[rsqrtf 函数](#rsqrtf)|[signbit 函数](#signbit)|[signbitf 函数](#signbitf)|  
|[sin 函数](#sin)|[sincos 函数](#sincos)|[sincosf 函数](#sincosf)|  
|[sinf 函数](#sinf)|[sinh 函数](#sinh)|[sinhf 函数](#sinhf)|  
|[sqrt 函数](#sqrt)|[sqrtf 函数](#sqrtf)|[tan 函数](#tan)|  
|[tanf 函数](#tanf)|[tanh 函数](#tanh)|[tanhf 函数](#tanhf)|  
|[trunc 函数](#trunc)|[truncf 函数](#truncf)|  
  
##  <a name="a-nameacosa--acos-function"></a><a name="acos"></a>acos 函数  
 计算参数的反余弦值  
  
```  
inline float acos(float _X) restrict(amp);
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
  
##  <a name="a-nameasina--asin-function"></a><a name="asin"></a>asin 函数  
 计算参数的反正弦值  
  
```  
inline float asin(float _X) restrict(amp);
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
  
##  <a name="a-nameatana--atan-function"></a><a name="atan"></a>atan 函数  
 计算参数的反正切值  
  
```  
inline float atan(float _X) restrict(amp);
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
  
##  <a name="a-nameceila--ceil-function"></a><a name="ceil"></a>ceil 函数  
 计算参数的上限  
  
```  
inline float ceil(float _X) restrict(amp);
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
  
##  <a name="a-namecosa--cos-function"></a><a name="cos"></a>cos 函数   
 计算参数的余弦值  
  
```  
inline float cos(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回自变量的反双曲余弦值  
  
##  <a name="a-nameexpa--exp-function"></a><a name="exp"></a>exp 函数  
 计算以 e 为底的参数的指数  
  
```  
inline float exp(float _X) restrict(amp);
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
  
##  <a name="a-namefabsa--fabs-function"></a><a name="fabs"></a>fabs 函数  
 返回参数的绝对值  
  
```  
inline float fabs(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
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
  
##  <a name="a-namefloora--floor-function"></a><a name="floor"></a>floor 函数  
 计算参数的下限  
  
```  
inline float floor(float _X) restrict(amp);
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
  
##  <a name="a-namefmaxa--fmax-function"></a><a name="fmax"></a>fmax 函数  
 确定参数的最大数值  
  
```  
inline float max(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
 `_Y`  
 整数值  
  
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
inline float min(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 整数值  
  
 `_Y`  
 整数值  
  
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
  
##  <a name="a-namefmoda--fmod-function"></a><a name="fmod"></a>fmod 函数  
 计算 _X/_Y 的浮点余数  
  
```  
inline float fmod(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X/_Y 的浮点余数  
  
##  <a name="a-namefmodfa--fmodf-function"></a><a name="fmodf"></a>fmodf 函数  
 计算 _X/_Y 的浮点余数。  
  
```  
inline float fmodf(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Y`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回 _X/_Y 的浮点余数  
  
##  <a name="a-namefrexpa--frexp-function"></a><a name="frexp"></a>frexp 函数  
 获取的尾数和 _X 的指数  
  
```  
inline float frexp(
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
  
##  <a name="a-nameisfinitea--isfinite-function"></a><a name="isfinite"></a>isfinite 函数  
 确定参数是否具有有限值  
  
```  
inline int isfinite(float _X) restrict(amp);
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
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 当且仅当自变量具有 NaN 值时，返回一个非零值  
  
##  <a name="a-nameldexpa--ldexp-function"></a><a name="ldexp"></a>ldexp 函数  
 将实数从尾数和指数计算  
  
```  
inline float ldexp(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值，尾数  
  
 `_Exp`  
 整数指数  
  
### <a name="return-value"></a>返回值  
 返回 _X * 2 ^ _Exp  
  
##  <a name="a-nameldexpfa--ldexpf-function"></a><a name="ldexpf"></a>ldexpf 函数  
 将实数从尾数和指数计算  
  
```  
inline float ldexpf(
    float _X,  
    int _Exp) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值，尾数  
  
 `_Exp`  
 整数指数  
  
### <a name="return-value"></a>返回值  
 返回 _X * 2 ^ _Exp  
  
##  <a name="a-nameloga--log-function"></a><a name="log"></a>log 函数  
 计算参数的以 e 为底对数  
  
```  
inline float log(float _X) restrict(amp);
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
  
##  <a name="a-namelog2a--log2-function"></a><a name="log2"></a>log2 函数  
 计算参数的&2; 为底对数  
  
```  
inline float log2(float _X) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
### <a name="return-value"></a>返回值  
 返回参数&2; 为底的对数  
  
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
 将拆分到小数的 _X 和整数部分。  
  
```  
inline float modf(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Ip`  
  
### <a name="return-value"></a>返回值  
 返回 _X 的有符号小数部分。  
  
##  <a name="a-namemodffa--modff-function"></a><a name="modff"></a>modff 函数  
 将拆分到小数的 _X 和整数部分。  
  
```  
inline float modff(
    float _X,  
    float* _Ip) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值  
  
 `_Ip`  
  
### <a name="return-value"></a>返回值  
 返回 _X 的有符号小数部分。  
  
##  <a name="a-namepowa--pow-function"></a><a name="pow"></a>pow 函数  
 计算 _X 的 _Y 次幂  
  
```  
inline float pow(
    float _X,  
    float _Y) restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_X`  
 浮点值，底数  
  
 `_Y`  
 浮点值，指数  
  
### <a name="return-value"></a>返回值  
 返回 _X 的 _Y 次幂的值  
  
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
  
##  <a name="a-namerounda--round-function"></a><a name="round"></a>round 函数  
 将舍入为最接近整数的 _X  
  
```  
inline float round(float _X) restrict(amp);
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
  
##  <a name="a-namesignbita--signbit-function"></a><a name="signbit"></a>signbit 函数  
 确定 _X 的符号是否为负号  
  
```  
inline int signbit(float _X) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
    float* _S,  
    float* _C) restrict(amp);
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
  
##  <a name="a-namesqrta--sqrt-function"></a><a name="sqrt"></a>sqrt 函数  
 计算自变量的平方根  
  
```  
inline float sqrt(float _X) restrict(amp);
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
  
##  <a name="a-nametrunca--trunc-function"></a><a name="trunc"></a>trunc 函数  
 将截断的整数部分的参数  
  
```  
inline float trunc(float _X) restrict(amp);
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
 [Concurrency:: fast_math Namespace](concurrency-fast-math-namespace.md)

