---
title: fmax、fmaxf、fmaxl
ms.date: 04/05/2018
apiname:
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 0fbe23a4b7d6e0c59523d62f844dd89e66642933
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465151"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax、fmaxf、fmaxl

确定两个指定数字值的较大值。

## <a name="syntax"></a>语法

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

```

### <a name="parameters"></a>参数

*x*<br/>
要比较的第一个值。

*y*<br/>
要比较的第二个值。

## <a name="return-value"></a>返回值

如果成功，则返回较大的一个*x*或*y*。 返回的为准确值，且不依赖于任何形式的舍入。

否则，可能返回以下值之一：

|问题|返回|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x*并*y* = NaN|NaN|

此函数不使用 [_matherr](matherr.md) 中指定的错误。

## <a name="remarks"></a>备注

由于 C++ 支持重载，可以调用采用并返回浮点型和长双精度型的 fmax 的重载。 在 C 程序中，fmax 始终采用和返回双精度型。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**fmax**， **fmaxf**， **fmaxl**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fmin、fminf、fminl](fmin-fminf-fminl.md)<br/>
