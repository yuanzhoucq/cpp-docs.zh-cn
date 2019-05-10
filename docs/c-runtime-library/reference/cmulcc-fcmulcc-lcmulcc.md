---
title: _Cmulcc、 _FCmulcc、 _LCmulcc
ms.date: 03/30/2018
apiname:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
ms.openlocfilehash: f81ccb641a80ab264e8bc54ba1987e2c2c8469f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335370"
---
# <a name="cmulcc-fcmulcc-lcmulcc"></a>_Cmulcc、 _FCmulcc、 _LCmulcc

将两个复数相乘。

## <a name="syntax"></a>语法

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>参数

*x*<br/>
其中一个复杂的操作数进行乘法运算。

*y*<br/>
其他复杂操作数进行乘法运算。

## <a name="return-value"></a>返回值

一个 **_Dcomplex**， **_Fcomplex**，或 **_Lcomplex**结构，它表示复杂数字的复杂产品*x*和*y*。

## <a name="remarks"></a>备注

内置算术运算符无法正常工作的 Microsoft 实现的复杂类型，因为 **_Cmulcc**， **_FCmulcc**，并 **_LCmulcc**函数简化复杂类型的乘法。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**_Cmulcc**, **_FCmulcc**, **_LCmulcc**|\<complex.h>|\<complex.h>|

这些函数是特定于 Microsoft 的。 类型 **_Dcomplex**， **_Fcomplex**，并 **_Lcomplex**是未实现 C99 本机类型与特定于 Microsoft 的等效**double _Complex**， **float _Complex**，和**long double _Complex**分别。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr、_FCmulcr、_LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
