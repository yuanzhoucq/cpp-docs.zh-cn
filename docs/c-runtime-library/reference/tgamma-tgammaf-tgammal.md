---
title: tgamma、tgammaf、tgammal
ms.date: 04/05/2018
apiname:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: c9ff92658163fc20ce21496aba34b22b3661748b
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518939"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma、tgammaf、tgammal

确定指定值的 gamma 函数。

## <a name="syntax"></a>语法

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
要查找其伽玛值的值。

## <a name="return-value"></a>返回值

如果成功，则返回的伽玛*x*。

如果出现范围错误的严重性*x*太大或太小，数据类型。 如果，可能会发生域错误或范围错误*x* < = 0。

|问题|返回|
|-----------|------------|
|x = ±0|±INFINITY|
|x = 负整数|NaN|
|x =-无穷大|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|域错误|NaN|
|极点错误|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|
|溢出范围错误|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|
|下溢范围错误|舍入后的正确值。|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**tgamma**采用并返回**float**并**长** **double**类型。 在 C 程序中， **tgamma**始终采用并返回**double**。

如果 x 是自然数，则此函数返回 (x-1) 的阶乘。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**tgamma**， **tgammaf**， **tgammal**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[lgamma、lgammaf、lgammal](lgamma-lgammaf-lgammal.md)<br/>
