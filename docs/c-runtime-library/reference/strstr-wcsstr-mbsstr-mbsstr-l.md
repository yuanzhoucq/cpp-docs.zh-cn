---
title: "strstr、wcsstr、_mbsstr、_mbsstr_l | Microsoft Docs"
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
  - "_mbsstr"
  - "wcsstr"
  - "_mbsstr_l"
  - "strstr"
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
  - "_fstrstr"
  - "_ftcsstr"
  - "strstr"
  - "wcsstr"
  - "_mbsstr"
  - "_tcsstr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrstr 函数"
  - "_ftcsstr 函数"
  - "_mbsstr 函数"
  - "_mbsstr_l 函数"
  - "_tcsstr 函数"
  - "fstrstr 函数"
  - "ftcsstr 函数"
  - "mbsstr 函数"
  - "mbsstr_l 函数"
  - "字符串 [C++], 搜索"
  - "strstr 函数"
  - "子字符串, 查找"
  - "tcsstr 函数"
  - "wcsstr 函数"
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strstr、wcsstr、_mbsstr、_mbsstr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回指向在字符串的一个搜索字符串的第一个匹配项。  
  
> [!IMPORTANT]
>  `_mbsstr` 和 `_mbsstr_l` 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. 中执行应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *strstr(  
   const char *str,  
   const char *strSearch   
); // C only  
char *strstr(  
   char *str,  
   const char *strSearch   
); // C++ only  
const char *strstr(  
   const char *str,  
   const char *strSearch   
); // C++ only  
wchar_t *wcsstr(  
   const wchar_t *str,  
   const wchar_t *strSearch   
); // C only  
wchar_t *wcsstr(  
   wchar_t *str,  
   const wchar_t *strSearch   
); // C++ only  
const wchar_t *wcsstr(  
   const wchar_t *str,  
   const wchar_t *strSearch   
); // C++ only  
unsigned char *_mbsstr(  
   const unsigned char *str,  
   const unsigned char *strSearch   
); // C only  
unsigned char *_mbsstr(  
   unsigned char *str,  
   const unsigned char *strSearch   
); // C++ only  
const unsigned char *_mbsstr(  
   const unsigned char *str,  
   const unsigned char *strSearch   
); // C++ only  
unsigned char *_mbsstr_l(  
   const unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C only  
unsigned char *_mbsstr_l(  
   unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsstr_l(  
   const unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `str`  
 要搜索的 null 终止的字符串。  
  
 `strSearch`  
 要搜索 null 终止的字符串。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 如果 `strSearch` 未出现在 `str`，则返回指向 `strSearch` 的第一个匹配项在 `str`的指针或 `NULL`指针。  如果 `strSearch` 指向长度为零的字符串，则函数返回 `str`。  
  
## 备注  
 `strstr` 函数返回指向 `strSearch` 第一个匹配项 `str`的指针。  搜索不包括终止空字符。  `wcsstr` 是 `strstr` 的宽字符版本；`_mbsstr` 是多字节字符版本。  参数和 `wcsstr` 的返回值是宽字符字符串；`_mbsstr` 的参数和返回值为多字节字符字符串。  `_mbsstr`验证其参数。  如果 `str` 或 `strSearch` 为 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则将 `_mbsstr`将 `errno` 设置为 `EINVAL`，并且返回0。  `strstr` 和 `wcsstr` 不验证其参数。  否则这三个函数否则具有相同行为。  
  
> [!IMPORTANT]
>  这些功能可能会招致从一个缓冲区溢出问题的威胁。  缓冲区溢出问题可用来攻击系统，因为它们允许执行任意的代码，这可能导致权限的非确保提升。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 在 C 中，这些函数采用第一个参数的一个 `const` 指针。  在 C\+\+ 中，有两个重载可用。  采用指向 `const` 的指针的重载返回指向 `const` 的指针；采用指向非`const` 的版本的指针返回指向非`const` 的指针。  如果这些函数的 `const` 和非`const` 版本可用，则会定义宏 \_CONST\_CORRECT\_OVERLOADS。  如果这两个 C\+\+ 重载都需要非 `const` 行为，请定义符号 \_CONST\_RETURN。  
  
 输出值受 `LC_CTYPE` 区域\-分类设置的影响；有关更多信息，请参见 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数版本对任何区域设置相关行为使用当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传入的区域设置。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|  
|**无**|**无**|`_mbsstr_l`|**无**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strstr`|\<string.h\>|  
|`wcsstr`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strstr.c  
  
#include <string.h>  
#include <stdio.h>  
  
char str[] =    "lazy";  
char string[] = "The quick brown dog jumps over the lazy fox";  
char fmt1[] =   "         1         2         3         4         5";  
char fmt2[] =   "12345678901234567890123456789012345678901234567890";  
  
int main( void )  
{  
   char *pdest;  
   int  result;  
   printf( "String to be searched:\n   %s\n", string );  
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );  
   pdest = strstr( string, str );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf( "%s found at position %d\n", str, result );  
   else  
      printf( "%s not found\n", str );  
}  
```  
  
  **要搜索的字符串。**  
 **敏捷的棕色狗跳过了懒惰的狐狸。**  
 **1         2         3         4         5**  
 **12345678901234567890123456789012345678901234567890**  
**延迟发现位置 36**   
## .NET Framework 等效项  
 [System::String::IndexOf](https://msdn.microsoft.com/en-us/library/system.string.indexof.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strpbrk、wcspbrk、\_mbspbrk、\_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [basic\_string::find](../Topic/basic_string::find.md)