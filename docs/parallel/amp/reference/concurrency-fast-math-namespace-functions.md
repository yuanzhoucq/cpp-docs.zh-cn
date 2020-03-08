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
ms.openlocfilehash: 3652e02d9f3ff7b09ee7334dba20188e40344cb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865465"
---
# <a name="concurrencyfast_math-namespace-functions"></a>Concurrency::fast_math 命名空间函数

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[asin](#asin)|
|[asinf](#asinf)|[atan](#atan)|[atan2](#atan2)|
|[atan2f](#atan2f)|[atanf](#atanf)|[ceil](#ceil)|
|[ceilf](#ceilf)|[cos](#cos)|[cosf](#cosf)|
|[cosh](#cosh)|[coshf](#coshf)|[exp](#exp)|
|[exp2](#exp2)|[exp2f](#exp2f)|[expf](#expf)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[floorf](#floorf)|[fmax](#fmax)|[fmaxf](#fmaxf)|
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[frexp](#frexp)|[frexpf](#frexpf)|
|[isfinite](#isfinite)|[isinf](#isinf)|[isnan](#isnan)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[log](#log)|
|[log10](#log10)|[log10f](#log10f)|[log2](#log2)|
|[log2f](#log2f)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[pow](#pow)|[powf](#powf)|
|[round](#round)|[roundf](#roundf)|[rsqrt](#rsqrt)|
|[rsqrtf](#rsqrtf)|[signbit](#signbit)|[signbitf](#signbitf)|
|[sin](#sin)|[sincos](#sincos)|[sincosf](#sincosf)|
|[sinf](#sinf)|[sinh](#sinh)|[sinhf](#sinhf)|
|[sqrt](#sqrt)|[sqrtf](#sqrtf)|[tan](#tan)|
|[tanf](#tanf)|[tanh](#tanh)|[tanhf](#tanhf)|
|[trunc](#trunc)|[truncf](#truncf)|

## <a name="acos"></a>acos

计算参数的反余弦

```cpp
inline float acos(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反余弦值

## <a name="acosf"></a>acosf

计算参数的反余弦

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的反余弦值

## <a name="asin"></a>  asin

计算参数的反正弦

```cpp
inline float asin(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正弦值

## <a name="asinf"></a>asinf

计算参数的反正弦

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正弦值

## <a name="atan"></a>  atan

计算参数的反正切值

```cpp
inline float atan(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正切值

## <a name="atan2"></a>  atan2

计算 _Y/_X 的反正切值

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

## <a name="atan2f"></a>atan2f

计算 _Y/_X 的反正切值

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

## <a name="atanf"></a>atanf

计算参数的反正切值

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反正切值

## <a name="ceil"></a>ceil

计算参数的上限

```cpp
inline float ceil(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的上限

## <a name="ceilf"></a>ceilf

计算参数的上限

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的上限

## <a name="cosf"></a>cosf

计算参数的余弦值

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的余弦值

## <a name="coshf"></a>coshf

计算参数的双曲余弦值

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反双曲余弦值

## <a name="cos"></a>  cos

计算参数的余弦值

```cpp
inline float cos(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的余弦值

## <a name="cosh"></a>  cosh

计算参数的双曲余弦值

```cpp
inline float cosh(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的反双曲余弦值

## <a name="exp"></a>  exp

计算自变量的以 e 为底的指数

```cpp
inline float exp(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的指数

## <a name="exp2"></a>exp2

计算参数的以2为底的指数

```cpp
inline float exp2(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的以 2 为底的幂

## <a name="exp2f"></a>exp2f

计算参数的以2为底的指数

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的以 2 为底的幂

## <a name="expf"></a>expf

计算自变量的以 e 为底的指数

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的指数

## <a name="fabs"></a>fabs

返回参数的绝对值。

```cpp
inline float fabs(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
整数值

### <a name="return-value"></a>返回值

返回参数的绝对值。

## <a name="fabsf"></a>fabsf

返回参数的绝对值。

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的绝对值。

## <a name="floor"></a>突破

计算参数的下限

```cpp
inline float floor(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的下限

## <a name="floorf"></a>floorf

计算参数的下限

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的下限

## <a name="fmax"></a>fmax

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

## <a name="fmaxf"></a>fmaxf

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

## <a name="fmin"></a>fmin

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

## <a name="fminf"></a>fminf

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

## <a name="fmod"></a>fmod

计算 _X/_Y 的浮点余数

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

## <a name="fmodf"></a>fmodf

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

## <a name="frexp"></a>frexp

获取 _X 的尾数和指数

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

## <a name="frexpf"></a>frexpf

获取 _X 的尾数和指数

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

## <a name="isfinite"></a>isfinite

确定参数是否具有有限值

```cpp
inline int isfinite(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有有限值时，返回一个非零值

## <a name="isinf"></a>isinf

确定参数是否为无穷

```cpp
inline int isinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有无限值时，返回一个非零值

## <a name="isnan"></a>isnan

确定参数是否为 NaN

```cpp
inline int isnan(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当自变量具有 NaN 值时，返回一个非零值

## <a name="ldexp"></a>ldexp

从尾数和指数计算实数

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

返回 _X \* 2 ^ _Exp

## <a name="ldexpf"></a>ldexpf

从尾数和指数计算实数

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

返回 _X \* 2 ^ _Exp

## <a name="log"></a>  log

计算自变量的以 e 为底的对数

```cpp
inline float log(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的对数

## <a name="log10"></a>  log10

计算自变量的以10为底的对数

```cpp
inline float log10(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

## <a name="log10f"></a>log10f

计算自变量的以10为底的对数

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

## <a name="log2"></a>log2

计算参数的以2为底的对数

```cpp
inline float log2(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的以2为底的对数

## <a name="log2f"></a>log2f

计算参数的以2为底的对数

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 10 为底的对数

## <a name="logf"></a>logf

计算自变量的以 e 为底的对数

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量以 e 为底的对数

## <a name="modf"></a>modf

将 _X 拆分为小数部分和整数部分。

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

## <a name="modff"></a>modff

将 _X 拆分为小数部分和整数部分。

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

## <a name="pow"></a>  pow

计算 _X 的次幂 _Y

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

返回 _X 的 _Y 的幂的值

## <a name="powf"></a>powf

计算 _X 的次幂 _Y

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

## <a name="round"></a>圆满

将 _X 舍入到最接近的整数

```cpp
inline float round(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回最接近 _X 的整数

## <a name="roundf"></a>roundf

将 _X 舍入到最接近的整数

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回最接近 _X 的整数

## <a name="rsqrt"></a>rsqrt

返回参数平方根的倒数

```cpp
inline float rsqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数平方根的倒数

## <a name="rsqrtf"></a>rsqrtf

返回参数平方根的倒数

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数平方根的倒数

## <a name="signbit"></a>signbit

确定 _X 的符号是否为负号

```cpp
inline int signbit(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当 _X 的符号为负号时，返回一个非零值

## <a name="signbitf"></a>signbitf

确定 _X 的符号是否为负号

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

当且仅当 _X 的符号为负号时，返回一个非零值

## <a name="sin"></a>  sin

计算参数的正弦值

```cpp
inline float sin(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正弦值

## <a name="sinf"></a>sinf

计算参数的正弦值

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正弦值

## <a name="sincos"></a>sincos

计算 _X 的正弦值和余弦值

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

## <a name="sincosf"></a>sincosf

计算 _X 的正弦值和余弦值

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

## <a name="sinh"></a>  sinh

计算参数的双曲正弦值

```cpp
inline float sinh(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正弦值

## <a name="sinhf"></a>sinhf

计算参数的双曲正弦值

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正弦值

## <a name="sqrt"></a>  sqrt

计算参数的平方根

```cpp
inline float sqrt(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根

## <a name="sqrtf"></a>sqrtf

计算参数的平方根

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的平方根

## <a name="tan"></a>  tan

计算参数的正切值

```cpp
inline float tan(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正切值

## <a name="tanf"></a>tanf

计算参数的正切值

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的正切值

## <a name="tanh"></a>  tanh

计算参数的双曲正切值

```cpp
inline float tanh(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正切值

## <a name="tanhf"></a>tanhf

计算参数的双曲正切值

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回参数的双曲正切值

## <a name="trunc"></a>trunc

将参数截断为整数组件

```cpp
inline float trunc(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的整数部分

## <a name="truncf"></a>truncf

将参数截断为整数组件

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>参数

*_X*<br/>
浮点值

### <a name="return-value"></a>返回值

返回自变量的整数部分

## <a name="requirements"></a>要求

**标头：** Amp_math**命名空间：** Concurrency：： fast_math

## <a name="see-also"></a>另请参阅

[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)
