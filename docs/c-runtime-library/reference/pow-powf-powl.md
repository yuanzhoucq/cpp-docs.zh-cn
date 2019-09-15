---
title: pow、powf、powl
ms.date: 04/05/2018
api_name:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: 863d2b76ec131670b10eefc086fa3485bd0a983d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950291"
---
# <a name="pow-powf-powl"></a>pow、powf、powl

计算*x*的*y*次幂。

## <a name="syntax"></a>语法

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
Base。

*y*<br/>
Exponent。

## <a name="return-value"></a>返回值

返回*x*<sup>*y*</sup>的值。 在溢出或下溢时不输出错误消息。

|x 和 y 的值|pow 的返回值|
|-----------------------|-------------------------|
|*x* ！ = 0.0， *y* = = 0。0|1|
|*x* = = 0.0， *y* = = 0。0|1|
|*x* = = 0.0， *y* < 0|INF|

## <a name="remarks"></a>备注

**pow**不识别大于 2<sup>64</sup>的整数浮点值（例如，1.0 e100）。

**pow**具有使用流式处理 simd 扩展2（SSE2）的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](set-sse2-enable.md)。

由于C++允许重载，因此可以调用**pow**的任何不同重载。 在 C 程序中， **pow**始终采用两个**双精度**值并返回一个**双精度**值。

`pow(int, int)` 将不再可用。 如果使用此重载，编译器可能会发出[C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md)。 若要避免此问题，请将第一个参数转换为**double**、 **float**或**long** **double**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头 (C)|必需的标头 (C++)|
|-|-|-|
|**pow**、 **powf**、 **powl**|\<math.h>|\<math.h> 或 \<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md) <br/>
[exp、expf、expl](exp-expf.md) <br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md) <br/>
[sqrt、sqrtf、sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
