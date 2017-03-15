---
title: "strspn、wcsspn、_mbsspn、_mbsspn_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsspn_l"
  - "wcsspn"
  - "strspn"
  - "_mbsspn"
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
  - "_ftcsspn"
  - "wcsspn"
  - "_mbsspn"
  - "_tcsspn"
  - "strspn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsspn 函数"
  - "_mbsspn 函数"
  - "_mbsspn_l 函数"
  - "_tcsspn 函数"
  - "ftcsspn 函数"
  - "mbsspn 函数"
  - "mbsspn_l 函数"
  - "字符串 [C++], 搜索"
  - "strspn 函数"
  - "子字符串, 查找"
  - "tcsspn 函数"
  - "wcsspn 函数"
ms.assetid: d077284a-809f-4068-959e-c6d6262677eb
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# strspn、wcsspn、_mbsspn、_mbsspn_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回第一个字符的索引，在字符串中，它不属于字符集。  
  
> [!IMPORTANT]
>  `_mbsspn` 和 `_mbsspn_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
size_t strspn(  
   const char *str,  
   const char *strCharSet   
);  
size_t wcsspn(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
);  
size_t _mbsspn(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
);  
size_t _mbsspn_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 要搜索的 null 终止的字符串。  
  
 `strCharSet`  
 null 终止的字符集。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回指定完全包含在 `strCharSet`*.*的`str`子字符串的长度整数值。如果 `str` 从不在 `strCharSet`*的一个字符开始，* 该函数返回 0。  
  
## 备注  
 `strspn` 函数返回不属于`strCharSet`的字符集的`str` 的第一个字符的索引。  搜索不包括终止空字符。  
  
 `wcsspn` 和 `_mbsspn` 是宽字符，属于 `strspn` **.**的多节字字符版本。`wcsspn`参数是宽字符字符串；`_mbsspn`参数是多字节字符字符串。  `_mbsspn`验证其参数。  如果 `str` 或`strCharSet`为 `NULL`，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则将 `_mbspn`将 `errno` 设置为 `EINVAL`，并且返回0。  `strspn` 和 `wcsspn` 不验证其参数。  否则这三个函数否则具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsspn`|`strspn`|`_mbsspn`|`wcsspn`|  
|**无**|**无**|`_mbsspn_l`|**无**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strspn`|\<string.h\>|  
|`wcsspn`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsspn`, `_mbsspn_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strspn.c  
// This program uses strspn to determine  
// the length of the segment in the string "cabbage"  
// consisting of a's, b's, and c's. In other words,  
// it finds the first non-abc letter.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[] = "cabbage";  
   int  result;  
   result = strspn( string, "abc" );  
   printf( "The portion of '%s' containing only a, b, or c "  
           "is %d bytes long\n", string, result );  
}  
```  
  
  **仅包含 a、b、c 的'cabbage'的部分长为 5 个字节**   
## .NET Framework 等效项  
 [System::String::Substring](https://msdn.microsoft.com/en-us/library/system.string.substring.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strspnp、\_wcsspnp、\_mbsspnp、\_mbsspnp\_l](../../c-runtime-library/reference/strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)