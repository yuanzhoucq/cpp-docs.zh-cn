---
title: "difftime, _difftime32, _difftime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_difftime32"
  - "difftime"
  - "_difftime64"
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
  - "_difftime64"
  - "difftime"
  - "difftime64"
  - "_difftime32"
  - "difftime32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_difftime32 函数"
  - "difftime 函数"
  - "时间, 查找差异"
  - "difftime64 函数"
  - "_difftime64 函数"
  - "difftime32 函数"
ms.assetid: 4cc0ac2b-fc7b-42c0-8283-8c9d10c566d0
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# difftime, _difftime32, _difftime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

查找两次时间之间的差异。  
  
## 语法  
  
```  
double difftime(   
   time_t timer1,  
   time_t timer0   
);  
double _difftime32(   
   __time32_t timer1,  
   __time32_t timer0   
);  
double _difftime64(   
   __time64_t timer1,  
   __time64_t timer0   
);  
```  
  
#### 参数  
 `timer1`  
 结束时间。  
  
 `timer0`  
 开始时间。  
  
## 返回值  
 `difftime` 返回从 `timer0` 到 `timer1` 流逝的时间（以秒为单位）。 返回值为双精度浮点数字。 返回值可能为 0，表示错误。  
  
## 备注  
 `difftime` 函数计算两个提供的时间值 `timer0` 和 `timer1` 之间的差异。  
  
 提供的时间值必须在 `time_t` 范围内。`time_t` 是 64 位值。 因此，范围的末尾已从扩展 23:59:59 2038 年 1 月 18 日，UTC 到 23:59:59，3000 年 12 月 31 日。`time_t` 的范围下限仍为 1970 年 1 月 1 日午夜。  
  
 `difftime` 是计算结果为 `_difftime32` 或 `_difftime64` 的内联函数，计算结果取决于是否定义了 `_USE_32BIT_TIME_T`。 \_difftime32 和 \_difftime64 可直接用于强制使用数据类型的特定大小。  
  
 这些函数验证其参数。 如果参数是零或负数，无效参数处理程序将调用，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回 0 并设置 `errno` 到 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`difftime`|\<time.h\>|  
|`_difftime32`|\<time.h\>|  
|`_difftime64`|\<time.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
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
使用随机浮点数字 1.04749e + 038 2.01482e + 038 1.72737e + 038Multiplying 2 浮点数字 100 万次...程序需要 3 秒钟。浮点乘法 2 500 万次点数...Program takes      5 seconds.  
```  
  
## .NET Framework 等效项  
 [System::DateTime::Subtract](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [时间管理](../../c-runtime-library/time-management.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)