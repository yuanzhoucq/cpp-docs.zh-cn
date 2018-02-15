---
title: "clock | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d56f29f1693fba1f4b455d8ae80ee38603e3a604
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="clock"></a>clock
计算调用进程所用的时钟时间。  
  
## <a name="syntax"></a>语法  
  
```  
clock_t clock( void );  
```  
  
## <a name="return-value"></a>返回值  
自进程开始 CRT 初始化后的运行时间，以每秒 `CLOCKS_PER_SEC` 单位数进行测量。 如果运行时间不可用或已超出可记录为 `clock_t` 类型的最大正时间，该函数将返回值 `(clock_t)(-1)`。   
  
## <a name="remarks"></a>备注  
`clock` 函数指示在进程开始期间自 CRT 初始化以来所经过的时钟时间。 请注意，此函数并不严格遵守 ISO C，它将净 CPU 时间指定为返回值。 若要获取 CPU 时间，请使用 Win32 [GetProcessTimes](https://msdn.microsoft.com/library/windows/desktop/ms683223) 函数。 若要确定运行时间（以秒为单位），将 `clock` 函数返回的值除以宏 `CLOCKS_PER_SEC`。  
  
只要有足够的时间，`clock` 返回的值就可能超过 `clock_t` 的最大正值。 当进程运行更长时间后，`clock` 返回的值始终为 `(clock_t)(-1)`，如 ISO C99 标准 (7.23.2.1) 和 ISO C11 标准 (7.27.2.1) 中所指定的那样。 Microsoft 将 `clock_t` 实现为 `long`，这是一个带符号的 32 位整数，将 `CLOCKS_PER_SEC` 宏定义为 1000。 这样，`clock` 函数的最大返回值为 2147483.647 秒，或大约 24.8 天。 不依赖于运行时间超过此时间的进程中 `clock` 返回的值。 可以使用 64 位 `time` 函数或 Windows [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904) 函数来记录多年进程运行时间。  

## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`clock`|\<time.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
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
 [时间管理](../../c-runtime-library/time-management.md)   
 [difftime、_difftime32、_difftime64](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)