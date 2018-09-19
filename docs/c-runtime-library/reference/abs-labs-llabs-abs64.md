---
title: abs、labs、llabs、_abs64 | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- abs
- _abs64
- labs
- llabs
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
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
dev_langs:
- C++
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1380a6e56ce444e80feccf3e8306a0a589c98d01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085259"
---
# <a name="abs-labs-llabs-abs64"></a>abs、labs、llabs、_abs64

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

### <a name="parameters"></a>参数

*n*<br/>
数值。

## <a name="return-value"></a>返回值

**Abs**，**实验室**， **llabs**并 **_abs64**函数返回参数的绝对值*n*. 无错误返回。

## <a name="remarks"></a>备注

由于 c + + 允许重载，可以调用的重载**abs**采用并返回**长**，**长****长**， **float**，**双**，和**长** **double**值。 这些重载在 \<cmath> 标头中进行定义。 在 C 程序中， **abs**始终采用并返回**int**。

**特定于 Microsoft**： 可以使用任何整型表示的负整数的范围大于可使用该类型表示的正整数的范围，因为它是可以提供这些参数不能转换的函数。 如果自变量的绝对值无法由返回类型，表示**abs**函数返回参数值保持不变。 具体而言，`abs(INT_MIN)` 返回 `INT_MIN`、`labs(LONG_MIN)` 返回 `LONG_MIN`、`llabs(LLONG_MIN)` 返回 `LLONG_MIN`，`_abs64(_I64_MIN)` 返回 `_I64_MIN`。 这意味着**abs**函数不能用于保证正值。

## <a name="requirements"></a>要求

|例程所返回的值|必需的 C 标头|必需的 C++ 标头|
|-------------|-----------------------|---------------------------|
|**abs**，**实验室**， **llabs**|\<math.h> 或 \<stdlib.h>|\<cmath>、\<cstdlib>、\<stdlib.h> 或 \<math.h>|
|**_abs64**|\<stdlib.h>|\<cstdlib> 或 \<stdlib.h>|

若要使用的重载的版本**abs** c + + 中必须包括\<cmath > 标头。

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

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)