---
title: rand | Microsoft 文档
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rand
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
- rand
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5289b27ae0749d85b3e4ee60717212acc95536d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405700"
---
# <a name="rand"></a>rand

通过使用的已知和完全可重现的算法生成一个伪随机数。 有可用; 此函数的以编程方式更安全版本请参阅[rand_s](rand-s.md)。 由生成编号**rand**不安全加密。 有关详细信息加密型安全随机数生成，使用[rand_s](rand-s.md)或函数声明的 c + + 标准库中[\<随机 >](../../standard-library/random.md)。

## <a name="syntax"></a>语法

```C
int rand( void );
```

## <a name="return-value"></a>返回值

**rand**返回伪随机数，如上面所述。 无错误返回。

## <a name="remarks"></a>备注

**Rand**函数返回一个伪随机整数在范围 0 到**RAND_MAX** (32767)。 使用[srand](srand.md)函数之前调用伪随机数生成器种子**rand**。

**Rand**函数将生成的已知的序列，并不适合用作加密功能。 有关详细信息加密型安全随机数生成，使用[rand_s](rand-s.md)或函数声明的 c + + 标准库中[\<随机 >](../../standard-library/random.md)。 有关问题信息**rand**以及如何\<随机 > 处理这些不足，请参阅[此视频](http://go.microsoft.com/fwlink/?LinkId=397615)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
