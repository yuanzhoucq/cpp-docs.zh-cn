---
title: log1p，log1pf log1pl2
ms.date: 04/05/2018
apiname:
- log1p
- log1pf
- log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
ms.openlocfilehash: e7984367aa4244a927bb9dabc5533a807d74ac1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524990"
---
# <a name="log1p-log1pf-log1pl"></a>log1p、log1pf、log1pl

计算 1 加上指定值的自然对数。

## <a name="syntax"></a>语法

```C
double log1p(
   double x
);

float log1p(
   float x
); //C++ only

long double log1p(
   long double x
); //C++ only

float log1pf(
   float x
);

long double log1pl(
   long double x
);

```

### <a name="parameters"></a>参数

*x*<br/>
浮点型参数。

## <a name="return-value"></a>返回值

如果成功，则返回自然 (底*e*) 的日志 (*x* + 1)。

否则，可能返回以下值之一：

|输入|结果|SEH 异常|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|非规格化数|与输入相同|UNDERFLOW||
|±0|与输入相同|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|±SNaN|与输入相同|INVALID||
|±QNaN 无限|与输入相同|||

**Errno**如果值设置为 ERANGE *x* =-1。 **Errno**值设置为**EDOM**如果*x* <-1。

## <a name="remarks"></a>备注

**Log1p**函数可能会比使用更精确`log(x + 1)`时*x*接近 0。

由于 c + + 允许重载，可以调用的重载**log1p**采用并返回**float**并**长** **double**类型。 在 C 程序中， **log1p**始终采用并返回**double**。

如果*x*是自然数，此函数返回的阶乘的对数 (*x* -1)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**log1p**， **log1pf**， **log1pl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
