---
title: "_ftime, _ftime32, _ftime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ftime64"
  - "_ftime"
  - "_ftime32"
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
  - "_ftime32"
  - "_ftime"
  - "_ftime64"
  - "ftime64"
  - "ftime"
  - "ftime32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ftime64 函数"
  - "_ftime64 函数"
  - "当前时间"
  - "_ftime 函数"
  - "ftime 函数"
  - "_ftime32 函数"
  - "ftime32 函数"
  - "时间, 获取当前"
ms.assetid: 96bc464c-3bcd-41d5-a212-8bbd836b814a
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _ftime, _ftime32, _ftime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取当前时间。  提供这些函数的更多安全版本；请参见 [\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)。  
  
## 语法  
  
```  
void _ftime(   
   struct _timeb *timeptr   
);  
void _ftime32(   
   struct __timeb32 *timeptr   
);  
void _ftime64(   
   struct __timeb64 *timeptr   
);  
```  
  
#### 参数  
 `timeptr`  
 指向`_timeb`，`__timeb32`, 或 `__timeb64` 结构的指针。  
  
## 备注  
 `_ftime` 函数获取当前本地时间并将其存储结构指向的 `timeptr`*。*`_timeb` `__timeb32`,和 `__timeb64` 结构在SYS\\Timeb.h中定义。  这些包含四个字段，下表中列出。  
  
 `dstflag`  
 如果非零，夏时制实际当前用于本地时区。\(说明如何为夏时制参见 [\_tzset](../../c-runtime-library/reference/tzset.md) 确定。\)  
  
 `millitm`  
 和的毫秒。  
  
 `time`  
 午夜时间为 \(00:00: 00\)，1970 年 1 月 1 日，协调通用时间 \(UTC\)。  
  
 `timezone`  
 区别在于分钟，移动到西，UTC 与本地时间之间。  值 `timezone` 是从全局变量设置 `_timezone` 的值 \(请参见 `_tzset`\)。  
  
 `_ftime64`，使用 `__timeb64` 结构，允许文件创建日期，3000 年 12 月 31 日23:59:59，UTC;而 `_ftime32` 是表示日期2038 年1 月 19 日03:14:07，UTC。  1970 年 1 月 1 日 00:00:00，是所有这些函数的下限的日期范围。  
  
 `_ftime` 与 `_ftime64` 等效，`_timeb` 包含 64 位时。  这符合，除非\_`_USE_32BIT_TIME_T` 定义旧行为，在实际情况下为；\_`_ftime` 使用 32 位时，`_timeb` 包含 32 位时。  
  
 `_ftime`验证其参数。  如果 `timeptr` 传递 null 指针，函数会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则该函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_ftime`|\<sys\/types.h 和\> sys \<\/timeb.h\>|  
|`_ftime32`|\<sys\/types.h 和\> sys \<\/timeb.h\>|  
|`_ftime64`|\<sys\/types.h 和\> sys \<\/timeb.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_ftime.c  
// compile with: /W3  
// This program uses _ftime to obtain the current  
// time and then stores this time in timebuffer.  
  
#include <stdio.h>  
#include <sys/timeb.h>  
#include <time.h>  
  
int main( void )  
{  
   struct _timeb timebuffer;  
   char timeline[26];  
   errno_t err;  
   time_t time1;  
   unsigned short millitm1;  
   short timezone1;  
   short dstflag1;  
  
   _ftime( &timebuffer ); // C4996  
   // Note: _ftime is deprecated; consider using _ftime_s instead  
  
   time1 = timebuffer.time;  
   millitm1 = timebuffer.millitm;  
   timezone1 = timebuffer.timezone;  
   dstflag1 = timebuffer.dstflag;  
  
   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",   
   time1);  
   printf( "Milliseconds: %d\n", millitm1);  
   printf( "Minutes between UTC and local time: %d\n", timezone1);  
   printf( "Daylight savings time flag (1 means Daylight time is in "  
           "effect): %d\n", dstflag1);   
  
   err = ctime_s( timeline, 26, & ( timebuffer.time ) );  
   if (err)  
   {  
       printf("Invalid argument to ctime_s. ");  
   }  
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,  
           &timeline[20] );  
}  
```  
  
  **1970 年 1 月 1 日午夜 \(UTC\):1051553334**  
**230 毫秒**  
**UTC 与本地时间之间的分钟：480**  
**夏时制标志 \(1 表示夏时制时间实际上是\):1**  
**时间是2003年4月28日 11:08:54.230 星期一**    
## .NET Framework 等效项  
 [System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)