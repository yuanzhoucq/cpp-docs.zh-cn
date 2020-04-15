---
title: erf、erff、erfl、erfc、erfcf、erfcl
ms.date: 4/2/2020
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
- _o_erf
- _o_erfc
- _o_erfcf
- _o_erfcl
- _o_erff
- _o_erfl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: ad7ad279d3686e4f33a6f5f901c60348c131b89a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347913"
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

** x <br/>
浮点值。

## <a name="return-value"></a>返回值

**erf**函数返回*x*的高斯错误函数 。 **erfc**函数返回*x*的互补高斯误差函数。

## <a name="remarks"></a>备注

**erf**函数计算*x*的高斯误差函数，该函数定义为：

![x 的错误函数](media/crt_erf_formula.PNG "x 的错误函数")

互补高斯误差函数定义为 1 - erf（x）。 **erf**函数返回范围 -1.0 到 1.0 中的值。 无错误返回。 **erfc**函数返回范围 0 到 2 中的值。 如果*x*对于**erfc**来说太大，则**errno**变量设置为**ERANGE**。

由于C++允许重载，因此可以调用获取和返回**浮点**和**长****双**类型的**erf**和**erfc**的重载。 在C程序中 **，erf**和**erfc**总是采取并返回**一个双**。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**埃尔夫**，**埃尔夫**，**埃尔弗尔**，**埃尔夫夫**，**埃尔夫夫**，**埃尔夫**|\<math.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
