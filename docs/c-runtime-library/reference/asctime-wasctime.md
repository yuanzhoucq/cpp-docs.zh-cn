---
title: "asctime、_wasctime | Microsoft Docs"
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
  - "_wasctime"
  - "asctime"
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
  - "_tasctime"
  - "asctime"
  - "_wasctime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tasctime 函数"
  - "_wasctime 函数"
  - "asctime 函数"
  - "tasctime 函数"
  - "时间结构转换"
  - "时间, 转换"
  - "wasctime 函数"
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# asctime、_wasctime
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

变换一个 `tm` 时间结构为字符串。  提供这些函数的更多安全版本；请参见 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
## 语法  
  
```  
char *asctime(   
   const struct tm *timeptr   
);  
wchar_t *_wasctime(   
   const struct tm *timeptr   
);  
```  
  
#### 参数  
 `timeptr`  
 Time\/date 结构  
  
## 返回值  
 `asctime` 返回指向字符串的指针； `_wasctime` 返回指向宽字符字符串的指针。  无错误值返回。  
  
## 备注  
 提供这些函数的更多安全版本；请参见[asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)。  
  
 `asctime` 函数转换为结构存储的时间为字符串。  `timeptr` 值总是包含调用 `gmtime` 或 `localtime`，都返回指向 `tm` 结构的指针，定义在 TIME.H。  
  
|timeptr 成员|值|  
|----------------|-------|  
|`tm_hour`|午夜后的小时 \(0 – 23\)。|  
|`tm_isdst`|如果夏时制有效，是正值；如果夏时制无效，是0；负值，如果夏时制状态未知，是负值。  C 运行库假设使用美国规则实现夏令时 \(DST\) 的计算。|  
|`tm_mday`|一月中的一天\(1–31\)|  
|`tm_min`|一小时中的分钟 \(0–59\)|  
|`tm_mon`|月份 \(0–11;一月 \= 0\)|  
|`tm_sec`|一分钟的秒数 \(0–59\)|  
|`tm_wday`|一周中的一天 \(0–6;周日 \= 0\)|  
|`tm_yday`|一年中的一天\(0–365; 1 月 1 日 \= 0 \)|  
|`tm_year`|年份 \(当前年份减 1900\)|  
  
 转换的字符串本地根据的时区设置也会调整。  有关设置本地时间，请参见 [time](../../c-runtime-library/reference/time-time32-time64.md)[\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)，[localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)，并且[\_tzset](../../c-runtime-library/reference/tzset.md) 有关配置本地时间的函数，以及有关环境定义时区和全局变量信息的函数。  
  
 `asctime` 生成的结果字符串正确包含 26 个字符并具有 `Wed Jan 02 02:03:55 1980\n\0`格式。  使用 24 小时制。  所有字段都具有一个常数的宽度。  换行符和空字符占用字符串中的后两个位置。  `asctime` 使用单例，静态分配的缓冲区容纳返回字符串。  每次对此函数的调用销毁以前调用的结果。  
  
 `_wasctime` 是 `asctime`的宽字符版本。  `_wasctime` 和 `asctime` 行为相同，否则。  
  
 这些函数验证其参数。  如果 `timeptr` 为 null 指针，或者如果它包含超出范围的值，则调用无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则该函数返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
### 通用文本程序映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE &和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tasctime`|`asctime`|`asctime`|`_wasctime`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`asctime`|\<time.h\>|  
|`_wasctime`|\<time.h\> or \<wchar.h\>|  
  
## 示例  
 使用 `asctime` 函数，此程序把系统时间存储在长整数 `aclock` 中，将其转换为结构 `newtime` 转换为字符串形式，然后输出。  
  
```  
// crt_asctime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
    struct tm   *newTime;  
    time_t      szClock;  
  
    // Get time in seconds  
    time( &szClock );  
  
    // Convert time to struct tm form   
    newTime = localtime( &szClock );  
  
    // Print local time as a string.  
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996  
    // Note: asctime is deprecated; consider using asctime_s instead  
}  
```  
  
  **当前日期和时间：白天 2 月 03 日 11:38: 58 年 2002**   
## .NET Framework 等效项  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)