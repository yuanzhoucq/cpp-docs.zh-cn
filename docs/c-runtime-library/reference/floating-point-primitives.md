---
title: 浮点基元
ms.date: 4/2/2020
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
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d861fbf2b71d557354a60f65b8a76dc24ca1dd13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346713"
---
# <a name="floating-point-primitives"></a>浮点基元

特定于 Microsoft 的原始函数，用于实现某些标准 C 运行时库 （CRT） 浮点函数。 此处记录它们的完整性，但不建议使用。 其中一些函数被标记为未使用，因为它们在精度、异常处理和符合 IEEE-754 行为方面存在问题。 它们仅存在于库中，以便向后兼容性。 为了正确的行为、可移植性和对标准的遵守，首选标准浮点功能而不是这些函数。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass，_ldclass，_fdclass

### <a name="syntax"></a>语法

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>参数

** x <br/>
浮点函数参数。

### <a name="remarks"></a>备注

这些浮点基元实现针对浮点类型的 CRT 宏[fp 分类](fpclassify.md)的 C 版本。 参数*x*的分类返回为以下常量之一，在 math.h 中定义：

|“值”|说明|
|-----------|-----------------|
| **FP_NAN** | 静态、信令或不确定的 NaN |
| **FP_INFINITE** | 正或负无穷大 |
| **FP_NORMAL** | 标准化非零正值或负值 |
| **FP_SUBNORMAL** | 正或负次正次正态（非规范化）值 |
| **FP_ZERO** | 零正值或负值 |

有关其他详细信息，可以使用特定于 Microsoft[的_fpclass，_fpclassf](fpclass-fpclassf.md)功能。 使用[fp 分类](fpclassify.md)宏或函数进行便携性。

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign，_ldsign，_fdsign

### <a name="syntax"></a>语法

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>参数

** x <br/>
浮点函数参数。

### <a name="remarks"></a>备注

这些浮点基元在 CRT 中实现[符号位](signbit.md)宏或函数。 如果符号位设置在参数*x*的符号（mantissa）中，则返回非零值;如果未设置符号位，则返回 0。

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp、_ldpcomp、_fdpcomp

### <a name="syntax"></a>语法

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>参数

*x*， *y*<br/>
浮点函数参数。

### <a name="remarks"></a>备注

这些浮点基元采用两个参数 *，x*和*y*，并返回一个值，显示它们的排序关系，表示为位或这些常量，在 math.h 中定义：

| “值” | 说明 |
|------------|-----------------|
| **_FP_LT** | *x*可视为小于*y* |
| **_FP_EQ** | *x*可以被视为等于*y* |
| **_FP_GT** | *x*可视为大于*y* |

