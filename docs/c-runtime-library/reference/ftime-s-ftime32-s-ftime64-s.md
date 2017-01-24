---
title: "_ftime_s、_ftime32_s、_ftime64_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ftime_s"
  - "_ftime64_s"
  - "_ftime32_s"
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
  - "_ftime_s"
  - "_ftime64_s"
  - "ftime_s"
  - "_ftime32_s"
  - "ftime32_s"
  - "ftime64_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ftime32_s 函数"
  - "ftime_s 函数"
  - "_ftime64_s 函数"
  - "当前时间"
  - "ftime64_s 函数"
  - "时间, 获取当前"
  - "_ftime_s 函数"
  - "_ftime32_s 函数"
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ftime_s、_ftime32_s、_ftime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取当前时间。 一些版本 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md) 因安全性增强中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
errno_t _ftime_s(   
   struct _timeb *timeptr   
);  
errno_t _ftime32_s(   
   struct __timeb32 *timeptr   
);  
errno_t _ftime64_s(   
   struct __timeb64 *timeptr   
);  
```  
  
#### 参数  
 `timeptr`  
 指向 `_timeb,``__timeb32`, ，或 `__timeb64` 结构。  
  
## 返回值  
 如果成功则为零，失败则返回错误代码。 如果 `timeptr` 为 `NULL`，则返回值为 `EINVAL`。  
  
## 备注  
 `_ftime_s` 函数将获取当前本地时间，并将其存储在所指向的结构 `timeptr`*。*`_timeb,``__timeb32`,，和`__timeb64` SYS\\Timeb.h 中定义结构。 它们包含四个字段下, 表中列出。  
  
 `dstflag`  
 如果为非夏时制当前有效的本地时区。 \(请参阅 [\_tzset](../../c-runtime-library/reference/tzset.md) 有关如何确定夏时制时间的说明。\)  
  
 `millitm`  
 以毫秒为单位秒的小数。  
  
 `time`  
 以秒为单位午夜算起的时间 \(00: 00:00\)、 1970 年 1 月 1 日，格式为协调世界时 \(UTC\)。  
  
 `timezone`  
 UTC 和当地时间之间移动 westward，以分钟为单位差异。 值 `timezone` 设置全局变量的值从 `_timezone` \(请参阅 `_tzset`\)。  
  
 `_ftime64_s`, 它使用 `__timeb64` 结构，请允许文件创建日期来向上表示通过 23:59:59，3000 年 12 月 31 日，UTC; 而 `_ftime32_s` 只代表 23:59:59 2038 年 1 月 18 日，UTC 日期。 午夜 1970 年 1 月 1 日，是所有这些函数的日期范围的下限。  
  
 `_ftime_s` 等效于 `_ftime64_s` 和 `_timeb` 包含 64 位时间。 也是如此除非 \_`USE_32BIT_TIME_T` 定义，则在这种情况下这一旧行为是否生效; \_`ftime_s` 使用 32 位时间和 `_timeb` 包含 32 位时间。  
  
 `_ftime_s` 会验证其参数。 如果传递 null 指针作为 `timeptr`, ，该函数将调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，函数将设置 `errno` 到 `EINVAL`。  
  
## 要求  
  
|函数|必需的标头|  
|--------|-----------|  
|`_ftime_s`|\< sys\/types.h \> 和 \< sys\/timeb.h \>|  
|`_ftime32_s`|\< sys\/types.h \> 和 \< sys\/timeb.h \>|  
|`_ftime64_s`|\< sys\/types.h \> 和 \< sys\/timeb.h \>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_ftime64_s.c  
// This program uses _ftime64_s to obtain the current  
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
  
   _ftime64_s( &timebuffer );  
  
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
  
```Output  
(UTC) 1970 年 1 月 1 日午夜以来的秒︰ 1051553334 毫秒︰ 230 UTC 与当地时间之间的分钟︰ 480 夏令时标志 （夏时制时间的效力范围是 1 表示）︰ 1 的时间是星期一 Apr 28 11:08:54.230 2003年  
```  
  
## .NET Framework 等效项  
 [System::DateTime::Now](https://msdn.microsoft.com/en-us/library/system.datetime.now.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)