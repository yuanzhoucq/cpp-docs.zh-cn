---
title: erf、erff、erfl、erfc、erfcf、erfcl | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
dev_langs:
- C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b7ab1448c3f1d77ab79266858a19d822b1cdb4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf、erff、erfl、erfc、erfcf、erfcl

计算某个值的误差函数或补余误差函数。

## <a name="syntax"></a>语法

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值。

## <a name="return-value"></a>返回值

**Erf**函数返回高斯误差函数*x*。 **Erfc**函数返回的补余高斯误差函数*x*。

## <a name="remarks"></a>备注

**Erf**函数计算的高斯误差函数*x*，其定义为：

![错误函数 x](media/crt_erf_formula.PNG "CRT_erf_formula")

补余高斯误差函数定义为 1-erf （x)。 **Erf**函数将返回一个值介于-1.0 到 1.0。 无错误返回。 **Erfc**函数返回一个值介于 0 到 2。 如果*x*太大**erfc**、 **errno**变量设置为**ERANGE**。

由于 c + + 允许重载，你可以调用的重载**erf**和**erfc**采用并返回**float**和**长** **double**类型。 在 C 程序中， **erf**和**erfc**始终采用并返回**double**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**erf**， **erff**， **erfl**， **erfc**， **erfcf**， **erfcl**|\<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
