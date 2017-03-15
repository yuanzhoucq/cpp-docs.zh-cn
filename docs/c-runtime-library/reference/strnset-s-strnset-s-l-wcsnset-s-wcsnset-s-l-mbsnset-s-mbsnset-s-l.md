---
title: "_strnset_s、_strnset_s_l、_wcsnset_s、_wcsnset_s_l、_mbsnset_s、_mbsnset_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnset_s_l"
  - "_strnset_s"
  - "_mbsnset_s"
  - "_strnset_s_l"
  - "_wcsnset_s_l"
  - "_wcsnset_s"
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
  - "_mbsnset_s_l"
  - "wcsnset_s"
  - "_tcsnset_s_l"
  - "_wcsnset_s"
  - "_mbsnset_s"
  - "_wcsnset_s_l"
  - "_strnset_s_l"
  - "strnset_s_l"
  - "_tcsnset_s"
  - "_strnset_s"
  - "strnset_s"
  - "mbsnset_s_l"
  - "mbsnset_s"
  - "wcsnset_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnset_s 函数"
  - "_mbsnset_s_l 函数"
  - "_strnset_s 函数"
  - "_strnset_s_l 函数"
  - "_tcsnset_s 函数"
  - "_tcsnset_s_l 函数"
  - "_wcsnset_s 函数"
  - "初始化字符"
  - "mbsnset_s 函数"
  - "mbsnset_s_l 函数"
  - "strnset_s 函数"
  - "strnset_s_l 函数"
  - "tcsnset_s 函数"
  - "tcsnset_s_l 函数"
  - "wcsnset_s 函数"
ms.assetid: 9cf1b321-b5cb-4469-b285-4c07cfbd8813
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _strnset_s、_strnset_s_l、_wcsnset_s、_wcsnset_s_l、_mbsnset_s、_mbsnset_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始化字符串到给定字符。  [\_strnset、\_strnset\_l、\_wcsnset、\_wcsnset\_l、\_mbsnset、\_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  `_mbsnset_s` 和 `_mbsnset_s_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
errno_t _strnset_s(  
   char *str,  
   size_t numberOfElements,  
   int c,  
   size_t count   
);  
errno_t _strnset_s_l(  
   char *str,  
   size_t numberOfElements,  
   int c,  
   size_t count,  
   locale_t locale  
);  
errno_t _wcsnset_s(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c,  
   size_t count   
);  
errno_t _wcsnset_s_l(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c,  
   size_t count,  
   _locale_t locale  
);  
errno_t _mbsnset_s(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c,  
   size_t count   
);  
errno_t _mbsnset_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 要修改的字符串。  
  
 `numberOfElements`  
 `str`缓冲区的大小。  
  
 `c`  
 字符设置。  
  
 `count`  
 要设置的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果成功，则为零；否则为错误代码。  
  
 这些函数验证其参数。  如果 `str` 不是有效的 null 终止字符串或范围参数小于或等于 0，则无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，这些函数返回错误代码并设置 `errno` 为该错误代码。  如果更具体的值不适用，默认值错误代码是 `EINVAL`。  
  
## 备注  
 这些功能集，至多，`str` 的第一个 `count` 字符到`c`。  如果 `count` 比 `str`的长度更长时，使用`str` 的长度代替 `count`。  如果 `count` 比 `numberOfElements` 大，并且这两个参数大小比 `str`大，错误发生。  
  
 `_wcsnset_s` 和 `_mbsnset_s`  是宽字符，并且是 `_strnset_s` 的多节字字符版本。  `_wcsnset_s` 的字符串参数是宽字符字符串；`_mbsnset_s` 是 `` 多字节字符字符串。  否则这三个函数否则具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE`  类别设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用通过的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 这些函数的调试版本首先用 0xFD 填充缓冲区。  若要禁用此行为，请使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnset_s`|`_strnset_s`|`_mbsnbset_s`|`_wcsnset_s`|  
|`_tcsnset_s_l`|`_strnset_s_l`|`_mbsnbset_s_l`|`_wcsnset_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strnset_s`|\<string.h\>|  
|`_strnset_s_l`|\<tchar.h\>|  
|`_wcsnset_s`|\<string.h\> 或 \<wchar.h\>|  
|`_wcsnset_s_l`|\<tchar.h\>|  
|`_mbsnset_s`, `_mbsnset_s_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strnset_s.c  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 characters of string to be *'s */  
   printf( "Before: %s\n", string );  
   _strnset_s( string, sizeof(string), '*', 4 );  
   printf( "After:  %s\n", string );  
}  
```  
  
  **之前：这是一项测试**  
**之后：\*\*\*\*是一项测试**   
## .NET Framework 等效项  
 [System::String::Replace](https://msdn.microsoft.com/en-us/library/system.string.replace.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)