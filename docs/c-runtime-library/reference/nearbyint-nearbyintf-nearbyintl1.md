---
title: nearbyint、nearbyintf、nearbyintl
ms.date: 4/2/2020
api_name:
- nearbyint
- nearbyintf
- nearbyintl
- _o_nearbyint
- _o_nearbyintf
- _o_nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 92e3a744ef8069d45733c06b7a2681905c3eab55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338588"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint、nearbyintf、nearbyintl

将指定的浮点值舍入为整数，并以浮点格式返回该值。

## <a name="syntax"></a>语法

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>参数

** x <br/>
要舍入的值。

## <a name="return-value"></a>返回值

如果成功，则使用[fegetround](fegetround-fesetround2.md)报告的当前舍入格式返回*x*， 四舍五入到最接近的整数。 否则，该函数返回以下值之一：

|问题|返回|
|-----------|------------|
|*x* = [无穷大]|*INFINITY，未修改|
|*x* = |0|±0，未修改|
|*x* = NaN|NaN|

错误不会通过[_matherr](matherr.md)报告;具体而言，此函数不报告任何**FE_INEXACT**异常。

## <a name="remarks"></a>备注

此函数和[rint](rint-rintf-rintl.md)之间的主要区别是此函数不引发不准确的浮点异常。

因为最大浮点值均为精确的整数，所以此函数本身不会溢出；而输出可能会溢出返回值，具体取决于所使用函数的版本。

C++允许重载，因此您可以调用带和返回**浮点**或**长****双**参数**的附近 int**的重载。 在 C 程序中，**附近的 int**始终采用两个双精度值并返回一个双精度值。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**附近，****附近，****附近**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[数学和浮点支持](../floating-point-support.md)<br/>
