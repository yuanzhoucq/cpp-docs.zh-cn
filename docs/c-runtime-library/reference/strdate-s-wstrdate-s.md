---
title: "_strdate_s、_wstrdate_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdate_s"
  - "_wstrdate_s"
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
  - "_strdate_s"
  - "wstrdate_s"
  - "_wstrdate_s"
  - "strdate_s"
  - "_tstrdate_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "日期, 复制"
  - "tstrdate_s 函数"
  - "wstrdate_s 函数"
  - "_tstrdate_s 函数"
  - "strdate_s 函数"
  - "复制日期"
  - "_strdate_s 函数"
  - "_wstrdate_s 函数"
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _strdate_s、_wstrdate_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

复制当前系统日期到缓冲区。  版本[\_strdate, \_wstrdate](../../c-runtime-library/reference/strdate-wstrdate.md) 安全增强如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 语法  
  
```  
errno_t _strdate_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrdate_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strdate_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrdate_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### 参数  
 \[out\] `buffer`  
 将填写格式的日期字符串的缓冲区的指针。  
  
 \[in\] `numberOfElements`  
 缓冲区的大小。  
  
## 返回值  
 如果成功,是0。  如果失败，返回值是错误代码。  错误代码定义在ERRNO.H中；有关此函数发生的具体错误，请参见下表。  有关错误代码的更多信息，请参见 [errno](../../c-runtime-library/errno-constants.md)。  
  
## 错误情况  
  
|`buffer`|`numberOfElements`|返回|`buffer` 的内容|  
|--------------|------------------------|--------|------------------|  
|`NULL`|\(任意\)|`EINVAL`|未被修改|  
|非 `NULL` \(指向有效的缓冲区\)|0|`EINVAL`|未被修改|  
|非 `NULL` \(指向有效的缓冲区\)|0 \< `numberOfElements` \< 9|`EINVAL`|空字符串|  
|非 `NULL` \(指向有效的缓冲区\)|`numberOfElements` \>\= 9|0|按指定的备注格式化当前日期|  
  
## 安全问题  
 `NULL`传入缓冲区无效的非空值会导致访问冲突，如果`numberOfElements` 参数大于 9。  
  
 为`buffer` 大于缓冲区的实际大小的值会导致缓冲区溢出。  
  
## 备注  
 `_strdate` 和 `_wstrdate`函数提供更安全版本。  `_strdate_s` 函数复制当前系统日期到缓冲区由 `buffer`指向，格式的 `mm`\/`dd`\/`yy`，其中 `mm` 是将月份表示的两个数字中，`dd` 是表示一日的，两位数字，并且 `yy` 为年的前两个数字。  例如，字符串 `12/05/99` 表示 1999 年 12 月 5 日。  缓冲区长度必须至少为 9 个字符。  
  
 `_wsetlocale_wstrdate_s`  是 `_strdate_s`  的宽字符版本，`_wstrdate_s` 参数和 的返回值都是宽字符字符串。  否则这些函数具有相同行为。  
  
 如果 `buffer` 是 `NULL` 指针，或者，如果 `numberOfElements` 小于 9 字符，是无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果实现允许继续，这些函数返回 \-1 并将 `errno` 设置为 `EINVAL`，如果该缓冲区是 `NULL`，如果 `numberOfElements` 的值小于或等于 0，或者 `errno` 设置为 `ERANGE`，如果 `numberOfElements` 小于 9. 为。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 通用文本程序映射：  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS not defined|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------------|----------------|-------------------|  
|`_tstrdate_s`|`_strdate_s`|`_strdate_s`|`_wstrdate_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strdate`|\<time.h\>|  
|`_wstrdate`|\<time.h\> or \<wchar.h\>|  
|`_strdate_s`|\<time.h\>|  
  
## 示例  
 请参阅 [time](../../c-runtime-library/reference/time-time32-time64.md) 的示例。  
  
## .NET Framework 等效项  
 [System::DateTime::Parse](https://msdn.microsoft.com/en-us/library/system.datetime.parse.aspx)  
  
## 请参阅  
 [时间管理](../../c-runtime-library/time-management.md)   
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime\_s、\_ctime32\_s、\_ctime64\_s、\_wctime\_s、\_wctime32\_s、\_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime、\_mktime32、\_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)