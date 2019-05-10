---
title: _Cbuild、 _FCbuild、 _LCbuild
ms.date: 03/30/2018
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
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: 5565c87a3cccd1715a1357f417238587f3fba4d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340461"
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild、 _FCbuild、 _LCbuild

构造从实部和虚部的复数。

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

一个 **_Dcomplex**， **_Fcomplex**，或 **_Lcomplex**结构，它表示复数 (*实际*，*虚部* \*我) 指定的浮点类型的值。

## <a name="remarks"></a>备注

**_Cbuild**， **_FCbuild**，并 **_LCbuild**函数简化复杂类型的创建。 使用[creal、 crealf、 creall](creal-crealf-creall.md)并[cimag、 cimagf、 cimagl](cimag-cimagf-cimagl.md)函数来检索表示复数的实部和虚部部分。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**_Cbuild**， **_FCbuild**， **_LCbuild**|\<complex.h>|\<ccomplex>|

这些函数是特定于 Microsoft 的。 类型 **_Dcomplex**， **_Fcomplex**，并 **_Lcomplex**是未实现 C99 本机类型与特定于 Microsoft 的等效**double _Complex**， **float _Complex**，和**long double _Complex**分别。 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc、_FCmulcc、_LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr、_FCmulcr、_LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
