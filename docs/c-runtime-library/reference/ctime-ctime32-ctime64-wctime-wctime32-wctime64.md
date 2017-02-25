---
title: "ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ctime64"
  - "_wctime32"
  - "ctime"
  - "_wctime64"
  - "_ctime32"
  - "_wctime"
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
  - "_wctime64"
  - "_ctime32"
  - "_tctime"
  - "_wctime"
  - "_wctime32"
  - "_tctime64"
  - "_ctime64"
  - "ctime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tctime64 函数"
  - "_ctime32 函数"
  - "ctime32 函数"
  - "_wctime 函数"
  - "wctime64 函数"
  - "_tctime64 函数"
  - "_tctime32 函数"
  - "_ctime64 函数"
  - "_wctime64 函数"
  - "ctime 函数"
  - "wctime32 函数"
  - "ctime64 函数"
  - "_wctime32 函数"
  - "_tctime 函数"
  - "tctime32 函数"
  - "tctime 函数"
  - "wctime 函数"
  - "时间, 转换"
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将时间值转换为字符串并调整本地时间区域设置。 这些函数的更安全版本才会有效。请参阅 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)。  
  
## 语法  
  
```  
char *ctime(   
   const time_t *timer   
);  
char *_ctime32(   
   const __time32_t *timer )  
;  
char *_ctime64(   
   const __time64_t *timer )  
;  
wchar_t *_wctime(   
   const time_t *timer   
);  
wchar_t *_wctime32(   
   const __time32_t *timer  
);  
wchar_t *_wctime64(   
   const __time64_t *timer   
);  
```  
  
#### 参数  
 `timer`  
 指针，指向存储的时间。  
  
## 返回值  
 指向字符的字符串结果的指针。`NULL` 如果将返回︰  
  
-   `time` 表示自 1970 年 1 月 1 日午夜 UTC 之前的日期。  
  
-   如果您使用 `_ctime32` 或 `_wctime32` 和 `time` 表示 23:59:59 2038 年 1 月 18 日，UTC 之后的日期。  
  
-   如果您使用 `_ctime64` 或 `_wctime64` 和 `time` 表示 23:59:59，3000 年 12 月 31 日，UTC 之后的日期。  
  
 `ctime` 是一个内联函数，其计算结果为 `_ctime64` 和 `time_t` 等同于 `__time64_t`。 如果您需要强制编译器将解释 `time_t` 为旧的 32 位 `time_t`, ，您可以定义 `_USE_32BIT_TIME_T`。 这样做，这将导致 `ctime` 评估结果才为 `_ctime32`。 这不是建议的因为您的应用程序可能会失败后 2038 年 1 月 18 日，并且不允许在 64 位平台上。  
  
## 备注  
 `ctime` 函数将转换为存储的时间值 [time\_t](../../c-runtime-library/standard-types.md) 转换为字符串的值。`timer` 值通常通过调用中获取 [时间](../../c-runtime-library/reference/time-time32-time64.md), ，它将返回自午夜以来经过的秒数 \(00: 00:00\)、 1970 年 1 月 1 日，格式为协调世界时 \(UTC\)。 返回值字符串包含完全 26 个字符，其形式︰  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 使用 24 小时制。 所有字段都具有固定宽度。 换行符 \('\\n'\) 和 null 字符 \(\\0'\) 占据的最后两个字符串。  
  
 此外可根据当地时间区域设置调整已转换的字符字符串。 请参阅 `time`, ，[\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), ，和 [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) 函数以获取有关配置本地时间的信息和 [\_tzset](../../c-runtime-library/reference/tzset.md) 有关定义的时区环境和全局变量的详细信息的函数。  
  
 调用 `ctime` 修改使用的单个静态分配的缓冲区 `gmtime` 和 `localtime` 函数。 这些例程的一个每次调用将销毁上一个调用的结果。`ctime` 共享的静态缓冲区时 `asctime` 函数。 因此，调用 `ctime` 销毁的任何以前调用结果 `asctime`, ，`localtime`, ，或 `gmtime`。  
  
 `_wctime` 和 `_wctime64` 的宽字符版本均 `ctime` 和 `_ctime64`; 返回一个指向宽字符字符串。 否则为 `_ctime64`, ，`_wctime`, ，和 `_wctime64` 行为 `ctime`。  
  
 这些函数验证其参数。 如果 `timer` 是 null 指针，或如果计时器值为负，这些函数将调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数返回 `NULL` 并设置 `errno` 到 `EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tctime`|`ctime`|`ctime`|`_wctime`|  
|`_tctime32`|`_ctime32`|`_ctime32`|`_wctime32`|  
|`_tctime64`|`_ctime64`|`_ctime64`|`_wctime64`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`ctime`|\<time.h\>|  
|`_ctime32`|\<time.h\>|  
|`_ctime64`|\<time.h\>|  
|`_wctime`|\<.h \> 或 \< wchar.h \>|  
|`_wctime32`|\<.h \> 或 \< wchar.h \>|  
|`_wctime64`|\<.h \> 或 \< wchar.h \>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_ctime64.c  
// compile with: /W3  
/* This program gets the current  
 * time in _time64_t form, then uses ctime to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   __time64_t ltime;  
  
   _time64( &ltime );  
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996  
   // Note: _ctime64 is deprecated; consider using _ctime64_s  
}  
```  
  
```Output  
该时间是星期三年 2 月 13 16:04:43 2002年  
```  
  
## .NET Framework 等效项  
  
-   [System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)