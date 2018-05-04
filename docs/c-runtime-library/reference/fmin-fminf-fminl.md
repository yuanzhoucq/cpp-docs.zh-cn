---
title: fmin，fminf，fminl |Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abf16c4cc21d1dc396f0b81aadc8d495c6bdd4b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fmin-fminf-fminl"></a>fmin、fminf、fminl

确定两个指定值的较小值。

## <a name="syntax"></a>语法

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
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

如果成功，将返回较小的*x*或*y*。

|输入|结果|
|-----------|------------|
|*x*为 NaN|*y*|
|*y*为 NaN|*x*|
|*x*和*y*是 NaN|NaN|

该函数不会导致[_matherr](matherr.md)要调用会导致任何浮点异常，或更改的值**errno**。

## <a name="remarks"></a>备注

由于 c + + 允许重载，你可以调用的重载**fmin**采用并返回**float**和**长** **double**类型。 在 C 程序中， **fmin**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**fmin**， **fminf**， **fminl**|C：\<math.h><br />C++：\<math.h> 或 \<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
