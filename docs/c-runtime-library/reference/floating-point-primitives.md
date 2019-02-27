---
title: 浮点基元
ms.date: 01/31/2019
apiname:
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
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 230d0def145bcb443437b59303b2b36e348da2bb
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703418"
---
# <a name="floating-point-primitives"></a>浮点基元

特定于 Microsoft 的用于实现一些标准 C 运行时库 (CRT) 浮点函数的基元函数。 它们为了保持完整性，此处记录，但不建议使用。 这些函数的一些标记为未使用，因为已知这些具有精度、 异常处理和符合 IEEE-754 行为中的问题。 它们仅用于向后兼容性的库中存在。 有关正确的行为、 可移植性和遵从标准，首选标准的浮点函数，而这些函数。

## <a name="dclass-ldclass-fdclass"></a>_dclass，_ldclass _fdclass

### <a name="syntax"></a>语法

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数自变量。

### <a name="remarks"></a>备注

这些浮点基元实现 C 版本的 CRT 宏[fpclassify](fpclassify.md)对浮点类型。 自变量的分类*x*返回作为在 math.h 中定义以下常量之一：

|“值”|描述|
|-----------|-----------------|
| **FP_NAN** | 静态、信令或不确定的 NaN |
| **FP_INFINITE** | 正或负无穷大 |
| **FP_NORMAL** | 标准化非零正值或负值 |
| **FP_SUBNORMAL** | 正或负次正常的 （非规范化） 值 |
| **FP_ZERO** | 零正值或负值 |

更多详细信息，可以使用 Microsoft 专用[_fpclass、 _fpclassf](fpclass-fpclassf.md)函数。 使用[fpclassify](fpclassify.md)宏或函数的可移植性。

## <a name="dsign-ldsign-fdsign"></a>_dsign，_ldsign _fdsign

### <a name="syntax"></a>语法

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数自变量。

### <a name="remarks"></a>备注

这些浮点基元实现[signbit](signbit.md)宏或 CRT 中的函数。 它们返回一个非零值，如果在自变量的有效位数 （尾数） 中设置符号位*x*，如果未设置符号位为 0。

## <a name="dpcomp-ldpcomp-fdpcomp"></a>_dpcomp，_ldpcomp _fdpcomp

### <a name="syntax"></a>语法

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>参数

*x*， *y*<br/>
浮点函数自变量。

### <a name="remarks"></a>备注

这些浮点基元不采用两个自变量*x*并*y*，并返回一个值，显示了其排序的关系，表示为按位或两个常数，在 math.h 中定义的：

| 值 | 描述 |
|------------|-----------------|
| **_FP_LT** | *x*可被视为小于*y* |
| **_FP_EQ** | *x*可被视为等于*y* |
| **_FP_GT** | *x*可被视为大于*y* |

这些基元实现[isgreater，isgreaterequal，isless，islessequal，islessgreater，和 isunordered](floating-point-ordering.md)宏和 CRT 中的函数。

## <a name="dtest-ldtest-fdtest"></a>_dtest，_ldtest _fdtest

### <a name="syntax"></a>语法

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>参数

*px*<br/>
浮点型参数指向的指针。

### <a name="remarks"></a>备注

这些浮点基元实现 c + + 版本的 CRT 函数[fpclassify](fpclassify.md)对浮点类型。 自变量*x*计算和分类将作为在 math.h 中定义以下常量之一：

|“值”|描述|
|-----------|-----------------|
| **FP_NAN** | 静态、信令或不确定的 NaN |
| **FP_INFINITE** | 正或负无穷大 |
| **FP_NORMAL** | 标准化非零正值或负值 |
| **FP_SUBNORMAL** | 正或负次正常的 （非规范化） 值 |
| **FP_ZERO** | 零正值或负值 |

更多详细信息，可以使用 Microsoft 专用[_fpclass、 _fpclassf](fpclass-fpclassf.md)函数。 使用[fpclassify](fpclassify.md)函数的可移植性。

## <a name="dint-ldint-fdint"></a>_d_int，_ld_int _fd_int

### <a name="syntax"></a>语法

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>参数

*px*<br/>
浮点型参数指向的指针。

*exp*<br/>
作为一种整型类型的一个指数。

### <a name="remarks"></a>备注

这些浮点基元采用指向浮点值的*px*和指数值*exp*，并在可能的情况中删除给定的指数，下面的浮点值的小数部分. 返回的值是结果**fpclassify**中的输入值*px*如果它是 NaN 或无穷大，和中的输出值*px*否则为。

## <a name="dscale-ldscale-fdscale"></a>_dscale，_ldscale _fdscale

### <a name="syntax"></a>语法

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>参数

*px*<br/>
浮点型参数指向的指针。

*exp*<br/>
作为一种整型类型的一个指数。

### <a name="remarks"></a>备注

这些浮点基元采用指向浮点值的*px*和指数值*exp*，并扩展中的值*px* 2<sup> *exp*</sup>如有可能。 返回的值是结果**fpclassify**中的输入值*px*如果它是 NaN 或无穷大，和中的输出值*px*否则为。 对于可移植性，更喜欢[ldexp、 ldexpf、 ldexpl 和](ldexp.md)函数。

