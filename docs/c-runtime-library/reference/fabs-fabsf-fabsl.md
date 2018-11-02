---
title: fabs、fabsf、fabsl
ms.date: 04/05/2018
apiname:
- fabsf
- fabs
- fabsl
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
ms.openlocfilehash: 8df36c06fb3ca9af9be4cf704998946b3eaf9a6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623556"
---
# <a name="fabs-fabsf-fabsl"></a>fabs、fabsf、fabsl

计算浮点自变量的绝对值。

## <a name="syntax"></a>语法

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);
```

### <a name="parameters"></a>参数

*x*<br/>
浮点值。

## <a name="return-value"></a>返回值

**Fabs**函数返回参数的绝对值*x*。 无错误返回。

|输入|SEH 异常|Matherr 异常|
|-----------|-------------------|-----------------------|
|± QNAN,IND|无|_DOMAIN|

## <a name="remarks"></a>备注

C + + 允许重载，因此可以调用的重载**fabs**如果包括\<cmath > 标头。 在 C 程序中， **fabs**始终采用并返回**double**。

## <a name="requirements"></a>要求

|函数|必需的 C 标头|必需的 C++ 标头|
|--------------|-----------------------|---------------------------|
|**fabs**， **fabsf**， **fabsl**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [abs](abs-labs-llabs-abs64.md) 的示例。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
