---
title: copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl
ms.date: 04/05/2018
apiname:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
ms.openlocfilehash: 6f450da4a4391f94d1905beefdeca8e3f01fec51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662808"
---
# <a name="copysign-copysignf-copysignl-copysign-copysignf-copysignl"></a>copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl

返回一个值，该值具有一个自变量的数值和另一个自变量的符号。

## <a name="syntax"></a>语法

```C
double copysign(
   double x,
   double y
);
float copysign(
   float x,
   float y
); // C++ only
long double copysign(
   long double x,
   long double y
); // C++ only
float copysignf(
   float x,
   float y
); // C++ only
long double copysignl(
   long double x,
   long double y
); // C++ only
double _copysign(
   double x,
   double y
);
long double _copysignl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>参数

*x*<br/>
作为结果的数值返回的浮点值。

*y*<br/>
作为结果的符号返回的浮点值。

[浮点支持例程](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>返回值

**Copysign**函数返回浮点值，它将合并的量*x*和的符号*y*。 无错误返回。

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**copysign**采用并返回**float**或**长** **double**值。 在 C 程序中， **copysign**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_copysign**|\<float.h>|
|**copysign**， **copysignf**， **copysignl**， **_copysignf**， **_copysignl**|\<math.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign、_chgsignf、_chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
