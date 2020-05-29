---
title: difftime, _difftime32, _difftime64
ms.date: 4/2/2020
api_name:
- _difftime32
- difftime
- _difftime64
- _o__difftime32
- _o__difftime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _difftime64
- difftime
- difftime64
- _difftime32
- difftime32
helpviewer_keywords:
- _difftime32 function
- difftime function
- time, finding the difference
- difftime64 function
- _difftime64 function
- difftime32 function
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
ms.openlocfilehash: e8d9ed3e33935c8e6c788380c02b9ae179dd06e8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914781"
---
# <a name="difftime-_difftime32-_difftime64"></a>difftime, _difftime32, _difftime64

查找两次时间之间的差异。

## <a name="syntax"></a>语法

```C
double difftime( time_t timeEnd, time_t timeStart );
double _difftime32( __time32_t timeEnd, __time32_t timeStart );
double _difftime64( __time64_t timeEnd, __time64_t timeStart );
```

### <a name="parameters"></a>参数

*timeEnd*<br/>
结束时间。

*timeStart*<br/>
开始时间。

## <a name="return-value"></a>返回值

**difftime**返回从*timeStart*到*timeEnd*的运行时间（以秒为单位）。 返回值为双精度浮点数字。 返回值可能为 0，表示错误。

## <a name="remarks"></a>备注

**Difftime**函数计算两个提供的时间值*timeStart*和*timeEnd*之间的差异。

提供的时间值必须在**time_t**范围内。 **time_t**为64位值。 因此，范围的末尾已从 2038 年 1 月 18 日 23:59:59（UTC 时间）延至 3000 年 12 月 31 日 23:59:59。 **Time_t**的下限仍为1970年1月1日午夜。

**difftime**是一种内联函数，其计算结果为 **_difftime32**或 **_difftime64** ，具体取决于是否定义 **_USE_32BIT_TIME_T** 。 _difftime32 和 _difftime64 可直接用于强制使用数据类型的特定大小。

这些函数验证其参数。 如果参数为零或负值，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回0，并将**errno**设置为**EINVAL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**difftime**|\<time.h>|
|**_difftime32**|\<time.h>|
|**_difftime64**|\<time.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
// crt_difftime.c
// This program calculates the amount of time
// needed to do a floating-point multiply 100 million times.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <float.h>

double RangedRand( float range_min, float range_max)
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   return ((double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min);
}

int main( void )
{
   time_t   start, finish;
   long     loop;
   double   result, elapsed_time;
   double   arNums[3];

   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   arNums[0] = RangedRand(1, FLT_MAX);
   arNums[1] = RangedRand(1, FLT_MAX);
   arNums[2] = RangedRand(1, FLT_MAX);
   printf( "Using floating point numbers %.5e %.5e %.5e\n", arNums[0], arNums[1], arNums[2] );

   printf( "Multiplying 2 numbers 100 million times...\n" );

   time( &start );
   for( loop = 0; loop < 100000000; loop++ )
      result = arNums[loop%3] * arNums[(loop+1)%3];
   time( &finish );

   elapsed_time = difftime( finish, start );
   printf( "\nProgram takes %6.0f seconds.\n", elapsed_time );
}
```

```Output
Using random floating point numbers 1.04749e+038 2.01482e+038 1.72737e+038
Multiplying 2 floating point numbers 100 million times...
Program takes      3 seconds.
```

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[时间管理](../../c-runtime-library/time-management.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
