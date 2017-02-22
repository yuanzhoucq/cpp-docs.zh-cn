---
title: "time、_time32、_time64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "time"
  - "_time64"
  - "_time32"
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
  - "time"
  - "_time64"
  - "time/time"
  - "time/_time32"
  - "time/_time64"
  - "_time32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time32 函数"
  - "_time32 函数"
  - "_time64 函数"
  - "时间函数"
  - "系统时间"
  - "time64 函数"
ms.assetid: 280e00f2-2b93-4ece-94cd-e048484c6cc7
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# time、_time32、_time64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取系统时间。  
  
## 语法  
  
```  
time_t time(  
   time_t *timer   
);  
__time32_t _time32(  
   __time32_t *timer   
);  
__time64_t _time64(  
   __time64_t *timer   
);  
```  
  
#### 参数  
 `timer`  
 指针指向时间的存储位置。  
  
## 返回值  
 返回自 1970 年 1 月 1 日午夜以来经过的时间，或者如果发生错误返回 \-1。  
  
## 备注  
 `time` 函数根据系统时钟返回自协调世界时 \(UTC\) 1970 年 1 月 1 日午夜 \(00:00:00\) 以来经过的秒数。 返回的值存储在由 `timer` 给定的位置。 此参数可以为 `NULL`，在这种情况下不存储返回值。  
  
 `time` 是 `_time64` 的包装器，并且默认情况下，`time_t` 等效于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；64 位平台上不允许使用此宏。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`time`, `_time32`, `_time64`|C: \<time.h\>、C\+\+: \<ctime\> 或 \<time.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```c  
// crt_times.c  
// compile with: /W3  
// This program demonstrates these time and date functions:  
//      time         _ftime    ctime_s     asctime_s  
//      _localtime64_s    _gmtime64_s    mktime    _tzset  
//      _strtime_s     _strdate_s  strftime  
//  
// Also the global variable:  
//      _tzname  
//  
// Turn off deprecated unsafe CRT function warnings  
#define _CRT_SECURE_NO_WARNINGS 1  
  
#include <time.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/timeb.h>  
#include <string.h>  
  
int main()  
{  
    char tmpbuf[128], timebuf[26], ampm[] = "AM";  
    time_t ltime;  
    struct _timeb tstruct;  
    struct tm today, gmt, xmas = { 0, 0, 12, 25, 11, 93 };  
    errno_t err;  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    // Display operating system-style date and time.   
    _strtime_s( tmpbuf, 128 );  
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );  
    _strdate_s( tmpbuf, 128 );  
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );  
  
    // Get UNIX-style time and display as number and string.   
    time( &ltime );  
    printf( "Time in seconds since UTC 1/1/70:\t%lld\n", (long long)ltime );  
    err = ctime_s(timebuf, 26, &ltime);  
    if (err)  
    {  
       printf("ctime_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "UNIX time and date:\t\t\t%s", timebuf );  
  
    // Display UTC.   
    err = _gmtime64_s( &gmt, &ltime );  
    if (err)  
    {  
       printf("_gmtime64_s failed due to an invalid argument.");  
    }  
    err = asctime_s(timebuf, 26, &gmt);  
    if (err)  
    {  
       printf("asctime_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "Coordinated universal time:\t\t%s", timebuf );  
  
    // Convert to time structure and adjust for PM if necessary.   
    err = _localtime64_s( &today, &ltime );  
    if (err)  
    {  
       printf("_localtime64_s failed due to an invalid argument.");  
       exit(1);  
    }  
    if( today.tm_hour >= 12 )  
    {  
   strcpy_s( ampm, sizeof(ampm), "PM" );  
   today.tm_hour -= 12;  
    }  
    if( today.tm_hour == 0 )  // Adjust if midnight hour.  
   today.tm_hour = 12;  
  
    // Convert today into an ASCII string   
    err = asctime_s(timebuf, 26, &today);  
    if (err)  
    {  
       printf("asctime_s failed due to an invalid argument.");  
       exit(1);  
    }  
  
    // Note how pointer addition is used to skip the first 11   
    // characters and printf is used to trim off terminating   
    // characters.  
    //  
    printf( "12-hour time:\t\t\t\t%.8s %s\n",  
       timebuf + 11, ampm );  
  
    // Print additional time information.   
    _ftime( &tstruct ); // C4996  
    // Note: _ftime is deprecated; consider using _ftime_s instead  
    printf( "Plus milliseconds:\t\t\t%u\n", tstruct.millitm );  
    printf( "Zone difference in hours from UTC:\t%u\n",   
             tstruct.timezone/60 );  
    printf( "Time zone name:\t\t\t\t%s\n", _tzname[0] ); //C4996  
    // Note: _tzname is deprecated; consider using _get_tzname  
    printf( "Daylight savings:\t\t\t%s\n",   
             tstruct.dstflag ? "YES" : "NO" );  
  
    // Make time for noon on Christmas, 1993.   
    if( mktime( &xmas ) != (time_t)-1 )  
    {  
       err = asctime_s(timebuf, 26, &xmas);  
       if (err)  
       {  
          printf("asctime_s failed due to an invalid argument.");  
          exit(1);  
       }  
       printf( "Christmas\t\t\t\t%s\n", timebuf );  
    }  
  
    // Use time structure to build a customized time string.   
    err = _localtime64_s( &today, &ltime );  
    if (err)  
    {  
        printf(" _localtime64_s failed due to invalid arguments.");  
        exit(1);  
    }  
  
    // Use strftime to build a customized time string.   
    strftime( tmpbuf, 128,  
         "Today is %A, day %d of %B in the year %Y.\n", &today );  
    printf( tmpbuf );  
}  
```  
  
```Output  
操作系统时间：            13:51:23 操作系统日期：            04/25/03 自 UTC 1/1/70 以来的时间（以秒为单位）：   1051303883 UNIX 时间和日期：         2003 年 4 月 25 日周五 13:51:23 协调世界时：      2003 年 4 月 25 日周五 20:51:23 12 小时制时间：            01:51:23 PM 加毫秒：         552 与 UTC 的时差（以小时为单位）：   8 时区名称：            太平洋标准夏令时：         是的圣诞节            1993 年 12 月 25 日周六 12:00:00 今天是 2003 年 4 月 25 日周五。  
```  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [\_utime、\_utime32、\_utime64、\_wutime、\_wutime32、\_wutime64](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)