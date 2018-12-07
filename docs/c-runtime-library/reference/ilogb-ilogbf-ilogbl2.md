---
title: ilogb、 ilogbf、 ilogbl2
ms.date: 04/05/2018
apiname:
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
ms.openlocfilehash: 272544124dd8a8a666fc434516d3c45c73b1d011
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519563"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb、ilogbf、ilogbl

检索一个整数，以表示指定值以 2 为底的无偏差指数。

## <a name="syntax"></a>语法

```C
int ilogb(
   double x
);

int ilogb(
   float x
); //C++ only

int ilogb(
   long double x
); //C++ only

int ilogbf(
   float x
);

int ilogbl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
指定的值。

## <a name="return-value"></a>返回值

如果成功，则返回 2 为底的指数*x*以签名**int**值。

否则将返回在 \<math.h> 中定义的以下值之一：

|输入|结果|
|-----------|------------|
|±0|FP_ILOGB0|
|±inf，±nan，无限|FP_ILOGBNAN|

按 [_matherr](matherr.md) 中指定的内容报告错误。

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**ilogb**采用并返回**float**并**长** **double**类型。 在 C 程序中， **ilogb**始终采用并返回**double**。

调用此函数相当于调用等效项**logb**函数，然后将返回值转换为**int**。

## <a name="requirements"></a>要求

|例程所返回的值|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**ilogb**， **ilogbf**， **ilogbl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb、logbf、logbl、_logb、_logbf](logb-logbf-logbl-logb-logbf.md)<br/>
