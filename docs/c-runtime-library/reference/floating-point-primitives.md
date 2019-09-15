---
title: 浮点基元
ms.date: 01/31/2019
api_name:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: 25d70062a76f9c32692f5df3f7abb96b49892725
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957163"
---
# <a name="floating-point-primitives"></a>浮点基元

用于实现某些标准 C 运行时库（CRT）浮点函数的特定于 Microsoft 的基元函数。 为了完整起见，我们记录了这些内容，但不建议使用。 其中一些函数被记录为 "未使用"，因为已知这些函数的精度、异常处理和一致性均为 IEEE-754 行为。 它们仅用于向后兼容性。 若要获得正确的行为、可移植性和符合标准，更喜欢这些函数的标准浮点函数。

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>语法

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数参数。

### <a name="remarks"></a>备注

这些浮点基元实现适用于浮点类型的 CRT 宏[fpclassify](fpclassify.md)的 C 版本。 自变量*x*的分类作为以下常量之一返回：在 math 中定义：

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 静态、信令或不确定的 NaN |
| **FP_INFINITE** | 正或负无穷大 |
| **FP_NORMAL** | 标准化非零正值或负值 |
| **FP_SUBNORMAL** | 正或负次正常（非规范化）值 |
| **FP_ZERO** | 零正值或负值 |

有关更多详细信息，可以使用 Microsoft 特定的[_fpclass，_fpclassf](fpclass-fpclassf.md)函数。 使用[fpclassify](fpclassify.md)宏或函数实现可移植性。

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>语法

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数参数。

### <a name="remarks"></a>备注

这些浮点基元实现了 CRT 中的[signbit](signbit.md)宏或函数。 如果在参数*x*的有效位数（尾数）中设置了符号位，则它们将返回非零值; 如果未设置符号位，则返回0。

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>语法

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>参数

*x*、 *y*<br/>
浮点函数自变量。

### <a name="remarks"></a>备注

这些浮点基元采用两个参数*x*和*y*，并返回一个值，该值显示其顺序关系，表示为在 math 中定义的常量的按位 or。

| 值 | 描述 |
|------------|-----------------|
| **_FP_LT** | *x*可以视为小于*y* |
| **_FP_EQ** | *x*可以视为等于*y* |
| **_FP_GT** | *x*可以视为大于*y* |

这些基元实现了 CRT 中的[isgreater、isgreaterequal、isless、islessequal、islessgreater 和 isunordered](floating-point-ordering.md)宏和函数。

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>语法

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>参数

*px*<br/>
指向浮点自变量的指针。

### <a name="remarks"></a>备注

这些浮点基元实现适用于浮点C++类型的 CRT 函数[fpclassify](fpclassify.md)的版本。 计算参数*x* ，并以 math 定义的常量之一返回分类：

|值|描述|
|-----------|-----------------|
| **FP_NAN** | 静态、信令或不确定的 NaN |
| **FP_INFINITE** | 正或负无穷大 |
| **FP_NORMAL** | 标准化非零正值或负值 |
| **FP_SUBNORMAL** | 正或负次正常（非规范化）值 |
| **FP_ZERO** | 零正值或负值 |

有关更多详细信息，可以使用 Microsoft 特定的[_fpclass，_fpclassf](fpclass-fpclassf.md)函数。 使用[fpclassify](fpclassify.md)函数实现可移植性。

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>语法

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>参数

*px*<br/>
指向浮点自变量的指针。

*exp*<br/>
整数类型的指数。

### <a name="remarks"></a>备注

这些浮点基元采用指向浮点值*px*和指数值*exp*的指针，并在可能的情况下删除浮点值下的浮点值的小数部分。 返回的值为**fpclassify**中输入值的结果 *，如果该值*为 NaN 或无穷大，则为 px 的输出值，否则为*px*的输出值。

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>语法

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>参数

*px*<br/>
指向浮点自变量的指针。

*exp*<br/>
整数类型的指数。

### <a name="remarks"></a>备注

