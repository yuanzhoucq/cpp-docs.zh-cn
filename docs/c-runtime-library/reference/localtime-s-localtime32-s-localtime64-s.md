---
title: "localtime_s, _localtime32_s, _localtime64_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_localtime64_s"
  - "_localtime32_s"
  - "localtime_s"
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
  - "_localtime32_s"
  - "localtime32_s"
  - "localtime_s"
  - "localtime64_s"
  - "_localtime64_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_localtime64_s 函数"
  - "localtime32_s 函数"
  - "_localtime32_s 函数"
  - "localtime64_s 函数"
  - "时间, 转换值"
  - "localtime_s 函数"
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# localtime_s, _localtime32_s, _localtime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将时间值转换和更正为本地时区。 一些版本 [localtime、 \_localtime32、 \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 因安全性增强中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### 参数  
 `_tm`  
 指向要填充的时间结构的指针。  
  
 `time`  
 指针，指向存储的时间。  
  
## 返回值  
 如果成功，则为零。 如果失败，返回值将是错误代码。 错误代码是在 Errno.h 中定义的。 有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
### 错误条件  
  
|`_tm`|`time`|返回值|中的值 `_tm`|调用无效参数处理程序|  
|-----------|------------|---------|---------------|----------------|  
|`NULL`|any|`EINVAL`|未修改|是|  
|不 `NULL` （指向有效内存）|`NULL`|`EINVAL`|所有字段都设置为\-1|是|  
|不 `NULL` （指向有效内存）|小于 0 或大于 `_MAX__TIME64_T`|`EINVAL`|所有字段都设置为\-1|否|  
  
 对于第一个的两个错误条件，无效参数处理程序将调用，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
## 备注  
 `_localtime32_s` 函数将存储为时间转换为 [time\_t](../../c-runtime-library/standard-types.md) 值并将结果存储在类型的结构 `tm`。`long` 值 `timer` 自午夜以来经过的秒数表示 \(00: 00:00\)、 1970 年 1 月 1 日，UTC。 此值通常从获取 `time` 函数。  
  
 `_localtime32_s` 如果用户首次设置全局环境变量将为本地时区更正 `TZ`。 当 `TZ` 设置时，其他三个环境变量 \(`_timezone`, ，`_daylight`, ，和 `_tzname`\) 以及自动设置。 如果 `TZ` 变量未设置， `localtime32_s` 尝试使用控制面板中的日期\/时间应用程序中指定的时区信息。 如果无法获得此信息，PST8PDT，这表明太平洋时区，则默认情况下使用。 请参阅 [\_tzset](../../c-runtime-library/reference/tzset.md) 有关这些变量的说明。`TZ` 是 Microsoft 扩展并不是 ANSI 标准定义的一部分 `localtime`。  
  
> [!NOTE]
>  目标环境应尝试确定夏时制是否有效。  
  
 `_localtime64_s`, 它使用 `__time64_t` 结构，请允许向上通过 23:59:59，3000 年 12 月 31 日，格式为协调世界时 \(UTC\) 表示的日期值，而 `_localtime32_s` 表示 23:59:59 2038 年 1 月 18 日，UTC 日期。  
  
 `localtime_s` 是一个内联函数，其计算结果为 `_localtime64_s`, ，和 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 这样做，这将导致 `localtime_s` 评估结果才为 `_localtime32_s`。 这不是建议的因为您的应用程序可能会失败后 2038 年 1 月 18 日，并且不允许在 64 位平台上。  
  
 结构类型的字段 [tm](../../c-runtime-library/standard-types.md) 存储下面的值，其中每个 `int`。  
  
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
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`localtime_s`|\<time.h\>|  
|`_localtime32_s`|\<time.h\>|  
|`_localtime64_s`|\<time.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## 示例输出  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## .NET Framework 等效项  
 [System::DateTime::ToLocalTime](https://msdn.microsoft.com/en-us/library/system.datetime.tolocaltime.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)