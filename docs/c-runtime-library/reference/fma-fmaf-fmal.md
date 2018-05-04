---
title: fma、fmaf、fmal | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
dev_langs:
- C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b28009a9c3cc4edceb9032660a0c2a71916dfb2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fma-fmaf-fmal"></a>fma、fmaf、fmal

两个值相乘，添加第三个值，然后将结果舍入，由于中间舍入不会丢失任何精度。

## <a name="syntax"></a>语法

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);

```

### <a name="parameters"></a>参数

*x*<br/>
要相乘的第一个值。

*y*<br/>
要相乘的第二个值。

*z*<br/>
要相加的值。

## <a name="return-value"></a>返回值

返回 `(x * y) + z`。 然后使用当前舍入格式舍入返回值。

否则，可能返回以下值之一：

|问题|返回|
|-----------|------------|
|*x* = 无穷大， *y* = 0 或<br /><br /> *x* = 0， *y* = 无穷大|NaN|
|*x*或*y* = 确切 ± 无穷大， *z*符号相反 = 无穷大|NaN|
|*x*或*y* = NaN|NaN|
|不 (*x* = 0， *y*= 无限期) 和*z* = NaN<br /><br /> 不 (*x*= 无限期， *y*= 0) 和*z* = NaN|NaN|
|溢出范围错误|±HUGE_VAL、 ±HUGE_VALF 或 ±HUGE_VALL|
|下溢范围错误|舍入后的正确值。|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于 c + + 允许重载，你可以调用的重载**fma**采用并返回**float**和**长** **double**类型。 在 C 程序中， **fma**始终采用并返回**double**。

此函数计算值就好像它采取了无限精度，然后将最终结果舍入。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fma**， **fmaf**， **fmal**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[remainder、remainderf、remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo、remquof、remquol](remquo-remquof-remquol.md)<br/>
