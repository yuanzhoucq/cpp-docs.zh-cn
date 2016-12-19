---
title: "strcat、wcscat、_mbscat | Microsoft Docs"
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
  - "_mbscat"
  - "wcscat"
  - "strcat"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbscat"
  - "_ftcscat"
  - "_tcscat"
  - "strcat"
  - "wcscat"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcscat 函数"
  - "_mbscat 函数"
  - "_tcscat 函数"
  - "追加字符串"
  - "串联字符串"
  - "ftcscat 函数"
  - "mbscat 函数"
  - "strcat 函数"
  - "字符串 [C++], 追加"
  - "字符串 [C++], 串联"
  - "tcscat 函数"
  - "wcscat 函数"
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcat、wcscat、_mbscat
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

追加一个字符串。  有关这些函数的更多安全版本，请参见 [strcat\_s、wcscat\_s、\_mbscat\_s](../../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)。  
  
> [!IMPORTANT]
>  `_mbscat_s` 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *strcat(  
   char *strDestination,  
   const char *strSource   
);  
wchar_t *wcscat(  
   wchar_t *strDestination,  
   const wchar_t *strSource   
);  
unsigned char *_mbscat(  
   unsigned char *strDestination,  
   const unsigned char *strSource   
);  
template <size_t size>  
char *strcat(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
wchar_t *wcscat(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
unsigned char *_mbscat(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### 参数  
 `strDestination`  
 以NULL中止的目的字符串。  
  
 `strSource`  
 null 终止的源字符串。  
  
## 返回值  
 这些函数都返回一个目标字符串 \(`strDestination`\)。  没有保留任何返回值以指示错误。  
  
## 备注  
 `strcat` 功能追加 `strSource` 到 `strDestination` 并停止使用 null 字符的结果字符串。  `strSource` 的初始字符覆盖 `strDestination`终止 null 字符。  如果源和目标字符串重叠，则 `strcat` 的行为未定义。  
  
> [!IMPORTANT]
>  由于 `strcat` 在追加 `strSource` 之前不会检查是否在 `strDestination` 有足够空间，这是一个可能导致缓冲区溢出的原因。         考虑改用 [strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) 代替。  
  
 `wcscat` 和 `_mbscat` 是宽字符，属于 `strcat`的多节字字符版本。  参数和 `wcscat` 的返回值是宽字符字符串；`_mbscat` 的参数和返回值为多字节字符字符串。  否则这三个函数否则具有相同行为。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscat`|`strcat`|`_mbscat`|`wcscat`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strcat`|\<string.h\>|  
|`wcscat`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscat`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见[strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)示例。  
  
## .NET Framework 等效项  
 [System::String::Concat](https://msdn.microsoft.com/en-us/library/system.string.concat.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)