---
title: cabs、cabsf、cabsl
ms.date: 11/04/2016
api_name:
- cabs
- cabsf
- cabsl
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
- cabs
- cabsf
- cabsl
- complex/cabs
- complex/cabsf
- complex/cabsl
helpviewer_keywords:
- cabs function
- cabsf function
- cabsl function
ms.assetid: 6b8eb453-cc8f-4972-bebf-351cbdfdfc15
ms.openlocfilehash: 62f297bba116550f572725a6bde094e5407777a4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939404"
---
# <a name="cabs-cabsf-cabsl"></a>cabs、cabsf、cabsl

检索复数的绝对值。

## <a name="syntax"></a>语法

```C
double cabs(
   _Dcomplex z
);
float cabs(
   _Fcomplex z
);  // C++ only
long double cabs(
   _Lcomplex z
);  // C++ only
float cabsf(
   _Fcomplex z
);
long double cabsl(
   _Lcomplex z
);
```

### <a name="parameters"></a>参数

*z*<br/>
一个复数。

## <a name="return-value"></a>返回值

*Z*的绝对值。

## <a name="remarks"></a>备注

由于C++允许重载，因此你可以调用采用 **_Fcomplex**或 **_Lcomplex**值的**cab**的重载，并返回**浮点**或**长** **双精度**值。 在 C 程序中， **cab**始终使用 **_Dcomplex**值并返回一个**双精度**值。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**cab**、 **cabsf**、 **cabsl**|\<complex.h>|\<ccomplex>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
