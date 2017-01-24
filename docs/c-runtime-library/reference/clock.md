---
title: "clock | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "clock"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "clock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "计算使用的处理器时间"
  - "clock 函数"
  - "使用的处理器时间"
  - "使用的处理器时间, 计算"
  - "时间, 计算处理器"
ms.assetid: 3e1853dd-498f-49ba-b06a-f2315f20904e
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# clock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

计算调用进程所用的时钟时间。  
  
## 语法  
  
```  
clock_t clock( void );  
```  
  
## 返回值  
 自进程启动后已用的时钟时间（以秒为单位的运行时间乘以 `CLOCKS_PER_SEC`）。  如果运行时间量不可用，则函数返回 \-1，并强制转换为 `clock_t`。  
  
## 备注  
 `clock` 函数告知调用进程已用的时钟时间。  请注意，这并不严格遵守 ISO C99（它将净 CPU 时间指定为返回值）。  若要获取 CPU 时间，请使用 Win32 [GetProcessTimes](http://msdn.microsoft.com/library/windows/desktop/ms683223) 函数。  
  
 计时器刻度约等于 1\/`CLOCKS_PER_SEC` 秒。  只要有足够的时间，`clock` 返回的值便可能会超过 `clock_t` 的最大正值，从而变为负值，或超过最大绝对值并滚动更新。  对于运行超过 214,748 秒（即大约 59 小时）的进程中的总运行时间，不要依赖此值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`clock`|\<time.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_clock.c  
// This example prompts for how long  
// the program is to run and then continuously  
// displays the elapsed time for that period.  
//  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <time.h>  
  
void sleep( clock_t wait );  
  
int main( void )  
{  
   long    i = 6000000L;  
   clock_t start, finish;  
   double  duration;  
  
   // Delay for a specified time.  
   printf( "Delay for three seconds\n" );  
   sleep( (clock_t)3 * CLOCKS_PER_SEC );  
   printf( "Done!\n" );  
  
   // Measure the duration of an event.  
   printf( "Time to do %ld empty loops is ", i );  
   start = clock();  
   while( i-- )   
      ;  
   finish = clock();  
   duration = (double)(finish - start) / CLOCKS_PER_SEC;  
   printf( "%2.1f seconds\n", duration );  
}  
  
// Pauses for a specified number of milliseconds.  
void sleep( clock_t wait )  
{  
   clock_t goal;  
   goal = wait + clock();  
   while( goal > clock() )  
      ;  
}  
```  
  
  **Delay for three seconds**  
**Done\!  Time to do 6000000 empty loops is 0.1 seconds**    
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [difftime, \_difftime32, \_difftime64](../../c-runtime-library/reference/difftime-difftime32-difftime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)