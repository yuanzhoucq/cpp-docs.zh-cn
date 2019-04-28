---
title: fdim、fdimf、fdiml
ms.date: 04/05/2018
apiname:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: 263635a32b21b01faa84405ab97bd5518f054ba5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334783"
---
# <a name="fdim-fdimf-fdiml"></a>fdim、fdimf、fdiml

确定第一个值和第二个值之间的正数差。

## <a name="syntax"></a>语法

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);
```

### <a name="parameters"></a>参数

*x*<br/>
第一个值。

*y*<br/>
第二个值。

## <a name="return-value"></a>返回值

返回之间的正数差*x*并*y*:

|返回值|方案|
|------------------|--------------|
|x-y|如果 x > y|
|0|如果 x <= y|

否则，可能返回以下错误之一：

|问题|返回|
|-----------|------------|
|溢出范围错误|+ HUGE_VAL、+ HUGE_VALF，或 + HUGE_VALL|
|下溢范围错误|正确值（舍入后）|
|*x*或*y*为 NaN|NaN|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

因为C++允许重载，可以调用的重载**fdim**采用并返回**float**并**长** **double**类型。 在 C 程序中， **fdim**始终采用并返回**double**。

除了 NaN 处理，此函数相当于`fmax(x - y, 0)`。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fdim**， **fdimf**， **fdiml**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
