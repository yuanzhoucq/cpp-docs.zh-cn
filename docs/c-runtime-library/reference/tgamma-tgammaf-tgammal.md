---
title: tgamma、tgammaf、tgammal
ms.date: 4/2/2020
api_name:
- tgamma
- tgammaf
- tgammal
- _o_tgamma
- _o_tgammaf
- _o_tgammal
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
ms.openlocfilehash: d7e27e8b818a16cb0c18f58e2f40c0090dd13ecf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362507"
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

** x <br/>
要查找其伽玛值的值。

## <a name="return-value"></a>返回值

如果成功，则返回*x*的 gamma。

如果*x*的大小对于数据类型来说太大或太小，则可能发生范围错误。 如果*x* <= 0，则可能发生域错误或范围错误。

|问题|返回|
|-----------|------------|
|x = |0|*无限|
|x = 负整数|NaN|
|x = -INFINITY|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|域错误|NaN|
|极点错误|[HUGE_VAL、HUGE_VALF 或 HUGE_VALL|
|溢出范围错误|[HUGE_VAL、HUGE_VALF 或 HUGE_VALL|
|下溢范围错误|舍入后的正确值。|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用带和返回**浮点**和**长****双**类型的**tgamma**重载。 在 C 程序中 **，tgamma**始终获取并返回**一个双**。

如果 x 是自然数，则此函数返回 (x-1) 的阶乘。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**特伽马**，**特伽马夫**，**特加玛尔**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[lgamma、lgammaf、lgammal](lgamma-lgammaf-lgammal.md)<br/>
