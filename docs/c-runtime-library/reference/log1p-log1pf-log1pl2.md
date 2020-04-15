---
title: log1p、log1pf、log1pl2
ms.date: 4/2/2020
api_name:
- log1p
- log1pf
- log1pl
- _o_log1p
- _o_log1pf
- _o_log1pl
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
ms.openlocfilehash: b4e077f5b806dbe38ed4a4f4e8eef0259170cb7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341813"
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

** x <br/>
浮点型参数。

## <a name="return-value"></a>返回值

如果成功，则返回 （*x* = 1） 的自然 （基 *-e*） 日志。

否则，可能返回以下值之一：

|输入|结果|SEH 异常|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|非规格化数|与输入相同|UNDERFLOW||
|±0|与输入相同|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|*SNaN|与输入相同|INVALID||
|*QNaN，无限期|与输入相同|||

如果*x* = -1，**则 errno**值设置为 ERANGE。 如果*x* < -1，**则 errno**值设置为**EDOM。**

## <a name="remarks"></a>备注

**log1p**函数可能比*当 x*接近`log(x + 1)`0 时使用更准确。

由于C++允许重载，因此可以调用**log1p**的重载，这些重载和返回**浮点**和**长****双**类型。 在 C 程序中 **，log1p**始终采用并返回**一个双**。

如果*x*是自然数字，则此函数返回 （*x* - 1） 因子的对数。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**日志1p**，**日志1pf**，**日志1pl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
