---
title: ilogb、ilogbf、ilogbl2 | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc15d09b2e2ff79771b2be4250ea1ea770a02f31
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
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

如果成功，返回 2 为底的指数*x*作为一个已签名**int**值。

否则将返回在 \<math.h> 中定义的以下值之一：

|输入|结果|
|-----------|------------|
|±0|FP_ILOGB0|
|±inf，±nan，无限期|FP_ILOGBNAN|

按 [_matherr](matherr.md) 中指定的内容报告错误。

## <a name="remarks"></a>备注

由于 c + + 允许重载，你可以调用的重载**ilogb**采用并返回**float**和**长** **double**类型。 在 C 程序中， **ilogb**始终采用并返回**double**。

调用此函数是类似于调用的等效方法**logb**函数，然后将返回值转换为**int**。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**ilogb**， **ilogbf**， **ilogbl**|\<math.h>|\<cmath>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb、logbf、logbl、_logb、_logbf](logb-logbf-logbl-logb-logbf.md)<br/>
