---
title: ldexp、 ldexpf、 ldexpl
ms.date: 04/05/2018
apiname:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
ms.openlocfilehash: 7fbf89f8d78e8a2ce1018a790350ec986dcab87e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502604"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp、 ldexpf、 ldexpl

将浮点数乘以二的整数幂。

## <a name="syntax"></a>语法

```C
double ldexp(
   double x,
   int exp
);
float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值。

*exp*<br/>
整数指数。

## <a name="return-value"></a>返回值

**Ldexp**函数将返回的值*x* \* 2<sup>*exp* </sup>如果成功。 在溢出时，和具体取决于的符号*x*， **ldexp**返回 + /- **HUGE_VAL**; **errno**值设置为**ERANGE**.

有关详细信息**errno**和可能的错误返回值，请参阅[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**ldexp**采用**float**或**长** **double**类型。 在 C 程序中， **ldexp**始终采用**double**和一个**int** ，并返回**double**。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**ldexp**， **ldexpf**， **ldexpl**|\<math.h>|\<cmath>|

有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>输出

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
