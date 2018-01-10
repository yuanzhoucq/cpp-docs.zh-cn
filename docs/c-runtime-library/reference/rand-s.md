---
title: "rand_s | Microsoft 文档"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: rand_s
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
f1_keywords: rand_s
dev_langs: C++
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
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5fde51ee8fb65426166d9d5d2e7d6e5873dd6e8
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2018
---
# <a name="rands"></a>rand_s

生成一个伪随机数。 这是一个更安全的函数版本[rand](../../c-runtime-library/reference/rand.md)，具有安全增强功能中所述[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。 

## <a name="syntax"></a>语法

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>参数

*randomValue*  
指向要保存生成的值的整数的指针。

## <a name="return-value"></a>返回值

如果成功，则返回零，否则返回错误代码。 如果输入的指针_randomValue_是 null 指针，该函数调用无效参数处理程序中, 所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，则函数将返回 `EINVAL`，并且将 `errno` 设置为 `EINVAL`。 如果函数失败的任何其他原因，*_randomValue_设置为 0。

## <a name="remarks"></a>备注

`rand_s` 函数将介于 0 到 `UINT_MAX` 范围内的一个伪随机整数写入输入指针。 `rand_s` 函数使用操作系统生成加密型安全随机数。 它不使用由 [srand](../../c-runtime-library/reference/srand.md) 函数生成的种子，也不影响 `rand` 所使用的随机数序列。

`rand_s` 函数要求在待声明函数的包含语句之前定义常量 `_CRT_RAND_S`，如以下示例所示：

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

`rand_s` 取决于 [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) API，它仅 Windows XP 和更高版本中可用。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`rand_s`|\<stdlib.h>|

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

[浮点支持](../../c-runtime-library/floating-point-support.md)  
[rand](../../c-runtime-library/reference/rand.md)  
[srand](../../c-runtime-library/reference/srand.md)  
