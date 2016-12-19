---
title: "_strtime、_wstrtime | Microsoft Docs"
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
  - "_wstrtime"
  - "_strtime"
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
  - "_wstrtime"
  - "_strtime"
  - "wstrtime"
  - "strtime"
  - "_tstrtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtime 函数"
  - "_tstrtime 函数"
  - "_wstrtime 函数"
  - "将时间复制到缓冲区"
  - "strtime 函数"
  - "时间, 复制"
  - "tstrtime 函数"
  - "wstrtime 函数"
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strtime、_wstrtime
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

复制时间到缓冲区。  提供这些函数的更多安全版本；请参见 [\_strtime\_s、\_wstrtime\_s](../../c-runtime-library/reference/strtime-s-wstrtime-s.md)。  
  
## 语法  
  
```  
char *_strtime(  
   char *timestr   
);  
wchar_t *_wstrtime(  
   wchar_t *timestr   
);  
template <size_t size>  
char *_strtime(  
   char (&timestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrtime(  
   wchar_t (&timestr)[size]  
); // C++ only  
```  
  
#### 参数  
 `timestr`  
 时间字符串。  
  
## 返回值  
 返回指向结果字符串的指针 `timestr`。  
  
## 备注  
 `_strtime` 函数复制当前本地时间到由 `timestr`指向的缓冲区*。*时间格式为`hh:mm:ss`，其中`hh` 是以 24 小时形式表示的两位数字的小时数，`mm` 是表示分钟的两位数，`ss` 是表示秒的两位数。  例如，字符串 `18:23:44` 表示下午 6 点 23 分钟 44 秒钟。缓冲区长度必须至少为 9 个字符。  
  
 `_wsetlocale_wstrtime`  是 `_strtime`  的宽字符版本，`_wstrtime` 参数和 的返回值都是宽字符字符串。  这些函数为具有相同的行为。如果 `timestr` 是 `NULL` 指针或如果 `timestr`格式不正确，调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许异常继续，这些函数返回 null 并将 `errno` 设置为 `EINVAL`，如果 `timestr` 为空或 `errno` 设置为 `ERANGE`，如果 `timestr` 不正确的格式。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE &和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tstrtime`|`_strtime`|`_strtime`|`_wstrtime`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strtime`|\<time.h\>|  
|`_wstrtime`|\<time.h\> or \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strtime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char tbuffer [9];  
   _strtime( tbuffer ); // C4996  
   // Note: _strtime is deprecated; consider using _strtime_s instead  
   printf( "The current time is %s \n", tbuffer );  
}  
```  
  
  **当前时间为 14:21:44。**   
## .NET Framework 等效项  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)