---
title: ldexp、ldexpf、ldexpl
ms.date: 4/2/2020
api_name:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
- _o_ldexp
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 0432cfb66db5a90c933401549aba1b538fa66855
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342234"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp、ldexpf、ldexpl

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

** x <br/>
浮点值。

*exp*<br/>
整数指数。

## <a name="return-value"></a>返回值

**如果成功，ldexp**函数返回*x* \* 2<sup>*exp*</sup>的值。 在溢出时，并根据*x*的**符号返回**+/- **HUGE_VAL**;**errno**值设置为**ERANGE**。

有关**errno**和可能的错误返回值的详细信息，请参阅[errno、_doserrno、_sys_errlist 和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用采用**浮点**或**长****双**类型**ldexp**的重载。 在 C 程序中 **，ldexp**始终采用**双****和 int**并返回**一个双**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**ldexp**， **ldexpf**， **ldexpl**|\<math.h>|\<cmath>|

有关兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
