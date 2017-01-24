---
title: "_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l | Microsoft Docs"
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
  - "_mbsnset"
  - "_strnset"
  - "_mbsnset_l"
  - "_wcsnset_l"
  - "_wcsnset"
  - "_strnset_l"
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
  - "_tcsncset_l"
  - "mbsnset_l"
  - "_tcsnset_l"
  - "_fstrnset"
  - "_wcsnset_l"
  - "_ftcsnset"
  - "wcsnset_l"
  - "_mbsnset_l"
  - "_strnset"
  - "_tcsnset"
  - "_strnset_l"
  - "mbsnset"
  - "strnset_l"
  - "_mbsnset"
  - "_wcsnset"
  - "_tcsncset"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrnset 函数"
  - "_ftcsnset 函数"
  - "_mbsnset 函数"
  - "_mbsnset_l 函数"
  - "_strnset 函数"
  - "_strnset_l 函数"
  - "_tcsncset 函数"
  - "_tcsncset_l 函数"
  - "_tcsnset 函数"
  - "_tcsnset_l 函数"
  - "_wcsnset 函数"
  - "_wcsnset_l 函数"
  - "字符 [C++], 初始化至格式"
  - "fstrnset 函数"
  - "ftcsnset 函数"
  - "初始化字符"
  - "mbsnset 函数"
  - "mbsnset_l 函数"
  - "字符串 [C++], 初始化"
  - "strnset_l 函数"
  - "tcsncset 函数"
  - "tcsnset 函数"
  - "tcsnset_l 函数"
  - "wcsnset_l 函数"
ms.assetid: 3f306489-5763-48e5-b939-aefee7c94ef5
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始化字符串到特定字符。  有关这些函数存在的更多安全版本；请参见 [\_strnset\_s、\_strnset\_s\_l、\_wcsnset\_s、\_wcsnset\_s\_l、\_mbsnset\_s、\_mbsnset\_s\_l](../../c-runtime-library/reference/strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbsnset` 和 `_mbsnset_l` 不能在 Windows 运行时中执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_strnset(  
   char *str,  
   int c,  
   size_t count   
);  
char *_strnset_l(  
   char *str,  
   int c,  
   size_t count,  
   locale_t locale  
);  
wchar_t *_wcsnset(  
   wchar_t *str,  
   wchar_t c,  
   size_t count   
);  
wchar_t *_wcsnset_l(  
   wchar_t *str,  
   wchar_t c,  
   size_t count,  
   _locale_t locale  
);  
unsigned char *_mbsnset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnset_l(  
   unsigned char *str,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 要修改的字符串。  
  
 `c`  
 字符设置。  
  
 `count`  
 要设置的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回指向修改后的字符串的指针。  
  
## 备注  
 `_strnset` 功能集，至多，`str` 的第一个 `count` 字符到`c` \(转换为 `char`\)。  如果 `count` 比 `str`的长度更长时，使用`str` 代替 `count`。  
  
 `_wcsnset` 和 `_mbsnset`  是宽字符， `_strnset` 的多节字字符版本。  参数和 `_wcsnset`  的返回值是宽字符串；`_mbsnset` 的参数和返回值为多字节字符串。  否则这三个函数否则具有相同行为。  
  
 `_mbsnset` 确认其参数； 如果 `str` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行，`_mbsnset`  返回空，设置 `errno` 为`EINVAL`。  `_strnset` 和 `_wcsnset` 不验证其参数。  
  
 输出值受区域设置的 `LC_CTYPE`  类别设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用通过的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strnset`|\<string.h\>|  
|`_strnset_l`|\<tchar.h\>|  
|`_wcsnset`|\<string.h\> 或 \<wchar.h\>|  
|`_wcsnset_l`|\<tchar.h\>|  
|`_mbsnset`, `_mbsnset_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strnset.c  
// compile with: /W3  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 characters of string to be *'s */  
   printf( "Before: %s\n", string );  
   _strnset( string, '*', 4 ); // C4996  
   // Note: _strnset is deprecated; consider using _strnset_s  
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