---
title: "strcspn、wcscspn、_mbscspn、_mbscspn_l | Microsoft Docs"
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
  - "_mbscspn_l"
  - "wcscspn"
  - "_mbscspn"
  - "strcspn"
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
  - "strcspn"
  - "_mbscspn"
  - "wcscspn"
  - "_ftcscspn"
  - "_tcscspn"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcscspn 函数"
  - "_mbscspn 函数"
  - "_mbscspn_l 函数"
  - "_tcscspn 函数"
  - "ftcscspn 函数"
  - "mbscspn 函数"
  - "mbscspn_l 函数"
  - "strcspn 函数"
  - "字符串 [C++], 搜索"
  - "tcscspn 函数"
  - "wcscspn 函数"
ms.assetid: f73f51dd-b533-4e46-ba29-d05c553708a6
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcspn、wcscspn、_mbscspn、_mbscspn_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回字符串中第一个匹配项的索引，字符的索引也是一组字符的索引。  
  
> [!IMPORTANT]
>  `_mbschr`和`_mbschr_l`不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
size_t strcspn(  
   const char *str,  
   const char *strCharSet   
);  
size_t wcscspn(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
);  
size_t _mbscspn(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
);  
size_t _mbscspn_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
);  
```  
  
#### 参数  
 `str`  
 以null 终止的搜索字符串。  
  
 `strCharSet`  
 null 终止的字符集。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这些函数返回在 `strCharSet`中的`str` 的第一个字符的索引。  如果`str`中的字符都不在 `strCharSet`，则返回值是 `str`的长度。  
  
 没有保留任何返回值以指示错误。  
  
## 备注  
 `wcscspn` 和 `_mbscspn` 是宽字符，属于 `strcspn` 的多节字字符版本。  `wcscspn`参数是宽字符字符串；`_mbscspn`参数的返回值为多字节字符字符串。  
  
 `_mbscspn`验证其参数。  如果`str` 或 `strCharSet`是空指针，则会调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则该函数返回 0 并将 `errno` 设置为 `EINVAL`。  `strcspn` 和 `wcscspn` 不验证其参数。  否则这三个函数否则具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscspn`|`strcspn`|`_mbscspn`|`wcscspn`|  
|`n/a`|`n/a`|`_mbscspn_l`|`n/a`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strcspn`|\<string.h\>|  
|`wcscspn`|\<string.h\> 或 \<wchar.h\>|  
|`_mbscspn`, `_mbscspn_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strcspn.c  
  
#include <string.h>  
#include <stdio.h>  
  
void test( const char * str, const char * strCharSet )  
{  
   int pos = strcspn( str, strCharSet );  
   printf( "strcspn( \"%s\", \"%s\" ) = %d\n", str, strCharSet, pos );      
}  
  
int main( void )  
{  
   test( "xyzbxz", "abc" );  
   test( "xyzbxz", "xyz" );  
   test( "xyzbxz", "no match" );  
   test( "xyzbxz", "" );  
   test( "", "abc" );  
   test( "", "" );  
}  
```  
  
  **strcspn\( "xyzbxz", "abc" \) \= 3**  
**strcspn\( "xyzbxz", "xyz" \) \= 0**  
**strcspn\( "xyzbxz", "no match" \) \= 6**  
**strcspn\( "xyzbxz", "" \) \= 6**  
**strcspn \("“abc”\) \= 0**  
**strcspn\( "", "" \) \= 0**   
## .NET Framework 等效项  
 [System::String::Substring](https://msdn.microsoft.com/en-us/library/system.string.substring.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)