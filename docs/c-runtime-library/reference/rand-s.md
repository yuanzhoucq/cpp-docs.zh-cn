---
title: rand_s | Microsoft 文档
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rand_s
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
- rand_s
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8407848db8f442324127df8d7267a5350c077b2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="rands"></a>rand_s

生成一个伪随机数。 这是一个更安全的函数版本[rand](rand.md)，具有安全增强功能中所述[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。

## <a name="syntax"></a>语法

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>参数

*randomValue*<br/>
指向要保存生成的值的整数的指针。

## <a name="return-value"></a>返回值

如果成功，则返回零，否则返回错误代码。 如果输入的指针_randomValue_是 null 指针，该函数调用无效参数处理程序中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将返回**EINVAL**和设置**errno**到**EINVAL**。 如果函数失败的任何其他原因，*_randomValue_设置为 0。

## <a name="remarks"></a>备注

**Rand_s**函数范围为 0 到中写入一个伪随机整数**UINT_MAX**到的输入指针。 **Rand_s**函数使用操作系统来生成加密性极安全的随机数字。 它不使用由生成的种子[srand](srand.md)函数，也不会影响使用的随机数字序列[rand](rand.md)。

**Rand_s**函数需要该常量 **_CRT_RAND_S**之前，当函数为声明，如以下示例所示的包含语句定义：

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

**rand_s**取决于[RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) API，才可在 Windows XP 及更高版本。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**rand_s**|\<stdlib.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
[srand](srand.md)<br/>
