---
title: creal、crealf、creall
ms.date: 03/30/2018
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: 4dcdf60fee6d57b5561b72b477aa1a8bb31f35f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171211"
---
# <a name="creal-crealf-creall"></a>creal、crealf、creall

检索复数的实部。

## <a name="syntax"></a>语法

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>parameters

*z*<br/>
一个复数。

## <a name="return-value"></a>返回值

*Z*的实部。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用采用 **_Fcomplex**或 **_Lcomplex**值的**creal**重载，并返回**float**或**long double**值。 在 C 程序中， **creal**始终采用 **_Dcomplex**值并返回一个**双精度**值。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**creal**、 **crealf**、 **creall**|\<complex.h>|\<ccomplex>|

**_Fcomplex**、 **_Dcomplex**和 **_Lcomplex**类型是特定于 Microsoft 的等效项，它们分别是未实现的本机 C99 类型**float _Complex**、 **double _Complex**和**long double _Complex**。 有关兼容性的详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
