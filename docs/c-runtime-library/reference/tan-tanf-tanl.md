---
title: tan、tanf、tanl
ms.date: 04/10/2018
api_name:
- tan
- tanf
- tanl
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
- tan
- tanf
- _tanl
- tanl
helpviewer_keywords:
- tanl function
- _tanl function
- tan function
- calculating tangents
- tangent
- tanf function
- trigonometric functions
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
ms.openlocfilehash: 9fc1a75bdc6fddb5134b9db17961ba3c4550bc79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168702"
---
# <a name="tan-tanf-tanl"></a>tan、tanf、tanl

计算正切值。

## <a name="syntax"></a>语法

```C
double tan( double x );
float tanf( float x );
long double tanl( long double x );
```

```cpp
float tan( float x );  // C++ only
long double tan( long double x );  // C++ only
```

### <a name="parameters"></a>parameters

*x*<br/>
角度（以弧度为单位）。

## <a name="return-value"></a>返回值

**Tan**函数返回*x*的正切值。 如果*x*大于或等于263，或者小于或等于-263，则结果中的结果会丢失。

|输入|SEH 异常|**Matherr**异常|
|-----------|-------------------|-------------------------|
|± QNAN，IND|none|_DOMAIN|
|± INF|**无效**|_DOMAIN|

## <a name="remarks"></a>备注

由于C++允许重载，因此你可以调用具有**tan**的重载，该重载采用并返回**浮点**或**长** **双精度**值。 在 C 程序中， **tan**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------|-|
|**tan**、 **tanf**、 **tanl**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_tan.c
// This program displays the tangent of pi / 4
// Compile by using: cl crt_tan.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x;

   x = tan( pi / 4 );
   printf( "tan( %f ) = %f\n", pi/4, x );
}
```

```Output
tan( 0.785398 ) = 1.000000
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[acos、acosf、acosl](acos-acosf-acosl.md)<br/>
[asin、asinf、asinl](asin-asinf-asinl.md)<br/>
[atan、atanf、atanl、atan2、atan2f、atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
[_CItan](../../c-runtime-library/citan.md)<br/>
