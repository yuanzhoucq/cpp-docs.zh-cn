---
title: exp2、exp2f、exp2l
ms.date: 04/05/2018
apiname:
- exp2
- exp2f
- exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: 70a3b7eb610556d4a26de7cf0aad55affcdbdc94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338826"
---
# <a name="exp2-exp2f-exp2l"></a>exp2、exp2f、exp2l

计算 2 的指定值的幂。

## <a name="syntax"></a>语法

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
指数值。

## <a name="return-value"></a>返回值

如果成功，则返回 2 为底的指数*x*，即 2<sup>x</sup>。 否则，它会返回以下值之一：

|问题|返回|
|-----------|------------|
|*x* = ±0|1|
|*x* = -INFINITY|+0|
|*x* = +INFINITY|+INFINITY|
|*x* = NaN|NaN|
|溢出范围错误|+ HUGE_VAL、+ HUGE_VALF，或 + HUGE_VALL|
|下溢范围错误|正确的结果，舍入后|

按 [_matherr](matherr.md) 中所指定的报告错误。

## <a name="remarks"></a>备注

因为C++允许重载，可以调用的重载**exp2**采用并返回**float**并**长双精度型**类型。 在 C 程序中， **exp2**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**exp**， **expf**，**资源管理器**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
