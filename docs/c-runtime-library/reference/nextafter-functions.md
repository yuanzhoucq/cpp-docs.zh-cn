---
title: nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
ms.date: 04/05/2018
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: 0e0a60dc9f7c068d8c18c10f3c6b819b9e06d3b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444851"
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl

返回下一个可表示的浮点值。

## <a name="syntax"></a>语法

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>参数

*x*<br/>
要从其开始的浮点值。

*y*<br/>
要达到的浮点值。

## <a name="return-value"></a>返回值

返回之后的返回类型的下一步可表示浮点值*x*的方向*y*。 如果*x*并*y*相等，该函数将返回*y*，已转换为返回类型，且未触发异常。 如果*x*不等于*y*，并且结果为非正规或零， **FE_UNDERFLOW**并**FE_INEXACT**浮点异常状态设置，并返回正确的结果。 如果任一*x*或*y*是 NAN，则返回值为输入 Nan 之一。 如果*x*是有限的结果为无限或无法在类型中表示，正确的有符号无穷大或 NAN 返回的则**FE_OVERFLOW**并**FE_INEXACT**设置浮点异常状态，并**errno**设置为**ERANGE**。

## <a name="remarks"></a>备注

**Nextafter**并**nexttoward**函数系列是等同的只不过参数类型的*y*。 如果*x*并*y*相等，则返回该值*y*转换为返回类型。

由于 c + + 允许重载，如果包括\<cmath > 可以调用的重载**nextafter**并**nexttoward**返回**float**和**长****双**类型。 在 C 程序中， **nextafter**并**nexttoward**始终返回**double**。

**_Nextafter**并 **_nextafterf**是 Microsoft 特定函数的函数。 **_Nextafterf**编译 x64 时，函数才可用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**， **nextafterf**， **nextafterl**， **_nextafterf**， **nexttoward**， **nexttowardf**， **nexttowardl**|\<math.h>|\<math.h> 或 \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> 或 \<cfloat>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
