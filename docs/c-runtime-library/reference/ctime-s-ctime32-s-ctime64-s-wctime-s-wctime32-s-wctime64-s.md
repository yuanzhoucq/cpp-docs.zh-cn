---
title: "ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s | Microsoft Docs"
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
  - "_ctime64_s"
  - "_wctime32_s"
  - "ctime_s"
  - "_wctime64_s"
  - "_ctime32_s"
  - "_wctime_s"
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
  - "ctime64_s"
  - "_ctime32_s"
  - "_tctime32_s"
  - "_ctime64_s"
  - "_wctime_s"
  - "_tctime_s"
  - "_tctime64_s"
  - "ctime_s"
  - "ctime32_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wctime32_s 函数"
  - "ctime64_s 函数"
  - "_tctime64_s 函数"
  - "_wctime_s 函数"
  - "tctime_s 函数"
  - "_wctime64_s 函数"
  - "ctime_s 函数"
  - "ctime32_s 函数"
  - "_ctime64_s 函数"
  - "tctime64_s 函数"
  - "wctime64_s 函数"
  - "wctime_s 函数"
  - "_tctime_s 函数"
  - "tctime32_s 函数"
  - "wctime32_s 函数"
  - "时间, 转换"
  - "_ctime32_s 函数"
  - "_tctime32_s 函数"
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将时间值转换为字符串并调整本地时间区域设置。 一些版本 [ctime、 \_ctime64、 \_wctime、 \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) 因安全性增强中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
errno_t ctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _ctime32_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _ctime64_s(   
   char* buffer,  
   size_t numberOfElements,  
   const __time64_t *time )  
;  
errno_t _wctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const time_t *time   
);  
errno_t _wctime32_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time32_t *time   
);  
errno_t _wctime64_s(   
   wchar_t* buffer,  
   size_t numberOfElements,  
   const __time64_t *time   
);  
template <size_t size>  
errno_t _ctime32_s(   
   char (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _ctime64_s(   
   char (&buffer)[size],  
   const __time64_t *time  
); // C++ only  
template <size_t size>  
errno_t _wctime32_s(   
   wchar_t (&buffer)[size],  
   const __time32_t *time   
); // C++ only  
template <size_t size>  
errno_t _wctime64_s(   
   wchar_t (&buffer)[size],  
   const __time64_t *time   
); // C++ only  
```  
  
#### 参数  
 \[\] out `buffer`  
 必须足以容纳 26 个字符。 指向字符字符串结果时，指针或 `NULL`如果︰  
  
-   `time` 表示自 1970 年 1 月 1 日午夜 UTC 之前的日期。  
  
-   如果您使用 `_ctime32_s` 或 `_wctime32_s` 和 `time` 表示 23:59:59 2038 年 1 月 18 日，UTC 之后的日期。  
  
-   如果您使用 `_ctime64_s` 或 `_wctime64_s` 和 `time` 表示 23:59:59，3000 年 12 月 31 日，UTC 之后的日期。  
  
-   如果您使用 `_ctime_s` 或 `_wctime_s`, ，这些函数是对前面的函数的包装器。 请参见“备注”部分。  
  
 \[in\] `numberOfElements`  
 缓冲区的大小。  
  
 \[\] t in`ime`  
 指针，指向存储的时间。  
  
## 返回值  
 如果成功，则为零。 如果没有失败的原因是一个无效参数，将调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则返回错误代码。 ERRNO 中定义了错误代码。H;有关这些错误的列表，请参阅 [errno](../../c-runtime-library/errno-constants.md)。 下表中显示为每个错误条件而引发的实际错误代码。  
  
## 错误条件  
  
|`buffer`|`numberOfElements`|`time`|返回|中的值 `buffer`|  
|--------------|------------------------|------------|--------|------------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|不 `NULL` （指向有效内存）|0|any|`EINVAL`|未修改|  
|不 `NULL`|0 \< 大小 \< 26|any|`EINVAL`|空字符串|  
|不 `NULL`|\>\= 26|NULL|`EINVAL`|空字符串|  
|不 `NULL`|\>\= 26|\< 0|`EINVAL`|空字符串|  
  
## 备注  
 `ctime_s` 函数将转换为存储的时间值 [time\_t](../../c-runtime-library/standard-types.md) 转换为字符串的结构。`time` 值通常通过调用中获取 [时间](../../c-runtime-library/reference/time-time32-time64.md), ，它将返回自午夜以来经过的秒数 \(00: 00:00\)、 1970 年 1 月 1 日，格式为协调世界时 \(UTC\)。 返回值字符串包含完全 26 个字符，其形式︰  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 使用 24 小时制。 所有字段都具有固定宽度。 换行符 \('\\n'\) 和 null 字符 \(\\0'\) 占据的最后两个字符串。  
  
 此外可根据当地时间区域设置调整已转换的字符字符串。 请参阅 `time`, ，[\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), ，和 [localtime32\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) 函数以获取有关配置本地时间的信息和 [\_tzset](../../c-runtime-library/reference/tzset.md) 函数定义的时区环境和全局变量的信息。  
  
 `_wctime32_s` 和 `_wctime64_s` 的宽字符版本均 `_ctime32_s` 和 `_ctime64_s`; 返回一个指向宽字符字符串。 否则为 `_ctime64_s`, ，`_wctime32_s`, ，和 `_wctime64_s` 行为 `_ctime32_s`。  
  
 `ctime_s` 是一个内联函数，计算结果为 `_ctime64_s` 和 `time_t` 等同于 `__time64_t`。 如果需要强制编译器将 `time_t` 解释为旧的 32 位 `time_t`，你可以定义 `_USE_32BIT_TIME_T`。 这样做，这将导致 `ctime_s` 评估结果才为 `_ctime32_s`。 这不是建议的因为您的应用程序可能会失败后 2038 年 1 月 18 日，并且不允许在 64 位平台上。  
  
 C \+ \+ 中使用这些函数是由模板重载简化;重载可以自动推导出缓冲区长度，不再需要指定大小参数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tctime_s`|`ctime_s`|`ctime_s`|`_wctime_s`|  
|`_tctime32_s`|`_ctime32_s`|`_ctime32_s`|`_wctime32_s`|  
|`_tctime64_s`|`_ctime64_s`|`_ctime64_s`|`_wctime64_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`ctime_s,`<br /><br /> `_ctime32_s,`<br /><br /> `_ctime64_s`|\<time.h\>|  
|`_wctime_s,`<br /><br /> `_wctime32_s,`<br /><br /> `_wctime64_s`|\<.h \> 或 \< wchar.h \>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_wctime_s.c  
/* This program gets the current  
 * time in time_t form and then uses _wctime_s to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
#define SIZE 26  
  
int main( void )  
{  
   time_t ltime;  
   wchar_t buf[SIZE];  
   errno_t err;  
  
   time( &ltime );  
  
   err = _wctime_s( buf, SIZE, &ltime );  
   if (err != 0)  
   {  
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);  
   }  
   wprintf_s( L"The time is %s\n", buf );  
}  
```  
  
## 示例输出  
  
```  
The time is Fri Apr 25 13:03:39 2003  
```  
  
## .NET Framework 等效项  
  
-   [System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)