---
title: logb、logbf、logbl、_logb、_logbf
ms.date: 04/05/2018
api_name:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
ms.openlocfilehash: c5fc59f786b00dcf4ab1056424d8442a03f3adbf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953150"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>logb、logbf、logbl、_logb、_logbf

提取浮点型参数的指数值。

## <a name="syntax"></a>语法

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值。

## <a name="return-value"></a>返回值

**logb**将*x*的无偏差指数值返回为以浮点值形式表示的有符号整数。

## <a name="remarks"></a>备注

**Logb**函数提取浮点参数*x*的指数值，就好像*x*是用无限范围表示的。 如果参数*x*不规范，则将其视为已规范化。

由于C++允许重载，因此你可以调用**logb**的重载，该重载采用并返回**浮点**或**长** **双精度**值。 在 C 程序中， **logb**始终采用并返回**双精度型**。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± QNAN，IND|无|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_logb**|\<float.h>|
|**logb**、 **logbf**、 **logbl**、 **_logbf**|\<math.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
