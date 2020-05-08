---
title: rand_s
ms.date: 4/2/2020
api_name:
- rand_s
- _o_rand_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand_s
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: cad1740e64c7bbda553ac1a6c777d7e2295152ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919540"
---
# <a name="rand_s"></a>rand_s

生成一个伪随机数。 这是函数[rand](rand.md)的更安全版本，具有[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增强功能。

## <a name="syntax"></a>语法

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>参数

*randomValue*<br/>
指向用于保存生成值的整数的指针。

## <a name="return-value"></a>返回值

如果成功，则返回零，否则返回错误代码。 如果输入指针_randomValue_为空指针，则函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回**EINVAL** ，并将**Errno**设置为**EINVAL**。 如果函数因任何其他原因而失败，则 *_randomValue_将设置为0。

## <a name="remarks"></a>备注

**Rand_s**函数将 0 **UINT_MAX**到1之间的伪随机整数写入到输入指针。 **Rand_s**函数使用操作系统生成加密安全的随机数字。 它不使用由[srand](srand.md)函数生成的种子，也不会影响[rand](rand.md)使用的随机数字序列。

**Rand_s**函数要求在要声明的函数的包含语句之前定义常量 **_CRT_RAND_S** ，如以下示例中所示：

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s**依赖于[RtlGenRandom](/windows/win32/api/ntsecapi/nf-ntsecapi-rtlgenrandom) API，该 API 仅在 Windows XP 和更高版本中可用。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

有关详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number /
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>示例输出

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
