---
title: atan、atanf、atanl、atan2、atan2f、atan2l
ms.date: 04/05/2018
apiname:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
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
- atan
- atan2l
- atan2
- atanl
- atanf
- atan2f
helpviewer_keywords:
- atan function
- atanf function
- atanl function
- atan2 function
- atan2l function
- arctangent function
- trigonometric functions
- atan2f function
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
ms.openlocfilehash: 59a67b0d213a11630f551fd7582b44aab60e314f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341712"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan、atanf、atanl、atan2、atan2f、atan2l

计算反正切值**x** (**atan**， **atanf**，以及**atanl**) 或的反正切值**y** /**x** (**atan2**， **atan2f**，以及**atan2l**)。

## <a name="syntax"></a>语法

```C
double atan( double x );
float atanf( float x );
long double atanl( long double x );

double atan2( double y, double x );
float atan2f( float y, float x );
long double atan2l( long double y, long double x );
```

```cpp
float atan( float x );  // C++ only
long double atan( long double x );  // C++ only

float atan2( float y, float x );  // C++ only
long double atan2( long double y, long double x );  // C++ only
```

### <a name="parameters"></a>参数

*x*， *y*<br/>
任意数字。

## <a name="return-value"></a>返回值

**atan**返回的反正切*x*中范围-π/2 到 π/2 弧度。 **atan2**返回的反正切*y*/*x*中范围-π 到 π 弧度。 如果*x*为 0， **atan**返回 0。 如果这两个参数的**atan2**均为 0，则函数返回 0。 所有结果都都以弧度为单位。

**atan2**使用这两个参数符号来确定返回值的象限。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|为**QNAN**， **IND**|无|**_DOMAIN**|

## <a name="remarks"></a>备注

**Atan**函数可用于计算反正切值 （反正切函数） 的*x*。 **atan2**计算反正切值*y*/*x* (如果*x*等于 0， **atan2**返回 π/2，如果*y*为正，因此-π/2; 如果*y*是负数，或者，如果*y*为 0。)

**atan**具有使用流式处理 SIMD 扩展 2 (SSE2) 的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](set-sse2-enable.md)。

因为C++允许重载，可以调用的重载**atan**并**atan2**采用**float**或**长** **双精度**参数。 在 C 程序中， **atan**并**atan2**始终采用**double**参数和返回**double**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**atan**， **atan2**， **atanf**， **atan2f**， **atanl**， **atan2l**|\<math.h>|\<cmath> 或 \<math.h>|

## <a name="example"></a>示例

```C
// crt_atan.c
// arguments: 5 0.5
#include <math.h>
#include <stdio.h>
#include <errno.h>

int main( int ac, char* av[] )
{
   double x, y, theta;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );
      return 1;
   }
   x = atof( av[1] );
   theta = atan( x );
   printf( "Arctangent of %f: %f\n", x, theta );
   y = atof( av[2] );
   theta = atan2( y, x );
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );
   return 0;
}
```

```Output
Arctangent of 5.000000: 1.373401
Arctangent of 0.500000 / 5.000000: 0.099669
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
