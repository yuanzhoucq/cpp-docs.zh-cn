---
title: _Cbuild，_FCbuild，_LCbuild |Microsoft 文档
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
dev_langs:
- C++
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d5a2a5f40266f490cc0d18614c63715192b0707
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2018
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild，_FCbuild _LCbuild

构造从与实部和虚部的复数。

## <a name="syntax"></a>语法

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>参数

*real*<br/>
要构造的复数实部。

*imaginary*<br/>
要构造的复数的虚部。

## <a name="return-value"></a>返回值

A **_Dcomplex**， **_Fcomplex**，或**_Lcomplex**结构，它表示复数 (*实际*，*虚部* \*我) 为指定的浮点类型的值。

## <a name="remarks"></a>备注

**_Cbuild**， **_FCbuild**，和**_LCbuild**函数简化创建复杂类型。 使用[creal，crealf，creall](../../c-runtime-library/reference/creal-crealf-creall.md)和[cimag，cimagf，cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)函数来检索表示复数的实部和虚部部分。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|`_Cbuild`,`_FCbuild`, `_LCbuild`|\<complex.h>|\<ccomplex>|

这些函数是特定于 Microsoft 的。 类型**_Dcomplex**， **_Fcomplex**，和**_Lcomplex**到未实现的 C99 本机类型的特定于 Microsoft 的等效项**double _Complex**， **float _Complex**，和**长双精度 _Complex**分别。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](../../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](../../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](../../c-runtime-library/reference/norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)<br/>
[creal、crealf、creall](../../c-runtime-library/reference/creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)<br/>