这些浮点基元采用指向浮点值*px*和指数值*exp*的指针，并在可能的情况下将*px*中的值缩放2个<sup>*exp*</sup>。 返回的值为**fpclassify**中输入值的结果 *，如果该值*为 NaN 或无穷大，则为 px 的输出值，否则为*px*的输出值。 对于可移植性，更倾向于[ldexp、ldexpf 和 ldexpl](ldexp.md)函数。

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>语法

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>参数

*pexp*<br/>
作为整型的指针。

*px*<br/>
指向浮点自变量的指针。

### <a name="remarks"></a>备注

如果可能，这些浮点基元会将*px*指向的浮点值分解为有效位数（尾数）和指数。 缩放有效位数，使绝对值大于或等于0.5 且小于1.0。 指数是值*n*，其中原始浮点值等于按比例缩放的有效位数时间 2<sup>*n*</sup>。 此整数指数*n*存储在*pexp*所指向的位置。 *如果输入*值为 NaN 或无穷大，则返回的值为**fpclassify**的结果，否则返回。 对于可移植性，更倾向于[frexp、frexpf、frexpl](frexp.md)函数。

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>语法

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>参数

*y*<br/>
浮点函数参数。

*px*<br/>
指向浮点自变量的指针。

*exp*<br/>
整数类型的指数。

### <a name="remarks"></a>备注

这些浮点基元在 x 等于*y* * 2<sup>*exp*</sup>*的位置*上构造浮点值。 返回的值为**fpclassify**中输入值的结果 *，如果该值*为 NaN 或无穷大，则返回值; 否则为*px*的输出值。 对于可移植性，更倾向于[ldexp、ldexpf 和 ldexpl](ldexp.md)函数。

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>语法

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>参数

*ps*<br/>
指向数组的形式表示的浮点值的按位表示形式**无符号** **短**。

### <a name="remarks"></a>备注

这些浮点基元标准化下溢浮点值的小数部分，并调整*特征*或偏差指数以进行匹配。 值作为的按位表示浮点类型转换为数组的形式传递**无符号** **短**通过`_double_val`， `_ldouble_val`，或`_float_val`类型punning 联合声明在 math.h 中。 如果输入浮点值为 NaN 或无穷大，则返回值为**fpclassify**的结果，否则返回值为。

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>语法

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数参数。

*table*<br/>
指向多项式的常量系数表的指针。

*n*<br/>
计算多项式的顺序。

### <a name="remarks"></a>备注

这些浮点基元返回按顺序*n*的多项式计算*x*的计算，其系数由*表*中的相应常量值表示。 例如，如果*表*\[0] = 3.0，*表*\[1] = 4.0，*表*\[2] = 5.0， *n* = 2，则表示多项式 5.0 x<sup>2</sup> + 4.0 x + 3.0。 如果对*x*的2.0 计算此多项式，则结果为31.0。 这些函数不在内部使用。

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>语法

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数参数。

*base_flag*<br/>
用于控制要使用的基准的标志，0表示 base *e* ，0表示基数10。

### <a name="remarks"></a>备注

当*base_flag*为0时，这些浮点基元返回*x*、ln （*x*）或 log<sub>*e*</sub>（*x*）的自然对数。 如果*base_flag*为非零，则它们返回*x*的对数基数10，或日志<sub>10</sub>（*x*）。 这些函数不在内部使用。 对于可移植性，建议使用函数[log、logf、logl、log10、log10f 和 log10l](log-logf-log10-log10f.md)。

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>语法

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数参数。

*quadrant*<br/>
要用于生成`sin`、 `cos`、 `-sin`和`-cos`结果的象限偏移量（0、1、2或3）。

### <a name="remarks"></a>备注

这些浮点基元返回*象限*取模4的*x*偏移量的正弦值。 实际上，当*象限*取模4分别为0、1、2或3时，它们会返回*x*的正弦、余弦、正弦和-余弦值。 这些函数不在内部使用。 对于可移植性，更喜欢使用[sin、sinf、sinl](sin-sinf-sinl.md)、 [cos、cosf 和 cosl](cos-cosf-cosl.md)函数。

## <a name="requirements"></a>要求

标头\<： math >

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[frexp、frexpf、frexpl](frexp.md)<br/>
[ldexp、ldexpf 和 ldexpl](ldexp.md)<br/>
[log、logf、logl、log10、log10f、log10l](log-logf-log10-log10f.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
