---
title: _Cmulcc，_FCmulcc，_LCmulcc |Microsoft 文档
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d6e0158543a90135cb10e76f7c8df0102f5c6a68
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2018
---
# <a name="cmulcc-fcmulcc-lcmulcc"></a>_Cmulcc, _FCmulcc, _LCmulcc

两个复数相乘。

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

A **_Dcomplex**， **_Fcomplex**，或**_Lcomplex**结构，它表示复杂数字的复杂产品*x*和*y*。

## <a name="remarks"></a>备注

内置算术运算符无法正常工作的 Microsoft 实现的复杂类型，因为**_Cmulcc**， **_FCmulcc**，和**_LCmulcc**函数简化乘法的复杂类型。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|`_Cmulcc`,`_FCmulcc`, `_LCmulcc`|\<complex.h>|\<ccomplex>|

这些函数是特定于 Microsoft 的。 类型**_Dcomplex**， **_Fcomplex**，和**_Lcomplex**到未实现的 C99 本机类型的特定于 Microsoft 的等效项**double _Complex**， **float _Complex**，和**长双精度 _Complex**分别。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_Cbuild，_FCbuild _LCbuild](../../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](../../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](../../c-runtime-library/reference/norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)<br/>
[creal、crealf、creall](../../c-runtime-library/reference/creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)<br/>
