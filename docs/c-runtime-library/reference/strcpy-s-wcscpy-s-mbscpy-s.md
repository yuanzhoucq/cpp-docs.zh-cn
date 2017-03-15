---
title: "strcpy_s、wcscpy_s、_mbscpy_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcscpy_s"
  - "_mbscpy_s"
  - "strcpy_s"
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
  - "strcpy_s"
  - "_mbscpy_s"
  - "_tcscpy_s"
  - "wcscpy_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strcpy_s 函数"
  - "_tcscpy_s 函数"
  - "_mbscpy_s 函数"
  - "复制字符串"
  - "复制字符串 [c + +]"
  - "tcscpy_s 函数"
  - "wcscpy_s 函数"
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
caps.latest.revision: 41
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 41
---
# strcpy_s、wcscpy_s、_mbscpy_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

复制字符串。 这些版本的 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) 具有安全增强功能，如中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
> [!IMPORTANT]
>  `_mbscpy_s` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [\/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
errno_t strcpy_s(  
   char *strDestination,  
   size_t numberOfElements,  
   const char *strSource   
);  
errno_t wcscpy_s(  
   wchar_t *strDestination,  
   size_t numberOfElements,  
   const wchar_t *strSource   
);  
errno_t _mbscpy_s(  
   unsigned char *strDestination,  
   size_t numberOfElements,  
   const unsigned char *strSource   
);  
template <size_t size>  
errno_t strcpy_s(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
errno_t wcscpy_s(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
errno_t _mbscpy_s(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### 参数  
 `strDestination`  
 目标字符串缓冲区的位置。  
  
 `numberOfElements`  
 多字节窄函数 `char` 单元以及宽函数 `wchar_t` 单元中的目标字符串缓冲区的大小。  
  
 `strSource`  
 以 null 结尾的源字符串缓冲区。  
  
## 返回值  
 如果成功，则为零；否则返回错误。  
  
### 错误条件  
  
|`strDestination`|`numberOfElements`|`strSource`|返回值|`strDestination` 的内容|  
|----------------------|------------------------|-----------------|---------|--------------------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|`strDestination`\[0\] 设置为 0|  
|任何|0 或过小|any|`ERANGE`|`strDestination`\[0\] 设置为 0|  
  
## 备注  
 `strcpy_s` 函数将 `strSource` 地址中的内容（包括结尾的 null 字符）复制到 `strDestination` 指定的位置。 目标字符串必须足够大以保存源字符串及其结尾的 null 字符。 如果源和目标字符串重叠，则 `strcpy_s` 的行为是未定义的。  
  
 `wcscpy_s` 是宽字符版本的 `strcpy_s`；`_mbscpy_s` 是多字节字符版本。`wcscpy_s` 的参数和返回值是宽字符字符串；而 `_mbscpy_s` 的则是多字节字符字符串。 否则这三个函数否则具有相同行为。  
  
 如果 `strDestination` 或 `strSource` 是 null 指针，或如果目标字符串为太小，则调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，则在 `strDestination` 或 `strSource` 是 null 指针时，这些函数将返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`；如果目标字符串过小，则它们将返回 `ERANGE` 并将 `errno` 设置为 `ERANGE`。  
  
 成功执行时，目标字符串始终以 null 结尾。  
  
 在 C\+\+ 中，模板重载简化了这些函数的使用；重载可以自动推断缓冲区长度，从而无需指定大小自变量；并且它们可以自动将较旧、不安全的函数替换为更新、更安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
 这些函数的调试版本首先用 0xFE 填充缓冲区。 若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscpy_s`|`strcpy_s`|`_mbscpy_s`|`wcscpy_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strcpy_s`|\<string.h\>|  
|`wcscpy_s`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscpy_s`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strcpy_s.cpp  
// This program uses strcpy_s and strcat_s  
// to build a phrase.  
//  
  
#include <string.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   char string[80];  
   // using template versions of strcpy_s and strcat_s:  
   strcpy_s( string, "Hello world from " );  
   strcat_s( string, "strcpy_s " );  
   strcat_s( string, "and " );  
   // of course we can supply the size explicitly if we want to:  
   strcat_s( string, _countof(string), "strcat_s!" );  
  
   printf( "String = %s\n", string );  
}  
```  
  
```Output  
字符串 = Hello world from strcpy_s and strcat_s!  
```  
  
## .NET Framework 等效项  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)