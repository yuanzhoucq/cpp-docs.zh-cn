---
title: acosh、acoshf、acoshl | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- acoshf
- acosh
- acoshl
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
- acosh
- acoshf
- acoshl
- math/acosh
- math/acoshf
- math/acoshl
dev_langs:
- C++
helpviewer_keywords:
- acoshf function
- acosh function
- acoshl function
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 546006fcf1c559317b4afff424976db8109442e7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404747"
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

*x*  
浮点值。

## <a name="return-value"></a>返回值

**Acosh**函数返回的反双曲余弦值 （反双曲余弦值） *x*。 这些函数是有效的域上*x* ≥ 1。 如果*x*小于 1，`errno`设置为`EDOM`和结果是 quiet NaN。 如果*x*是不定的静默 NaN 或无穷大，返回相同的值。

|输入|SEH 异常|`_matherr` 异常|
|-----------|-------------------|--------------------------|
|± QNAN、IND、INF|无|无|
|*x* < 1|无|无|

## <a name="remarks"></a>备注

当你使用 c + + 时，可以调用的重载**acosh**采用并返回**float**或**长** **double**值。 在 C 程序中， **acosh**始终采用并返回**double**。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**acosh**， **acoshf**， **acoshl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)  
[asinh、asinhf、asinhl](asinh-asinhf-asinhl.md)  
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)  
[cosh、coshf、coshl](cosh-coshf-coshl.md)  
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)  
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)  