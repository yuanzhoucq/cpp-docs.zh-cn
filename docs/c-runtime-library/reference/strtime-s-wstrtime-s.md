---
title: "_strtime_s、_wstrtime_s | Microsoft Docs"
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
  - "_wstrtime_s"
  - "_strtime_s"
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
  - "_wstrtime_s"
  - "strtime_s"
  - "wstrtime_s"
  - "_strtime_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtime_s 函数"
  - "_wstrtime_s 函数"
  - "将时间复制到缓冲区"
  - "strtime_s 函数"
  - "时间, 复制"
  - "wstrtime_s 函数"
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strtime_s、_wstrtime_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

复制当前时间到缓冲区。  [\_strtime, \_wstrtime](../../c-runtime-library/reference/strtime-wstrtime.md)[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 语法  
  
```  
errno_t _strtime_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrtime_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strtime_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrtime_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### 参数  
 \[out\] `buffer`  
 缓冲区的长度至少10个字节，其中写入时间。  
  
 \[in\] `numberOfElements`  
 缓冲区的大小。  
  
## 返回值  
 如果成功,是0。  
  
 如果错误情况发生，则将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果失败，返回值是错误代码。  错误代码定义在ERRNO.H中；有关此函数发生的具体错误，请参见下表。  有关错误代码的更多信息，请参见 [errno 常数](../../c-runtime-library/errno-constants.md)。  
  
### 错误情况  
  
|`buffer`|`numberOfElements`|返回|`buffer` 的内容|  
|--------------|------------------------|--------|------------------|  
|`NULL`|\(任意\)|`EINVAL`|未被修改|  
|非 `NULL` \(指向有效的缓冲区\)|0|`EINVAL`|未被修改|  
|非 `NULL` \(指向有效的缓冲区\)|0 \< size \< 9|`EINVAL`|空字符串|  
|非 `NULL` \(指向有效的缓冲区\)|Size \> 9|0|按指定的备注格式化当前时间|  
  
## 安全问题  
 如果 `numberOfElements` 参数大于 9.，传入缓冲区无效的非空值会导致访问冲突。  
  
 为`numberOfElements` 大于缓冲区的实际大小的值会导致缓冲区溢出。  
  
## 备注  
 `_strtime` 和 `_wstrtime`函数提供更安全版本。  `_strtime_s` 函数复制当前本地时间到由 `timestr`指向的缓冲区*。*时间格式为`hh:mm:ss`，其中`hh` 是以 24 小时形式表示的两位数字的小时数，`mm` 是表示分钟的两位数，`ss` 是表示秒的两位数。  例如，字符串 `18:23:44` 表示下午 6 点 23 分钟 44 秒钟。缓冲区长度必须至少为 9 字节；实际大小由第二个参数指定。  
  
 `_wsetlocale_wstrtime`  是 `_strtime`  的宽字符版本，`_wstrtime` 参数和 的返回值都是宽字符字符串。  否则这些函数具有相同行为。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 通用文本程序映射：  
  
|TCHAR.H 例程|未定义的\_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tstrtime_s`|`_strtime_s`|`_strtime_s`|`_wstrtime_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strtime_s`|\<time.h\>|  
|`_wstrtime_s`|\<time.h\> or \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// strtime_s.c  
  
#include <time.h>  
#include <stdio.h>  
  
int main()  
{  
    char tmpbuf[9];  
    errno_t err;  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    // Display operating system-style date and time.   
    err = _strtime_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
      exit(1);  
    }  
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );  
    err = _strdate_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );  
  
}  
```  
  
  **OS 时间：14:37: 49**  
**OS 日期：04\/25\/03**   
## .NET Framework 等效项  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)