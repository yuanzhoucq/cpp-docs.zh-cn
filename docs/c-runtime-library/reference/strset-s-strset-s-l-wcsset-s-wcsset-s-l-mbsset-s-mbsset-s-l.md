---
title: "_strset_s、_strset_s_l、_wcsset_s、_wcsset_s_l、_mbsset_s、_mbsset_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsset_s"
  - "_wcsset_s_l"
  - "_strset_s"
  - "_mbsset_s_l"
  - "_strset_s_l"
  - "_mbsset_s"
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
  - "_wcsset_s_l"
  - "strset_s"
  - "_mbsset_s"
  - "mbsset_s"
  - "_strset_s"
  - "_mbsset_s_l"
  - "strset_s_l"
  - "_wcsset_s"
  - "mbsset_s_l"
  - "wcsset_s_l"
  - "wcsset_s"
  - "_strset_s_l"
  - "_tcsset_s_l"
  - "_tcsset_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsset_s 函数"
  - "_mbsset_s_l 函数"
  - "_strset_s 函数"
  - "_strset_s_l 函数"
  - "_tcsset_s 函数"
  - "_tcsset_s_l 函数"
  - "_wcsset_s 函数"
  - "_wcsset_s_l 函数"
  - "字符 [C++], 设置"
  - "mbsset_s 函数"
  - "mbsset_s_l 函数"
  - "字符串 [C++], 设置字符"
  - "strset_s 函数"
  - "strset_s_l 函数"
  - "tcsset_s 函数"
  - "tcsset_s_l 函数"
  - "wcsset_s 函数"
  - "wcsset_s_l 函数"
ms.assetid: dceb2909-6b41-4792-acb7-888e45bb8b35
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _strset_s、_strset_s_l、_wcsset_s、_wcsset_s_l、_mbsset_s、_mbsset_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串的字符设置为一个字符。  [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  `_mbsset_s` 和 `_mbsset_s_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
errno_t _strset_s(  
   char *str,  
   size_t numberOfElements,  
   int c   
);  
errno_t _strset_s_l(  
   char *str,  
   size_t numberOfElements,  
   int c,  
   locale_t locale  
);  
errno_t _wcsset_s(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c   
);  
errno_t *_wcsset_s_l(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c,  
   locale_t locale  
);  
errno_t _mbsset_s(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c   
);  
errno_t _mbsset_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 设置 null 终止的字符串。  
  
 `numberOfElements`  
 `str`缓冲区的大小。  
  
 `c`  
 字符设置。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；否则为错误代码。  
  
 这些函数验证其参数。  如果 `str` 是空指针，或者 `numberOfElements` 参数小于或等于 0，或传递的块没有以 null 终止，则调用无效参数处理，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些函数返回`EINVAL` 并将 `errno` 设置为`EINVAL`。  
  
## 备注  
 `_strset_s` 函数将`str` 的所有字符设置为`c`（转换为 `char`），不包括终止 null 字符。  `_wcsset_s` 和 `_mbsset_s` 是宽字符，属于 `_strset_s` 的多节字字符版本。  参数和返回值的数据类型相应地改变。  否则这些函数具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsset_s`|`_strset_s`|`_mbsset_s`|`_wcsset_s`|  
|`_tcsset_s_l`|`_strset_s_l`|`_mbsset_s_l`|`_wcsset_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strset_s`|\<string.h\>|  
|`_strset_s_l`|\<tchar.h\>|  
|`_wcsset_s`|\<string.h\> 或 \<wchar.h\>|  
|`_wcsset_s_l`|\<tchar.h\>|  
|`_mbsset_s`, `_mbsset_s_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strset_s.c  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char string[] = "Fill the string with something.";  
   printf( "Before: %s\n", string );  
   _strset_s( string, _countof(string), '*' );  
   printf( "After:  %s\n", string );  
}  
```  
  
  **以前：用一些填充字符串。**  
**以后：\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\***   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbset、\_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)