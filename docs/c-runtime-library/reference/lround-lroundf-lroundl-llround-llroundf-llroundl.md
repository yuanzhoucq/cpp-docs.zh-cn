---
title: lround、lroundf、lroundl、llround、llroundf、llroundl
ms.date: 04/05/2018
apiname:
- llround
- llroundf
- llroundl
- lroundf
- lround
- lroundl
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
- lround
- lroundl
- llroundl
- llround
- lroundf
- llroundf
helpviewer_keywords:
- lround function
- llroundl function
- llround function
- lroundf function
- llroundf function
- lroundl function
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
ms.openlocfilehash: a1406f84179df555125b908caa13a0cde6516597
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601443"
---
# <a name="lround-lroundf-lroundl-llround-llroundf-llroundl"></a>lround、lroundf、lroundl、llround、llroundf、llroundl

将浮点值舍入为最接近的整数。

## <a name="syntax"></a>语法

```C
long lround(
   double x
);
long lround(
   float x
);  // C++ only
long lround(
   long double x
);  // C++ only
long lroundf(
   float x
);
long lroundl(
   long double x
);
long long llround(
   double x
);
long long llround(
   float x
);  // C++ only
long long llround(
   long double x
);  // C++ only
long long llroundf(
   float x
);
long long llroundl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
要舍入的浮点值。

## <a name="return-value"></a>返回值

**Lround**并**llround**函数返回最接近**长**或**长****长**到整数*x*。 中间值从零舍入，这与浮点舍入模式的设置无关。 无错误返回。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|为**QNAN**， **IND**|无|**（_D)**|

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**lround**或**llround**采用并返回**float**并**长** **双**值。 在 C 程序中， **lround**并**llround**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**lround**， **lroundf**， **lroundl**， **llround**， **llroundf**， **llroundl**|\<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_lround.c
// Build with: cl /W4 /Tc crt_lround.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 3.5 and -3.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 3.5L;

   printf("lround(%f) is %d\n", x, lround(x));
   printf("lround(%f) is %d\n", -x, lround(-x));
   printf("lroundf(%f) is %d\n", y, lroundf(y));
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));
}
```

```Output
lround(2.499999) is 2
lround(-2.499999) is -2
lroundf(2.800000) is 3
lroundf(-2.800000) is -3
lroundl(3.500000) is 4
lroundl(-3.500000) is -4
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[lrint、lrintf、lrintl、llrint、llrintf、llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[round、roundf、roundl](round-roundf-roundl.md)<br/>
[nearbyint、nearbyintf、nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint、rintf、rintl](rint-rintf-rintl.md)<br/>
