---
title: nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
ms.date: 4/2/2020
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
- _o__nextafter
- _o_nextafter
- _o_nextafterf
- _o_nextafterl
- _o_nexttoward
- _o_nexttowardf
- _o_nexttowardl
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
ms.openlocfilehash: 7b1416147ed000dd3dd9a13bd52e41a474a8e9d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338567"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl

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

** x <br/>
要从其开始的浮点值。

*Y*<br/>
要达到的浮点值。

## <a name="return-value"></a>返回值

返回*x*之后返回类型的下一个可表示的浮点值，该值位于*y*方向。 如果*x*和*y*相等，则函数返回*y*，转换为返回类型，无异常触发。 如果*x*不等于*y*，并且结果是非正常或零，则设置**FE_UNDERFLOW**和**FE_INEXACT**浮点异常状态，并返回正确的结果。 如果*x*或*y*是 NAN，则返回值是输入 NA 之一。 如果*x*是有限的，并且结果在类型中是无限的或不可表示的，则返回正确签名的无穷大或 NAN，**则设置FE_OVERFLOW****和FE_INEXACT**浮点异常状态，并将**errno**设置为**ERANGE**。

## <a name="remarks"></a>备注

**下一个**函数和**下一个**函数族是等效的，但*y*的参数类型除外。 如果*x*和*y*相等，则返回的值为*y*转换为返回类型。

由于C++允许重载，因此，如果\<包含 cmath>则可以调用**下一个**和**下**一个返回**浮点**和**长****双**类型的重载。 在 C 程序中，**下一个**和**下**一个始终返回**双**。

**_nextafter**和 **_nextafterf**功能特定于 Microsoft。 **_nextafterf**函数仅在编译 x64 时可用。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头 (C)|必需的标头 (C++)|
|-------------|---------------------------|-------------------------------|
|**下一个**，**下一个，****下一个， 下一个，** **_nextafterf，****下一个**，**下一个**，**下一个**|\<math.h>|\<math.h> 或 \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> 或 \<cfloat>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
