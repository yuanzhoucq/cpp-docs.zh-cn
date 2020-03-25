---
title: abs、labs、llabs、_abs64
ms.date: 04/05/2018
api_name:
- abs
- _abs64
- labs
- llabs
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
ms.openlocfilehash: a21bdbcb54d7fecf00b3c782c562d60ccc866dcc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171406"
---
# <a name="abs-labs-llabs-_abs64"></a>abs、labs、llabs、_abs64

计算参数的绝对值。

## <a name="syntax"></a>语法

```C
int abs( int n );
long labs( long n );
long long llabs( long long n );
__int64 _abs64( __int64 n );
```

```cpp
long abs( long n );   // C++ only
long long abs( long long n );   // C++ only
double abs( double n );   // C++ only
long double abs( long double n );   // C++ only
float abs( float n );   // C++ only
```

### <a name="parameters"></a>parameters

*n*<br/>
数值。

## <a name="return-value"></a>返回值

**Abs**、 **labs**、 **llabs**和 **_abs64**函数返回参数*n*的绝对值。 无错误返回。

## <a name="remarks"></a>备注

由于C++允许重载，因此你可以调用采用并返回**long**、 **long** **、** **float**、 **double**和**long** **双精度**值的**abs**重载。 这些重载在 \<cmath> 标头中进行定义。 在 C 程序中， **abs**始终采用并返回**int**。

**Microsoft 专用**：由于可使用任何整型类型表示的负整数的范围大于可使用该类型表示的正整数的范围，因此，可以为这些不能转换的函数提供参数。 如果参数的绝对值不能由返回类型表示，则**abs**函数返回的参数值保持不变。 具体而言，`abs(INT_MIN)` 返回 `INT_MIN`、`labs(LONG_MIN)` 返回 `LONG_MIN`、`llabs(LLONG_MIN)` 返回 `LLONG_MIN`，`_abs64(_I64_MIN)` 返回 `_I64_MIN`。 这意味着不能使用**abs**函数来保证正值。

## <a name="requirements"></a>要求

|例程|必需的 C 标头|必需的 C++ 标头|
|-------------|-----------------------|---------------------------|
|**abs**、 **labs**、 **llabs**|\<math.h> 或 \<stdlib.h>|\<cmath>、\<cstdlib>、\<stdlib.h> 或 \<math.h>|
|**_abs64**|\<stdlib.h>|\<cstdlib> 或 \<stdlib.h>|

若要在中C++使用**abs**的重载版本，必须包含 \<h > 标头。

## <a name="example"></a>示例

此程序计算并显示几个数字的绝对值。

```C
// crt_abs.c
// Build: cl /W3 /TC crt_abs.c
// This program demonstrates the use of the abs function
// by computing and displaying the absolute values of
// several numbers.

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <limits.h>

int main( void )
{
    int ix = -4;
    long lx = -41567L;
    long long llx = -9876543210LL;
    __int64 wx = -1;

    // absolute 32 bit integer value
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));

    // absolute long integer value
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));

    // absolute long long integer value
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));

    // absolute 64 bit integer value
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,
        _abs64(wx));

    // Integer error cases:
    printf_s("Microsoft implementation-specific results:\n");
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));
}
```

```Output
The absolute value of -4 is 4
The absolute value of -41567 is 41567
The absolute value of -9876543210 is 9876543210
The absolute value of 0xffffffffffffffff is 0x0000000000000001
Microsoft implementation-specific results:
abs(INT_MIN) returns -2147483648
labs(LONG_MIN) returns -2147483648
llabs(LLONG_MIN) returns -9223372036854775808
_abs64(_I64_MIN) returns 0x8000000000000000
```

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)
