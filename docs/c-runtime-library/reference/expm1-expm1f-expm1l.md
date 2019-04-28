---
title: expm1、expm1f、expm1l
ms.date: 04/05/2018
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 5971f879ecef7d4fa1027849cc44d598e877b5f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334978"
---
# <a name="expm1-expm1f-expm1l"></a>expm1、expm1f、expm1l

计算以 e 为底的指数减一的值。

## <a name="syntax"></a>语法

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点指数值。

## <a name="return-value"></a>返回值

**Expm1**函数将返回表示 e 的浮点值<sup>x</sup> -1，如果成功。 在溢出时， **expm1**返回**HUGE_VAL**， **expm1f**返回**HUGE_VALF**， **expm1l**返回**HUGE_VALL**，并**errno**设置为**ERANGE**。 有关返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

因为C++允许重载，可以调用的重载**expm1**采用并返回**float**并**长** **double**值。 在 C 程序中， **expm1**始终采用并返回**double**。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**expm1**， **expm1f**， **expm1l**|\<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[exp2、exp2f、exp2l](exp2-exp2f-exp2l.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
