---
title: lgamma、lgammaf、lgammal
ms.date: 04/05/2018
api_name:
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
ms.openlocfilehash: 9baf8f0fefb50cea6a5301aac9ffd48ff3cd5bde
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953376"
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma、lgammaf、lgammal

确定指定值的伽玛函数绝对值的自然对数。

## <a name="syntax"></a>语法

```C
double lgamma( double x );
float lgammaf( float x );
long double lgammal( long double x );
```

```cpp
float lgamma( float x ); //C++ only
long double lgamma( long double x ); //C++ only
```

### <a name="parameters"></a>参数

*x*<br/>
要计算的值。

## <a name="return-value"></a>返回值

如果成功，则返回*x*的伽玛函数绝对值的自然对数。

|问题|返回|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = ±0|+INFINITY|
|*x*= 负整数|+INFINITY|
|±无限大|+INFINITY|
|极点错误|\+ HUGE_VAL、+ HUGE_VALF，或 + HUGE_VALL|
|溢出范围错误|± HUGE_VAL、± HUGE_VALF 或± HUGE_VALL|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**lgamma**的重载，该重载采用和返回**float**和**long** **double**类型。 在 C 程序中， **lgamma**始终采用并返回**双精度型**。

如果 x 是有理数，则此函数返回（x-1）的阶乘的对数。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**lgamma**、 **lgammaf**、 **lgammal**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[tgamma、tgammaf、tgammal](tgamma-tgammaf-tgammal.md)<br/>
