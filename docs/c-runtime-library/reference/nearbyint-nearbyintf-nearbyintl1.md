---
title: nearbyint、nearbyintf、nearbyintl
ms.date: 04/05/2018
apiname:
- nearbyint
- nearbyintf
- nearbyintl
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
ms.openlocfilehash: 827286c840c6564c8c3f8b351197b0201509d241
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156195"
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

*x*<br/>
要舍入的值。

## <a name="return-value"></a>返回值

如果成功，则返回*x*，并舍入为最接近的整数，使用当前舍入格式报告[fegetround](fegetround-fesetround2.md)。 否则，该函数返回以下值之一：

|问题|返回|
|-----------|------------|
|*x* = ±INFINITY|±INFINITY，以未修改形式|
|*x* = ±0|±0，以未修改形式|
|*x* = NaN|NaN|

通过不报告错误[_matherr](matherr.md); 具体而言，此函数不会报告任何**FE_INEXACT**异常。

## <a name="remarks"></a>备注

此函数的主要区别和[rint](rint-rintf-rintl.md)是此函数不会引发不精确的浮点异常。

因为最大浮点值均为精确的整数，所以此函数本身不会溢出；而输出可能会溢出返回值，具体取决于所使用函数的版本。

C++允许重载，因此可以调用的重载**nearbyint**采用并返回**float**或**长** **double**参数。 在 C 程序中， **nearbyint**始终采用两个双精度值并返回一个双精度值。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**nearbyint**， **nearbyintf**， **nearbyintl**|\<math.h>|\<cmath> 或 \<math.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[数学和浮点支持](../floating-point-support.md)<br/>
