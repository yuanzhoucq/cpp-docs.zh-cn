---
title: "strcmp、wcscmp、_mbscmp | Microsoft Docs"
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
  - "wcscmp"
  - "_mbscmp"
  - "strcmp"
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
  - "_mbscmp"
  - "wcscmp"
  - "strcmp"
  - "_tcscmp"
  - "_ftcscmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcscmp 函数"
  - "_mbscmp 函数"
  - "_tcscmp 函数"
  - "ftcscmp 函数"
  - "mbscmp 函数"
  - "strcmp 函数"
  - "字符串比较 [C++]"
  - "字符串 [C++], 比较"
  - "tcscmp 函数"
  - "wcscmp 函数"
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcmp、wcscmp、_mbscmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比较字符串。  
  
> [!IMPORTANT]
>  `_mbscmp` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int strcmp(  
   const char *string1,  
   const char *string2   
);  
int wcscmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
```  
  
#### 参数  
 `string1`, `string2`  
 要比较的 null 终止的字符串。  
  
## 返回值  
 这些函数的返回值指明 `string1` 和 `string2` 的序号关系。  
  
|值|string1 与 string2 的关系|  
|-------|---------------------------|  
|\< 0|`string1` 小于 `string2`。|  
|0|`string1` 等于 `string2`|  
|\> 0|`string1` 大于 `string2`|  
  
 参数验证错误时，`_mbscmp` 返回 `_NLSCMPERROR`，该返回值是在 \<string.h\> 和 \<mbstring.h\> 中定义的。  
  
## 备注  
 `strcmp` 函数对 `string1` 和 `string2` 执行序号比较并返回一个指示它们关系的值。  `wcscmp` 和 `_mbscmp` 分别是 `strcmp` 的宽字符和多字节字符版本。  `_mbscmp` 根据当前的多字节代码页识别多字节字符序列，并在发生错误时返回 `_NLSCMPERROR`。  有关更多信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。  同样，如果 `string1` 或 `string2` 为 null 指针，则 `_mbscmp` 将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许继续执行，则 `_mbscmp` 返回 `_NLSCMPERROR`，并将 `errno` 设置为 `EINVAL`。  `strcmp` 和 `wcscmp` 不会验证其参数。  否则这三个函数否则具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscmp`|`strcmp`|`_mbscmp`|`wcscmp`|  
  
 `strcmp` 函数与 `strcoll` 的不同之处在于 `strcmp` 比较是按顺序进行的且不受区域设置影响。  `strcoll` 通过使用当前区域设置的 `LC_COLLATE` 类别以字典顺序来比较字符串。  有关 `LC_COLLATE` 类别的详细信息，请参阅 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 在“C”区域设置中，字符集 \(ASCII 字符集\) 中的字符顺序与字典中的字符顺序一样。  但是在其他区域设置中，字符集中的字符顺序可能与字典中的顺序不同。  例如，在某些欧洲区域设置中，字符集中的字符“a”（值 0x61）位于字符“ä”（值 0xE4）之前，但在字典顺序中，字符“ä”位于字符“a”之前。  
  
 在字符集和字典字符顺序不同的区域设置中，可以使用 `strcoll`（而非 `strcmp`）来对字符串进行字典顺序的比较。  或者，也可以对原始字符串使用 `strxfrm`，然后对结果字符串使用 `strcmp`。  
  
 `strcmp` 函数区分大小写。  `_stricmp`、`_wcsicmp` 和 `_mbsicmp` 在比较字符串之前会首先将它们转换成小写形式。  包含位于 ASCII 表中“Z”和“a”之间的两个字符串（“\[”、“`\`”、“\]”、“`^`”、“`_`”和“```”）将有不同的比较结果，具体取决于它们的大小写形式。  例如，如果比较采用小写形式，则 `"ABCDE"` 和 `"ABCD^"` 这两个字符串件将以一种方式进行比较 \(`"abcde"` \> `"abcd^"`\)，而如果比较采用大写形式，则这两个字符串将采用另一种方式进行比较 \(`"ABCDE"` \< `"ABCD^"`\)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strcmp`|\<string.h\>|  
|`wcscmp`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscmp`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_strcmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof (tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
  **比较字符串：**  
 **The quick brown dog jumps over the lazy fox**  
 **The QUICK brown dog jumps over the lazy fox**  
 **strcmp：字符串 1 大于字符串 2**  
 **\_stricmp：字符串 1 等于字符串 2**   
## .NET Framework 等效项  
 [System::String::CompareOrdinal](https://msdn.microsoft.com/en-us/library/system.string.compareordinal.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [\_memicmp、\_memicmp\_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [\_stricmp、\_wcsicmp、\_mbsicmp、\_stricmp\_l、\_wcsicmp\_l、\_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)