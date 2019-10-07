---
title: modf、modff、modfl
ms.date: 04/05/2018
api_name:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: 32caadb787031dca0b0726c546a11c5cd6722b82
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951544"
---
# <a name="modf-modff-modfl"></a>modf、modff、modfl

将浮点值拆分为小数部分和整数部分。

## <a name="syntax"></a>语法

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值。

*intptr*<br/>
指向存储整数部分的指针。

## <a name="return-value"></a>返回值

此函数返回 *x* 的有符号小数部分。 无错误返回。

## <a name="remarks"></a>备注

**Modf**函数将浮点值*x*分解为小数部分和整数部分，每个部分都具有与*x*相同的符号。 返回*x*的带符号小数部分。 整数部分存储为介于*intptr*的浮点值。

**modf**具有使用流式处理 simd 扩展2（SSE2）的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](set-sse2-enable.md)。

C++允许重载，因此你可以调用**modf**的重载，该重载采用并返回**浮点**或**长** **双精度**型参数。 在 C 程序中， **modf**始终采用两个双精度值并返回一个双精度值。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**modf**、 **modff**、 **modfl**|C：\<math.h><br /><br /> C++：\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
