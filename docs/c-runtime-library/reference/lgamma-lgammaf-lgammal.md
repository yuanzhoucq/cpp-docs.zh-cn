---
title: lgamma、lgammaf、lgammal
ms.date: 4/2/2020
api_name:
- lgamma
- lgammaf
- lgammal
- _o_lgamma
- _o_lgammaf
- _o_lgammal
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
ms.openlocfilehash: e2bdfbeac7b995be0b589156437a3ded39114adf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342166"
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

** x <br/>
要计算的值。

## <a name="return-value"></a>返回值

如果成功，返回*x*的 gamma 函数的绝对值的自然对数。

|问题|返回|
|-----------|------------|
|*x* = NaN|NaN|
|*x* = |0|+INFINITY|
|*x*= 负整数|+INFINITY|
|*无限|+INFINITY|
|极点错误|+ HUGE_VAL、+ HUGE_VALF，或 + HUGE_VALL|
|溢出范围错误|[HUGE_VAL、HUGE_VALF 或 HUGE_VALL|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**lgamma**的重载，这些重载和返回**浮点**和**长****双**类型。 在 C 程序中 **，lgamma**始终获取并返回**一个双**。

如果 x 是一个合理数字，则此函数返回因子m 的对数 （x - 1）。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**lgamma，** **lgammaf，** **lgaml**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[tgamma、tgammaf、tgammal](tgamma-tgammaf-tgammal.md)<br/>
