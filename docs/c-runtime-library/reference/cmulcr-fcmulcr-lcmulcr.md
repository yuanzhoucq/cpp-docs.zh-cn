---
title: _Cmulcr，_FCmulcr，_LCmulcr |Microsoft 文档
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
- _Cmulcr
- _FCmulcr
- _LCmulcr
- complex/_Cmulcr
- complex/_FCmulcr
- complex/_LCmulcr
dev_langs:
- C++
helpviewer_keywords:
- _Cmulcr function
- _FCmulcr function
- _LCmulcr function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbd42e4c543d4bc42afa023d62b328a143c90374
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395020"
---
# <a name="cmulcr-fcmulcr-lcmulcr"></a>_Cmulcr，_FCmulcr _LCmulcr

将浮点数的复数相乘。

## <a name="syntax"></a>语法

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>参数

*x*<br/>
其中一个复杂的操作数进行乘法运算。

*y*<br/>
要相乘的浮点操作数。

## <a name="return-value"></a>返回值

A **_Dcomplex**， **_Fcomplex**，或 **_Lcomplex**结构，它表示复数的复杂产品*x*和flaoting 点数*y*。

## <a name="remarks"></a>备注

内置算术运算符无法正常工作的 Microsoft 实现的复杂类型，因为 **_Cmulcr**， **_FCmulcr**，和 **_LCmulcr**函数简化乘法的浮点类型的复杂类型。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**_Cmulcr**， **_FCmulcr**， **_LCmulcr**|\<complex.h>|\<complex.h>|

这些函数是特定于 Microsoft 的。 类型 **_Dcomplex**， **_Fcomplex**，和 **_Lcomplex**到未实现的 C99 本机类型的特定于 Microsoft 的等效项**double _Complex**， **float _Complex**，和**长双精度 _Complex**分别。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcc、_FCmulcc、_LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
