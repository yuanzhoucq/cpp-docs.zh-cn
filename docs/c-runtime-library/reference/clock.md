---
title: clock | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- processor time used, calculating
- time, calculating processor
- clock function
- processor time used
- calculating processor time used
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd4b399900802d110ff5746a0ccb2424ba40e6b5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209861"
---
# <a name="clock"></a>clock

计算调用进程所用的时钟时间。

## <a name="syntax"></a>语法

```C
clock_t clock( void );
```

## <a name="return-value"></a>返回值

该过程中，CRT 初始化开始时起经过的时间单位**CLOCKS_PER_SEC**单位 / 秒。 如果运行时间不可用或已超出可记录为的最大正时间**clock_t**类型，该函数返回的值`(clock_t)(-1)`。

## <a name="remarks"></a>备注

**时钟**函数则指出期间进程开始 CRT 初始化以来经过的时钟时间。 请注意，此函数并不严格遵守 ISO C，它将净 CPU 时间指定为返回值。 若要获取 CPU 时间，请使用 Win32 [GetProcessTimes](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getprocesstimes) 函数。 若要确定所经过的时间以秒为单位，将返回的值**时钟**函数由宏**CLOCKS_PER_SEC**。

只要有足够的时间，返回的值**时钟**可能会超过最大正值**clock_t**。 当进程运行更长，返回的值**时钟**始终`(clock_t)(-1)`、 所指定的 ISO C99 标准 (7.23.2.1) 和 ISO C11 标准 (7.27.2.1)。 Microsoft 实现**clock_t**作为**长**，带符号的 32 位整数，并且**CLOCKS_PER_SEC**宏定义为 1000年。 这样，最多**时钟**函数返回值为 2147483.647 秒，或大约 24.8 天。 不要依赖于返回的值**时钟**的进程中的运行时间超过此时间的时间。 可以使用 64 位[时间](time-time32-time64.md)函数或 Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904)多年的记录进程运行时间的函数。

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
