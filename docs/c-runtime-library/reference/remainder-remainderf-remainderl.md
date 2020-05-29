---
title: remainder、remainderf、remainderl
ms.date: 4/2/2020
api_name:
- remainderl
- remainder
- remainderf
- _o_remainder
- _o_remainderf
- _o_remainderl
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 6b2a1a94fa39f9e9474f7bc3da3150bf4134d35f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917853"
---
# <a name="remainder-remainderf-remainderl"></a>remainder、remainderf、remainderl

计算两个浮点值的商的余数（四舍五入到最接近的整数值）。

## <a name="syntax"></a>语法

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>参数

*x*<br/>
分子。

*误差*<br/>
分母。

## <a name="return-value"></a>返回值

*X* / *y*的浮点余数。 如果*y*的值为0.0，则**余数**返回静默 NaN。 有关**printf**系列的 quiet NaN 表示形式的信息，请参阅[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>备注

**余数**函数计算*x* / *y*的浮点余数*r* ，如*x* = *n* \* *y* + *r*（其中*n*是最接近*x* / *y*的整数），n 只要 &#124; *n* - *x* / *y* &#124; = 1/2，就会进行*n*运算。 当*r* = 0 时， *r*与*x*具有相同的符号。

由于 c + + 允许重载，因此你可以调用采用并返回**浮点**或**长****双精度**值的**余数**的重载。 在 C 程序中，**余数**始终采用两个**双精度型**参数，并返回**double**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头 (C)|必需的标头 (C++)|
|--------------|---------------------|-|
|**余数**、 **remainderf**、 **remainderl**|\<math.h>|\<cmath> 或 \<math.h>|

有关兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[remquo、remquof、remquol](remquo-remquof-remquol.md)<br/>
