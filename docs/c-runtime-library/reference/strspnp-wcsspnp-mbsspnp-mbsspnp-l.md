---
title: "_strspnp、_wcsspnp、_mbsspnp、_mbsspnp_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsspnp"
  - "_wcsspnp"
  - "_mbsspnp_l"
  - "_strspnp"
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
apitype: "DLLExport"
f1_keywords: 
  - "_tcsspnp"
  - "_mbsspnp"
  - "strspnp"
  - "_ftcsspnp"
  - "_mbsspnp_l"
  - "wcsspnp"
  - "mbsspnp_l"
  - "_wcsspnp"
  - "_strspnp"
  - "mbsspnp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsspnp 函数"
  - "_mbsspnp_l 函数"
  - "_strspnp 函数"
  - "_tcsspnp 函数"
  - "_wcsspnp 函数"
  - "mbsspnp 函数"
  - "mbsspnp_l 函数"
  - "strspnp 函数"
  - "tcsspnp 函数"
  - "wcsspnp 函数"
ms.assetid: 1ce18100-2edd-4c3b-af8b-53f204d80233
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strspnp、_wcsspnp、_mbsspnp、_mbsspnp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回一个指向给定的字符串而不是另一个给定的字符串的第一个字符的指针。  
  
> [!IMPORTANT]
>  `_mbsspnp` 和 `_mbsspnp_l` 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_strspnp(  
   const char *str,  
   const char *charset  
);  
wchar_t *_wcsspnp(  
   const unsigned wchar_t *str,  
   const unsigned wchar_t *charset  
);  
unsigned char *_mbsspnp(  
   const unsigned char *str,  
   const unsigned char *charset  
);  
unsigned char *_mbsspnp_l(  
   const unsigned char *str,  
   const unsigned char *charset,  
   _locale_t locale  
);  
  
```  
  
#### 参数  
 `str`  
 要搜索的 null 终止的字符串。  
  
 `charset`  
 null 终止的字符集。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 `_strspnp`、`_wcsspnp`和 `_mbsspnp` 返回指向不属于将 `charset`的字符。`str` 的第一个字符*。*如果 `str` 完全由从`charset`而来的字符，每一个函数会返回 `NULL`。对于其中每个实例，没有任何返回值保留指示错误。  
  
## 备注  
 `_mbsspnp` 函数返回一个指针指向多字符，它是`str` 的第一个字符。它不属于`charset`的字符集。  `_mbsspnp` 根据当前正在使用的[多字节代码页](../../c-runtime-library/code-pages.md) 识别多字节字符序列。  搜索不包括终止空字符。  
  
 如果 `str` 或 `charset`都 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则该函数返回 `NULL` 并将 `errno` 设置为 `EINVAL`。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsspnp`|`_strspnp`|`_mbsspnp`|`_wcsspnp`|  
  
 `_strspnp` 和`_wcsspnp` 是单字节字符，且是 `_mbsspnp` 的宽字符版本。  `_strspnp` 和 `_wcsspnp` 与 `_mbsspnp`行为相同 ;否则，它们仅用于提供映射不应为任何其他原因使用。  有关详细信息，请参阅 [使用一般文本映射](../../c-runtime-library/using-generic-text-mappings.md) 和 [一般文本映射](../../c-runtime-library/generic-text-mappings.md)。  
  
 `_mbsspnp_l`  相同，除非使用传递的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mbsspnp`|\<mbstring.h\>|  
|`_strspnp`|\<tchar.h\>|  
|`_wcsspnp`|\<tchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_mbsspnp.c  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void ) {  
   const unsigned char string1[] = "cabbage";  
   const unsigned char string2[] = "c";  
   unsigned char *ptr = 0;  
   ptr = _mbsspnp( string1, string2 );  
   printf( "%s\n", ptr);  
}  
```  
  
## Output  
  
```  
abbage  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)