这些基元在 CRT 中实现["较大"、"相等"、"无均"、"无均"、"无命令"和"无命令](floating-point-ordering.md)宏"和"无命令"宏和函数。

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest，_ldtest，_fdtest

### <a name="syntax"></a>语法

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>参数

*Px*<br/>
指向浮点参数的指针。

### <a name="remarks"></a>备注

这些浮点基元实现C++版本的 CRT 函数[fp 分类](fpclassify.md)的浮点类型。 参数*x*被计算，分类返回为以下常量之一，在 math.h 中定义：

|“值”|说明|
|-----------|-----------------|
| **FP_NAN** | 静态、信令或不确定的 NaN |
| **FP_INFINITE** | 正或负无穷大 |
| **FP_NORMAL** | 标准化非零正值或负值 |
| **FP_SUBNORMAL** | 正或负次正次正态（非规范化）值 |
| **FP_ZERO** | 零正值或负值 |

有关其他详细信息，可以使用特定于 Microsoft[的_fpclass，_fpclassf](fpclass-fpclassf.md)功能。 使用[fp 分类](fpclassify.md)函数进行便携性。

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int，_ld_int，_fd_int

### <a name="syntax"></a>语法

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>参数

*Px*<br/>
指向浮点参数的指针。

*exp*<br/>
作为积分类型的指数。

### <a name="remarks"></a>备注

这些浮点基元获取指向浮点值*px*和指数值*exp*的指针，并尽可能删除给定指数下浮点值的分数部分。 返回的值是按*px（* 如果是 NaN 或无穷大）和对以*px（* 否则）的输出值进行**fp 分类**的结果。

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale，_ldscale，_fdscale

### <a name="syntax"></a>语法

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>参数

*Px*<br/>
指向浮点参数的指针。

*exp*<br/>
作为积分类型的指数。

### <a name="remarks"></a>备注

这些浮点基元采用指向浮点值*px*和指数值*exp*的指针，如果可能，以*px*为例缩放值 2<sup>*exp。*</sup> 返回的值是按*px（* 如果是 NaN 或无穷大）和对以*px（* 否则）的输出值进行**fp 分类**的结果。 对于可移植性，请首选[ldexp、ldexpf 和 ldexpl](ldexp.md)函数。

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale，_ldunscale，_fdunscale

### <a name="syntax"></a>语法

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>参数

*pexp*<br/>
指向指数作为积分类型的指针。

*Px*<br/>
指向浮点参数的指针。

### <a name="remarks"></a>备注

如果可能，这些浮点基元将*px*指向的浮点值分解为符号（mantissa）和指数（如果可能）。 符号缩放，使绝对值大于或等于 0.5 和小于 1.0。 指数是值*n，* 其中原始浮点值等于缩放的符号乘法乘以 2<sup>*n*</sup>。 此整数指数*n*存储在*pexp*指向的位置。 返回的值是输入*值（如果是*NaN 或无穷大）和对输出值（否则）的**fp 分类**的结果。 对于便携性，请首选[frexp、frexpf、frexpl](frexp.md)函数。

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp，_ldexp，_fdexp

### <a name="syntax"></a>语法

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>参数

*Y*<br/>
浮点函数参数。

*Px*<br/>
指向浮点参数的指针。

*exp*<br/>
作为积分类型的指数。

### <a name="remarks"></a>备注

这些浮点基元在*以 px*表示等于*y* = 2<sup>*exp*</sup>的位置构造一个浮点值。 返回的值是*y*中的输入值（如果是 NaN 或无穷大）和对*以 px*表示的输出值（否则）的**fp 分类**的结果。 对于可移植性，请首选[ldexp、ldexpf 和 ldexpl](ldexp.md)函数。

## <a name="_dnorm-_fdnorm"></a>_dnorm，_fdnorm

### <a name="syntax"></a>语法

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>参数

*ps*<br/>
指向以**无符号****短**数组表示的浮点值的位表示。

### <a name="remarks"></a>备注

这些浮点基元使浮点值的分馏部分规范化，并调整*特征*或偏置指数来匹配。 该值作为浮点类型的位表示形式传递，转换为通过`_double_val`、`_ldouble_val`或`_float_val`类型在 math.h 中声明的无**符号****短**的数组。 返回值是输入浮点值（如果是 NaN 或无穷大）和输出值（否则）上的**fp 分类**的结果。

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly，_ldpoly，_fdpoly

### <a name="syntax"></a>语法

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>参数

** x <br/>
浮点函数参数。

*表*<br/>
指向多项式常量系数表的指针。

*n*<br/>
要评估的多项式顺序。

### <a name="remarks"></a>备注

这些浮点基元返回阶的多项式*n*中*x*的评估，其系数由*表中*的相应常量值表示。 例如，如果*表*\[0= = 3.0，*表*\[1= 4.0，*表*\[2= 5.0，n = 2，则表示多项式 5.0x<sup>2</sup> = 4.0x = 3.0。 *n* 如果此多项式计算为*x* 2.0，则结果为 31.0。 这些函数不在内部使用。

## <a name="_dlog-_dlog-_dlog"></a>_dlog，_dlog，_dlog

### <a name="syntax"></a>语法

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>参数

** x <br/>
浮点函数参数。

*base_flag*<br/>
控制要使用的基础的标志，0 表示基*e，0*表示基 10。

### <a name="remarks"></a>备注

当*base_flag*为 0 时，这些浮点基元返回 x、ln（x ） 或日志<sub>*e*</sub> *x**（x）* 的自然日志。*x* 当*base_flag*为非零时，它们返回*x*的日志基 10 或日志<sub>10</sub>*（x*）。 这些函数不在内部使用。 对于可移植性，请首选函数[日志、logf、logl、log10、log10f 和 log10l](log-logf-log10-log10f.md)。

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin，_ldsin，_fdsin

### <a name="syntax"></a>语法

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>参数

** x <br/>
浮点函数参数。

*象限*<br/>
象限偏移 0、1、2 或 3 用于生成`sin` `cos`、`-sin`和`-cos`结果。

### <a name="remarks"></a>备注

这些浮点基元返回*象**限*莫杜洛 4 偏移 x 的子值。 当*象限*莫杜洛 4 分别为 0、1、2 或 3 时，它们返回*x*的正子、协和子、正子和 -协和子。 这些函数不在内部使用。 对于便携性，首选[子、鼻、弦、](sin-sinf-sinl.md)[科斯、科斯夫和科斯尔](cos-cosf-cosl.md)函数。

## <a name="requirements"></a>要求

标题：\<数学.h>

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支撑](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[是因夫](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[frexp、frexpf、frexpl](frexp.md)<br/>
[ldexp、ldexpf 和 ldexpl](ldexp.md)<br/>
[log、logf、logl、log10、log10f、log10l](log-logf-log10-log10f.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
