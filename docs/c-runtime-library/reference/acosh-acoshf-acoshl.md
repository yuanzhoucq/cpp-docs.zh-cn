---
title: acosh、acoshf、acoshl
ms.date: 4/2/2020
api_name:
- acoshf
- acosh
- acoshl
- _o_acosh
- _o_acoshf
- _o_acoshl
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
- acosh
- acoshf
- acoshl
- math/acosh
- math/acoshf
- math/acoshl
helpviewer_keywords:
- acoshf function
- acosh function
- acoshl function
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
ms.openlocfilehash: b719f67651643885351843fb8e995964e03de105
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350848"
---
# <a name="acosh-acoshf-acoshl"></a>acosh、acoshf、acoshl

计算反双曲余弦。

## <a name="syntax"></a>语法

```C
double acosh( double x );
float acoshf( float x );
long double acoshl( long double x );
```

```cpp
float acosh( float x );  // C++ only
long double acosh( long double x );  // C++ only
```

### <a name="parameters"></a>参数

** x <br/>
浮点值。

## <a name="return-value"></a>返回值

**acosh**函数返回*x*的反向子宫面结节（弧形双曲子）。 这些函数在域*x* = 1 上有效。 如果*x*小于 1，`errno`则设置为`EDOM`，并且结果是一个安静的 NaN。 如果*x*是安静的 NaN、无限期或无穷大，则返回相同的值。

|输入|SEH 异常|`_matherr` 异常|
|-----------|-------------------|--------------------------|
|• QNAN，IND，INF|无|无|
|*x* < 1|无|无|

## <a name="remarks"></a>备注

使用C++时，可以调用获取和返回**浮点**值或**长****双精度**值的**aosh**重载。 在C程序中，**阿科什**总是采取并返回**双**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**阿科什**，**阿科斯夫**，**阿科斯赫尔**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_acosh.c
// Compile by using: cl /W4 crt_acosh.c
// This program displays the hyperbolic cosine of pi / 4
// and the arc hyperbolic cosine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = cosh( pi / 4 );
   y = acosh( x );
   printf( "cosh( %f ) = %f\n", pi/4, x );
   printf( "acosh( %f ) = %f\n", x, y );
}
```

```Output
cosh( 0.785398 ) = 1.324609
acosh( 1.324609 ) = 0.785398
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh、coshf、coshl](cosh-coshf-coshl.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)
