---
title: "_strdate, _wstrdate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdate"
  - "_wstrdate"
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
  - "_tstrdate"
  - "wstrdate"
  - "_wstrdate"
  - "_strdate"
  - "strdate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strdate 函数"
  - "日期, 复制"
  - "tstrdate 函数"
  - "_wstrdate 函数"
  - "wstrdate 函数"
  - "_strdate 函数"
  - "_tstrdate 函数"
  - "复制日期"
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _strdate, _wstrdate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

复制当前系统日期到缓冲区。  提供这些函数的更多安全版本；请参见 [\_strdate\_s、\_wstrdate\_s](../../c-runtime-library/reference/strdate-s-wstrdate-s.md)。  
  
## 语法  
  
```  
char *_strdate(  
   char *datestr   
);  
wchar_t *_wstrdate(  
   wchar_t *datestr   
);  
template <size_t size>  
char *_strdate(  
   char (&datestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrdate(  
   wchar_t (&datestr)[size]  
); // C++ only  
```  
  
#### 参数  
 `datestr`  
 对包含格式化的日期字符串的缓冲区的指针。  
  
## 返回值  
 这些函数均返回指向结果字符串`datestr`的指针。  
  
## 备注  
 提供这些函数的更多安全版本；请参见 [\_strdate\_s, \_wstrdate\_s](../../c-runtime-library/reference/strdate-s-wstrdate-s.md)。  建议在可能的情况下使用更安全的函数。  
  
 `_strdate` 函数复制当前系统日期到缓冲区由 `datestr`指向，格式的 `mm`\/`dd`\/`yy`，其中 `mm` 是将月份表示的两个数字中，`dd` 是表示一日的，两位数字，并且 `yy` 为年的前两个数字。  例如，字符串 `12/05/99` 表示 1999 年 12 月 5 日。  缓冲区长度必须至少为 9 个字符。  
  
 如果 `datestr` 是一个 `NULL` 指针，无效参数处理程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`。  
  
 `_wsetlocale_wstrdate`  是 `_strdate`  的宽字符版本，`_wstrdate` 参数和 的返回值都是宽字符字符串。  否则这些函数具有相同行为。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS not defined|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------------|----------------|-------------------|  
|`_tstrdate`|`_strdate`|`_strdate`|`_wstrdate`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strdate`|\<time.h\>|  
|`_wstrdate`|\<time.h\> or \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// strdate.c  
// compile with: /W3  
#include <time.h>  
#include <stdio.h>  
int main()  
{  
    char tmpbuf[9];  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996  
    // Note: _strdate is deprecated; consider using _strdate_s instead  
}  
```  
  
  **OS 日期：04\/25\/03**   
## .NET Framework 等效项  
 [System::DateTime::Parse](https://msdn.microsoft.com/en-us/library/system.datetime.parse.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)