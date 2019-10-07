---
title: tgamma、tgammaf、tgammal
ms.date: 04/05/2018
api_name:
- tgamma
- tgammaf
- tgammal
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
ms.openlocfilehash: 02926fa49bbabeb9cf532f53cfa6e30a77805e70
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946215"
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

如果成功，则返回*x*的伽玛。

如果*x*的大小太大或数据类型太小，则可能会发生范围错误。 如果*x* < = 0，则可能出现域错误或范围错误。

|问题|返回|
|-----------|------------|
|x = ±0|±无限大|
|x = 负整数|NaN|
|x = -INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|域错误|NaN|
|极点错误|± HUGE_VAL、± HUGE_VALF 或± HUGE_VALL|
|溢出范围错误|± HUGE_VAL、± HUGE_VALF 或± HUGE_VALL|
|下溢范围错误|舍入后的正确值。|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**tgamma**的重载，该重载采用和返回**float**和**long** **double**类型。 在 C 程序中， **tgamma**始终采用并返回**双精度型**。

如果 x 是自然数，则此函数返回 (x-1) 的阶乘。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**tgamma**、 **tgammaf**、 **tgammal**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[lgamma、lgammaf、lgammal](lgamma-lgammaf-lgammal.md)<br/>
