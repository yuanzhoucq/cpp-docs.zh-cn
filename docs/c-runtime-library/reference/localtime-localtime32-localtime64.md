---
title: "localtime、_localtime32、_localtime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_localtime64"
  - "_localtime32"
  - "localtime"
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
  - "localtime64"
  - "_localtime64"
  - "localtime32"
  - "localtime"
  - "_localtime32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "localtime32 函数"
  - "_localtime32 函数"
  - "_localtime64 函数"
  - "localtime64 函数"
  - "localtime 函数"
  - "时间, 转换值"
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# localtime、_localtime32、_localtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

转换时间值并更正本地时区。 这些函数的更安全版本才会有效。请参阅 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)。  
  
## 语法  
  
```  
struct tm *localtime(  
   const time_t *timer   
);  
struct tm *_localtime32(  
   const __time32_t *timer  
);  
struct tm *_localtime64(  
   const __time64_t *timer   
);  
```  
  
#### 参数  
 `timer`  
 指针，指向存储的时间。  
  
## 返回值  
 将一个指针返回到结构结果中，或 `NULL` 如果日期传递给函数︰  
  
-   之前午夜，自 1970 年 1 月 1 日。  
  
-   03:14:07 之后，2038 年 1 月 19 日，UTC \(使用 `_time32` 和 `time32_t`\)。  
  
-   23:59:59，3000 年 12 月 31 日，UTC 后 \(使用 `_time64` 和 `__time64_t`\)。  
  
 `_localtime64`, 它使用 `__time64_t` 结构，请允许向上通过 23:59:59，3000 年 12 月 31 日，格式为协调世界时 \(UTC\) 表示的日期值，而 `_localtime32` 表示 23:59:59 2038 年 1 月 18 日，UTC 日期。  
  
 `localtime` 是一个内联函数，其计算结果为 `_localtime64`, ，和 `time_t` 等同于 `__time64_t`。 如果您需要强制编译器将解释 `time_t`为旧的 32 位 `time_t`, ，您可以定义 `_USE_32BIT_TIME_T`。 这样做，这将导致 `localtime` 评估结果才为 `_localtime32`。 这不是建议的因为您的应用程序可能会失败后 2038 年 1 月 18 日，并且不允许在 64 位平台上。  
  
 结构类型的字段 [tm](../../c-runtime-library/standard-types.md) 存储下面的值，其中每个 `int`:  
  
 `tm_sec`  
 分钟后的几秒 \(0\-59\)。  
  
 `tm_min`  
 小时后的分钟 \(0\-59\)。  
  
 `tm_hour`  
 午夜后经过的小时 \(0\-23\)。  
  
 `tm_mday`  
 月 \(1\-31\) 天。  
  
 `tm_mon`  
 月 \(0 – 11;年 1 月 \= 0）。  
  
 `tm_year`  
 年份 （当前年份减去 1900年）。  
  
 `tm_wday`  
 星期几 \(0 – 6;星期日 \= 0）。  
  
 `tm_yday`  
 每年的一天 \(0\-365;1 月 1 日 \= 0\)。  
  
 `tm_isdst`  
 如果夏令时有效，则为，正值夏时制不起作用; 如果为 0如果夏时制的状态是未知的负值。 如果 `TZ` 设置环境变量，C 运行库会假定规则适用于美国境内用于实现夏令时 \(DST\) 计算。  
  
## 备注  
 `localtime` 函数将存储为时间转换为 [time\_t](../../c-runtime-library/standard-types.md) 值并将结果存储在类型的结构 `tm`。`long` 值 `timer` 自午夜以来经过的秒数表示 \(00: 00:00\)、 1970 年 1 月 1 日，UTC。 此值通常从获取 `time` 函数。  
  
 32 位和 64 位版本 `gmtime`, ，`mktime`, ，`mkgmtime`, ，和 `localtime` 所有使用单个 `tm` 每个线程进行转换的结构。 这些例程的一个每次调用将销毁上一个调用的结果。  
  
 `localtime` 如果用户首次设置全局环境变量将为本地时区更正 `TZ`。 当 `TZ` 设置时，其他三个环境变量 \(`_timezone`, ，`_daylight`, ，和 `_tzname`\) 以及自动设置。 如果 `TZ` 变量未设置， `localtime` 尝试使用控制面板中的日期\/时间应用程序中指定的时区信息。 如果无法获得此信息，PST8PDT，这表明太平洋时区，则默认情况下使用。 请参阅 [\_tzset](../../c-runtime-library/reference/tzset.md) 有关这些变量的说明。`TZ` 是 Microsoft 扩展并不是 ANSI 标准定义的一部分 `localtime`。  
  
> [!NOTE]
>  目标环境应尝试确定夏时制是否有效。  
  
 这些函数验证其参数。 如果 `timer` 是 null 指针，或如果计时器值为负，这些函数将调用无效参数处理程序中，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数返回 `NULL` 并设置 `errno` 到 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`localtime`|\<time.h\>|  
|`_localtime32`|\<time.h\>|  
|`_localtime64`|\<time.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_localtime.cpp  
// compile with: /W3  
/* This program uses _time64 to get the current time   
 * and then uses localtime64() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm *newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
  
        _time64( &long_time );           // Get time as 64-bit integer.  
                                         // Convert to local time.  
        newtime = _localtime64( &long_time ); // C4996  
        // Note: _localtime64 deprecated; consider _localetime64_s  
  
        if( newtime->tm_hour > 12 )        // Set up extension.  
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime->tm_hour > 12 )        // Convert from 24-hour  
                newtime->tm_hour -= 12;    //   to 12-hour clock.  
        if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime->tm_hour = 12;  
  
        char buff[30];  
        asctime_s( buff, sizeof(buff), newtime );  
        printf( "%.19s %s\n", buff, am_pm );  
}  
```  
  
```Output  
星期二年 2 月 12 10:05:58 AM  
```  
  
## .NET Framework 等效项  
 [System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)