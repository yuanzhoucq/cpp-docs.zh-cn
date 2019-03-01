---
title: rand
ms.date: 1/02/2018
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 868c6239ac1b86dfc9ac72cc8cc83d1ba3002b4a
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210414"
---
# <a name="rand"></a>rand

通过使用已知且完全可重现的算法生成一个伪随机数。 此函数的以编程方式更安全版本可用，请参阅[rand_s](rand-s.md)。 由生成编号**rand**不是安全加密。 有关详细信息进行了安全加密随机数字生成，使用[rand_s](rand-s.md)或函数声明的 c + + 标准库中[\<随机 >](../../standard-library/random.md)。

## <a name="syntax"></a>语法

```C
int rand( void );
```

## <a name="return-value"></a>返回值

**rand**返回伪随机数字，如上文所述。 无错误返回。

## <a name="remarks"></a>备注

**Rand**函数在范围 0 到返回一个伪随机整数**RAND_MAX** (32767)。 使用[srand](srand.md)函数之前调用伪随机数生成器的种子**rand**。

**Rand**函数生成的已知序列并不适合用作加密功能。 有关详细信息进行了安全加密随机数字生成，使用[rand_s](rand-s.md)或函数声明的 c + + 标准库中[\<随机 >](../../standard-library/random.md)。 有关什么是不妥**rand**以及如何\<随机 > 处理这些不足，请参阅本视频中标题为[rand 视为有害](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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
