---
title: "_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsset"
  - "_mbsset"
  - "_strset_l"
  - "_strset"
  - "_wcsset_l"
  - "_mbsset_l"
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
  - "mbsset"
  - "_strset_l"
  - "_mbsset"
  - "_strset"
  - "mbsset_l"
  - "strset_l"
  - "_wcsset"
  - "_ftcsset"
  - "wcsset_l"
  - "_tcsset_l"
  - "_mbsset_l"
  - "_wcsset_l"
  - "_fstrset"
  - "_tcsset"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrset 函数"
  - "_ftcsset 函数"
  - "_mbsset 函数"
  - "_mbsset_l 函数"
  - "_strset 函数"
  - "_strset_l 函数"
  - "_tcsset 函数"
  - "_tcsset_l 函数"
  - "_wcsset 函数"
  - "_wcsset_l 函数"
  - "字符 [C++], 设置"
  - "fstrset 函数"
  - "ftcsset 函数"
  - "mbsset 函数"
  - "mbsset_l 函数"
  - "字符串 [C++], 设置字符"
  - "strset_l 函数"
  - "tcsset 函数"
  - "tcsset_l 函数"
  - "wcsset_l 函数"
ms.assetid: c42ded42-2ed9-4f06-a0a9-247ba305473a
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串的字符设置为一个字符。  有关这些函数的更多安全版本，请参见 [\_strset\_s、\_strset\_s\_l、\_wcsset\_s、\_wcsset\_s\_l、\_mbsset\_s、\_mbsset\_s\_l](../../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbsset` 和 `_mbsset_l` 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_strset(  
   char *str,  
   int c   
);  
char *_strset_l(  
   char *str,  
   int c,  
   locale_t locale  
);  
wchar_t *_wcsset(  
   wchar_t *str,  
   wchar_t c   
);  
wchar_t *_wcsset_l(  
   wchar_t *str,  
   wchar_t c,  
   locale_t locale  
);  
unsigned char *_mbsset(  
   unsigned char *str,  
   unsigned int c   
);  
unsigned char *_mbsset_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 设置 null 终止的字符串。  
  
 `c`  
 字符设置。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回指向修改后的字符串的指针。  
  
## 备注  
 `_strset` 函数将 `c` 设置为`str` 的所有字符 \(不包括终止 null 字符\) ，转换为 `char`。  `_wcsset` 和 `_mbsset_l` 是 `_strset`的宽字符和多字节字符版本，并且参数的数据类型和返回值相应地改变。  否则这些函数具有相同行为。  
  
 `_mbsset`验证其参数。  如果 `str` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续， `_mbsset` 返回 `NULL`并设置`errno` 为 `EINVAL`。  `_strset` 和 `_wcsset` 不验证其参数。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  除了不具有使用当前区域的 `_l` 后缀以及具有 `_l` 后缀而不是使用传入的区域参数，这些函数的版本相同。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
> [!IMPORTANT]
>  这些函数可能容易受到的缓冲区溢出的威胁。  缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsset`|`_strset`|`_mbsset`|`_wcsset`|  
|`_tcsset_l`|`_strset_l`|`_mbsset_l`|`_wcsset_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strset`|\<string.h\>|  
|`_strset_l`|\<tchar.h\>|  
|`_wcsset`|\<string.h\> 或 \<wchar.h\>|  
|`_wcsset_l`|\<tchar.h\>|  
|`_mbsset`, `_mbsset_l`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strset.c  
// compile with: /W3  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[] = "Fill the string with something.";  
   printf( "Before: %s\n", string );  
   _strset( string, '*' ); // C4996  
   // Note: _strset is deprecated; consider using _strset_s instead  
   printf( "After:  %s\n", string );  
}  
```  
  
  **以前：用一些填充字符串。**  
**以后：\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\***   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
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