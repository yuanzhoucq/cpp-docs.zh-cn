---
title: "gmtime、_gmtime32、_gmtime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gmtime32"
  - "gmtime"
  - "_gmtime64"
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
  - "gmtime"
  - "_gmtime32"
  - "_gmtime64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_gmtime32 函数"
  - "_gmtime64 函数"
  - "gmtime 函数"
  - "gmtime32 函数"
  - "gmtime64 函数"
  - "时间函数"
  - "时间结构转换"
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# gmtime、_gmtime32、_gmtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将时间值转换为一种结构。 这些函数的更安全版本才会有效。请参阅 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)。  
  
## 语法  
  
```  
struct tm *gmtime(   
   const time_t *timer   
);  
struct tm *_gmtime32(   
   const __time32_t *timer   
);  
struct tm *_gmtime64(   
   const __time64_t *timer   
);  
```  
  
#### 参数  
 `timer`  
 指针，指向存储的时间。 因为自午夜以来经过的秒为单位表示的时间 \(00: 00:00\)、 1970 年 1 月 1 日，格式为协调世界时 \(UTC\)。  
  
## 返回值  
 指向类型的结构的指针 [tm](../../c-runtime-library/standard-types.md)。 返回的结构字段存储的计算结果的值 `timer` 参数以 utc 为单位，而不是以本地时间。 每个结构字段的类型是 `int`, 、，如下所示︰  
  
 `tm_sec`  
 分钟后的几秒 \(0\-59\)。  
  
 `tm_min`  
 小时后的分钟 \(0\-59\)。  
  
 `tm_hour`  
 午夜算起的小时 \(0\-23\)。  
  
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
 始终为 0 的 `gmtime`。  
  
 32 位和 64 位版本 `gmtime`, ，`mktime`, ，`mkgmtime`, ，和 `localtime` 都使用一个常用 `tm` 每个线程进行转换的结构。 这些函数之一的每次调用将销毁任何以前的调用的结果。 如果 `timer` 表示午夜，1970 年 1 月 1 日之前的日期 `gmtime` 返回 `NULL`。 无错误返回。  
  
 `_gmtime64`, 它使用 `__time64_t` 结构，而启用日期，以通过 23:59:59，3000 年 12 月 31 日，UTC，表示向上 `_gmtime32` 仅表示 23:59:59 2038 年 1 月 18 日，UTC 日期。 午夜 1970 年 1 月 1 日是这两个函数的日期范围的下限。  
  
 `gmtime` 是一个内联函数，计算结果为 `_gmtime64`, ，和 `time_t` 等同于 `__time64_t` 除非 `_USE_32BIT_TIME_T` 定义。 如果您必须强制编译器将解释 `time_t` 为旧的 32 位 `time_t`, ，您可以定义 `_USE_32BIT_TIME_T`, ，但执行操作将导致 `gmtime` 要内联到 `_gmtime32` 和 `time_t` 定义为 `__time32_t`。 我们建议，不做这一点，因为它不允许在 64 位平台上，并且在任何情况下您的应用程序可能会失败后 2038 年 1 月 18 日。  
  
 这些函数验证其参数。 如果 `timer` 是 null 指针，或如果计时器值为负，这些函数将调用无效参数处理程序中，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数返回 `NULL` 并设置 `errno` 到 `EINVAL`。  
  
## 备注  
 `_gmtime32` 函数将分解 `timer` 值并将其存储在类型的静态分配结构 `tm`, 在时间中定义。H。 值 `timer` 通常通过调用获取 `time` 函数。  
  
> [!NOTE]
>  在大多数情况下，目标环境来确定夏时制时间是否有效。 C 运行时该库将假设使用用于实现计算的夏令时 \(DST\) 的美国规则。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`gmtime`|\<time.h\>|  
|`_gmtime32`|\<time.h\>|  
|`_gmtime64`|\<time.h\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
  
      // crt_gmtime.c  
// compile with: /W3  
// This program uses _gmtime64 to convert a long-  
// integer representation of coordinated universal time  
// to a structure named newtime, then uses asctime to  
// convert this structure to an output string.  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm *newtime;  
   __int64 ltime;  
   char buff[80];  
  
   _time64( &ltime );  
  
   // Obtain coordinated universal time:  
   newtime = _gmtime64( &ltime ); // C4996  
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s  
   asctime_s( buff, sizeof(buff), newtime );  
   printf( "Coordinated universal time is %s\n", buff );  
}  
```  
  
```Output  
格式为协调通用时间为 2 月 12 日，星期二 23:11:31 2002年  
```  
  
## .NET Framework 等效项  
  
-   [System::DateTime::UtcNow](https://msdn.microsoft.com/en-us/library/system.datetime.utcnow.aspx)  
  
-   [System::DateTime::ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetime.touniversaltime.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [\_mkgmtime、\_mkgmtime32、\_mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)