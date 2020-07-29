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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d599567e38d216e78720a3d6b330310095acdd11
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218580"
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

如果成功，则返回（*x* + 1）的自然（以*e*为底）对数。

否则，可能返回以下值之一：

|输入|结果|SEH 异常|errno|
|-----------|------------|-------------------|-----------|
|+inf|+inf|||
|非规格化数|与输入相同|UNDERFLOW||
|±0|与输入相同|||
|-1|-inf|DIVBYZERO|ERANGE|
|< -1|nan|INVALID|EDOM|
|-inf|nan|INVALID|EDOM|
|± SNaN|与输入相同|INVALID||
|± QNaN，不定|与输入相同|||

如果*x* =-1，则**errno**值设置为 ERANGE。 如果*x* <-1，则将**errno**值设置为**EDOM** 。

## <a name="remarks"></a>备注

**log1p** `log(x + 1)` 当*x*接近0时，log1p 函数可能更准确。

由于 c + + 允许重载，因此你可以调用采用并返回和类型的**log1p**的重载 **`float`** **`long double`** 。 在 C 程序中， **log1p**始终采用并返回 **`double`** 。

如果*x*是自然数，则此函数返回（*x* -1）的阶乘的对数。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**log1p**、 **log1pf**、 **log1pl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[字母函数引用](crt-alphabetical-function-reference.md)<br/>
[log2、log2f、log2l](log2-log2f-log2l.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
