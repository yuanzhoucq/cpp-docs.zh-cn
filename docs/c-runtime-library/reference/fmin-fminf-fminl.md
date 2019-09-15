---
title: fmin、fminf、fminl
ms.date: 04/05/2018
api_name:
- fmin
- fminf
- fminl
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
ms.openlocfilehash: df01f2205291920b8c0519db622c93048278beb1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957096"
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

如果成功，则返回*x*或*y*中的较小者。

|输入|结果|
|-----------|------------|
|*x*为 NaN|*y*|
|*y*为 NaN|*x*|
|*x*和*y*为 NaN|NaN|

函数不会导致调用[_matherr](matherr.md) ，导致任何浮点异常或更改**errno**的值。

## <a name="remarks"></a>备注

由于C++允许重载，因此可以调用**fmin**的重载，该重载采用和返回**float**和**long** **double**类型。 在 C 程序中， **fmin**始终采用并返回**双精度型**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**fmin**、 **fminf**、 **fminl**|C：\<math.h><br />C++：\<math.h> 或 \<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
