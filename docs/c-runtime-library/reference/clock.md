---
title: clock
ms.date: 11/04/2016
apiname:
- clock
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clock
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
ms.openlocfilehash: 2fabd18fb28cb5ea13dfb156ea21e8743c2afd49
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500261"
---
# <a name="clock"></a>clock

计算调用进程所用的时钟时间。

## <a name="syntax"></a>语法

```C
clock_t clock( void );
```

## <a name="return-value"></a>返回值

自进程开始 CRT 初始化以来经过的时间, 以**CLOCKS_PER_SEC**单位/秒为单位。 如果运行时间不可用或已超过可记录为**clock_t**类型的最大正时间, 则函数将返回值`(clock_t)(-1)`。

## <a name="remarks"></a>备注

**时钟**函数告诉您自开始处理 CRT 初始化以来已经过了多少时钟时间。 请注意，此函数并不严格遵守 ISO C，它将净 CPU 时间指定为返回值。 若要获取 CPU 时间，请使用 Win32 [GetProcessTimes](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) 函数。 若要确定运行时间 (以秒为单位), 请使用宏**CLOCKS_PER_SEC**将**时钟**函数返回的值相除。

如果有足够的时间, 则**时钟**返回的值可能会超过**clock_t**的最大正值。 当进程运行时间较长时, 由 C99 返回的值始终`(clock_t)(-1)`由 iso standard (7.23.2.1) 和 iso C11 standard (7.27.2.1) 指定。 Microsoft 将**clock_t**实现为**长**、有符号的32位整数, 并将**CLOCKS_PER_SEC**宏定义为1000。 这将提供最大**时钟**函数返回值2147483.647 秒, 即约24.8 天。 不要依赖于运行时间超过此时间的进程中**时钟**返回的值。 可以使用64位[时间](time-time32-time64.md)函数或 Windows [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter)函数记录多年的进程运行时间。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**clock**|\<time.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_clock.c
// This sample uses clock() to 'sleep' for three
// seconds, then determines how long it takes
// to execute an empty loop 600000000 times.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// Pauses for a specified number of milliseconds.
void do_sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}

const long num_loops = 600000000L;

int main( void )
{
   long    i = num_loops;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   do_sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   start = clock();
   while( i-- )
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "Time to do %ld empty loops is ", num_loops );
   printf( "%2.3f seconds\n", duration );
}
```

```Output
Delay for three seconds
Done!
Time to do 600000000 empty loops is 1.354 seconds
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[difftime、_difftime32、_difftime64](difftime-difftime32-difftime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
