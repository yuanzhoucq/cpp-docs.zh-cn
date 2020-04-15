---
title: atan、atanf、atanl、atan2、atan2f、atan2l
ms.date: 4/2/2020
api_name:
- atan2f
- atan2l
- atan2
- atanf
- atan
- atanl
- _o_atan
- _o_atan2
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
ms.openlocfilehash: 3b8411f9839022477dff3100792e271e2f0b572b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334122"
---
# <a name="atan-atanf-atanl-atan2-atan2f-atan2l"></a>atan、atanf、atanl、atan2、atan2f、atan2l

计算**x（****阿坦**、**阿坦夫**和**阿坦尔**）的弧形或**y**/**x（****阿坦2、****阿坦2f**和**atan2l）** 的弧形。

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

**atan**返回范围 -*/2 到 +/2 弧度中的*x*弧形。 **atan2**返回范围 -α 中*y*/*x*的弧线 - = 弧度。 如果*x*为 0，**则 atan**返回 0。 如果**atan2**的两个参数均为 0，则函数返回 0。 所有结果都都以弧度为单位。

**atan2**使用两个参数的符号来确定返回值的象限。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|• **QNAN**， **IND**|无|**_DOMAIN**|

## <a name="remarks"></a>备注

**atan**函数计算*x*的弧切（逆切线函数）。 **atan2**计算*y*/*x*的弧形（如果*x*等于**0，atan2**返回 +/2，如果*y*为正，则 -+/2 如果*y*为负，则为 0，如果*y*为 0，则为 0。

**atan**具有使用流式 SIMD 扩展 2 （SSE2） 的实现。 有关使用 SSE2 实现的信息和限制，请参阅 [_set_SSE2_enable](set-sse2-enable.md)。

由于C++允许重载，因此可以调用采用**浮点**或**长****双**参数的**atan**和**atan2**的重载。 在 C 程序中 **，atan**和**atan2**总是采用**双重**参数并返回**一个双**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**阿坦**，**阿坦2**，**阿坦夫**，**阿坦2f**，**阿坦，****阿坦2l**|\<math.h>|\<cmath> 或 \<math.h>|

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

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[tan、tanf、tanl](tan-tanf-tanl.md)<br/>
[_CIatan](../../c-runtime-library/ciatan.md)<br/>
[_CIatan2](../../c-runtime-library/ciatan2.md)<br/>