## <a name="dunscale-ldunscale-fdunscale"></a>_dunscale，_ldunscale _fdunscale

### <a name="syntax"></a>语法

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>参数

*pexp*<br/>
指向一个指数为整型类型的指针。

*px*<br/>
浮点型参数指向的指针。

### <a name="remarks"></a>备注

这些浮点基元将指向的浮点值分解*px*到有效位数 （尾数） 和一个指数，在可能的情况。 有效数字进行缩放以便绝对值的数值是大于或等于 0.5 且小于 1.0。 指数为值*n*，其中原始浮点值等于 2 次缩放的有效数字<sup>*n*</sup>。 此整数指数*n*指向的位置处存储*pexp*。 返回的值是结果**fpclassify**中的输入值*px*是否 NaN 或无穷大，否则为输出值。 对于可移植性，更喜欢[frexp、 frexpf、 frexpl](frexp.md)函数。

## <a name="dexp-ldexp-fdexp"></a>_dexp，_ldexp _fdexp

### <a name="syntax"></a>语法

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>参数

*y*<br/>
浮点函数自变量。

*px*<br/>
浮点型参数指向的指针。

*exp*<br/>
作为一种整型类型的一个指数。

### <a name="remarks"></a>备注

这些浮点基元构造由指向的位置中的浮点值*px*等于*y* * 2<sup>*exp*</sup>。 返回的值是结果**fpclassify**中的输入值*y*如果它是 NaN 或无穷大，和中的输出值*px*否则为。 对于可移植性，更喜欢[ldexp、 ldexpf、 ldexpl 和](ldexp.md)函数。

## <a name="dnorm-fdnorm"></a>_dnorm _fdnorm

### <a name="syntax"></a>语法

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>参数

*ps*<br/>
指向数组的形式表示的浮点值的按位表示形式**无符号** **短**。

### <a name="remarks"></a>备注

这些浮点基元规范化 underflowed 的浮点值的小数部分和调整*特征*，或有偏差的指数，以匹配。 值作为的按位表示浮点类型转换为数组的形式传递**无符号** **短**通过`_double_val`， `_ldouble_val`，或`_float_val`类型punning 联合声明在 math.h 中。 返回值是结果**fpclassify**和上的输入的浮点值，如果它是 NaN 或无穷大，否则为输出值。

## <a name="dpoly-ldpoly-fdpoly"></a>_dpoly，_ldpoly _fdpoly

### <a name="syntax"></a>语法

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数自变量。

*table*<br/>
指向常量系数多项式的次数的表。

*n*<br/>
若要评估多项式的顺序。

### <a name="remarks"></a>备注

这些浮点基元返回的评估*x*中的顺序多项式*n*中相应的常量值由表示其系数*表*. 例如，如果*表*\[0] = 3.0*表*\[1] = 4.0，*表*\[2] = 5.0，和*n*= 2，它表示多项式 5.0 x<sup>2</sup> + 4.0 x + 3.0。 如果此多项式的次数的计算结果为*x* 2.0 中，结果是 31.0。 这些函数不是在内部使用。

## <a name="dlog-dlog-dlog"></a>_dlog，_dlog _dlog

### <a name="syntax"></a>语法

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数自变量。

*base_flag*<br/>
标志，用于控制要使用 0 表示基本的基础*e*和非零值的基数为 10。

### <a name="remarks"></a>备注

这些浮点基元返回的自然对数*x*，ln (*x*) 或日志<sub>*e*</sub>(*x*)，当*base_flag*为 0。 它们返回日志的基数为 10 *x*，或日志<sub>10</sub>(*x*)，当*base_flag*不为零。 这些函数不是在内部使用。 对于可移植性，更喜欢函数[日志、 logf、 logl、 log10、 log10f 和 log10l](log-logf-log10-log10f.md)。

## <a name="dsin-ldsin-fdsin"></a>_dsin，_ldsin _fdsin

### <a name="syntax"></a>语法

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点函数自变量。

*quadrant*<br/>
象限偏移量为 0、 1、 2 或 3 使用来生成`sin`， `cos`， `-sin`，和`-cos`结果。

### <a name="remarks"></a>备注

这些浮点基元返回的正弦*x*的偏移量*象限*对 4 取模。 实际上，它们返回正弦、 余弦、 正弦值，和-的余弦值*x*时*象限*对 4 取模是 0、 1、 2 或 3，分别。 这些函数不是在内部使用。 对于可移植性，更喜欢[sin、 sinf、 sinl](sin-sinf-sinl.md)， [cos、 cosf、 cosl 和](cos-cosf-cosl.md)函数。

## <a name="requirements"></a>要求

标头： \<math.h >

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite，_finite、 _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[frexp、frexpf、frexpl](frexp.md)<br/>
[ldexp、 ldexpf、 ldexpl](ldexp.md)<br/>
[log、logf、logl、log10、log10f、log10l](log-logf-log10-log10f.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
