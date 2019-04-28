---
title: fmod、 fmodf、 fmodl
ms.date: 04/05/2018
apiname:
- fmod
- fmodf
- fmodl
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: 78677be1a0c9921c35e54d43a00b8956a9d858b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333347"
---
# <a name="fmod-fmodf-fmodl"></a>fmod、 fmodf、 fmodl

计算浮点余数。

## <a name="syntax"></a>语法

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>参数

*x*， *y*<br/>
浮点值。

## <a name="return-value"></a>返回值

**fmod**返回的浮点余数*x* / *y*。 如果的值*y*为 0.0， **fmod**返回静态 NaN。 有关安静 NaN 的表示形式**printf**系列，请参阅[printf](printf-printf-l-wprintf-wprintf-l.md)。

## <a name="remarks"></a>备注

**Fmod**函数计算的浮点余数*f*的*x* / *y*以便*x* = *我* \* *y* + *f*，其中*我*是一个整数， *f*具有相同的符号*x*，和值的绝对值*f*是值的绝对值小于*y*。

C++允许重载，因此可以调用的重载**fmod**采用并返回**float**并**长** **double**值。 在 C 程序中， **fmod**始终采用两个**double**自变量并返回**double**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fmod**， **fmodf**， **fmodl**|\<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
