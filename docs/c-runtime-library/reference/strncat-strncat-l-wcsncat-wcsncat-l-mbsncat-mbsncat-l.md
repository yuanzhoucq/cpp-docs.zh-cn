---
title: "strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l | Microsoft Docs"
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
  - "strncat"
  - "_strncat_l"
  - "_mbsncat"
  - "_mbsncat_l"
  - "wcsncat"
  - "wcsncat_l"
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
  - "_tcsncat_l"
  - "_wcsncat_l"
  - "_tcsnccat_l"
  - "_mbsncat"
  - "_strncat_l"
  - "strncat"
  - "_tcsnccat"
  - "_mbsncat_l"
  - "_ftcsncat"
  - "wcsncat"
  - "_tcsncat"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsncat 函数"
  - "_mbsncat 函数"
  - "_mbsncat_l 函数"
  - "_tcsncat 函数"
  - "_tcsncat_l 函数"
  - "_tcsnccat 函数"
  - "_tcsnccat_l 函数"
  - "追加字符串"
  - "字符 [C++], 追加到字符串"
  - "串联字符串"
  - "ftcsncat 函数"
  - "mbsncat 函数"
  - "mbsncat_l 函数"
  - "字符串串联 [C++]"
  - "字符串 [C++], 追加"
  - "strncat 函数"
  - "tcsncat 函数"
  - "tcsncat_l 函数"
  - "tcsnccat 函数"
  - "tcsnccat_l 函数"
  - "wcsncat 函数"
ms.assetid: de67363b-68c6-4ca5-91e3-478610ad8159
caps.latest.revision: 29
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

向字符串追加字符。  关于这些函数的更多安全版本；请参见 [strncat\_s、\_strncat\_s\_l、wcsncat\_s、\_wcsncat\_s\_l、\_mbsncat\_s、\_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbsncat` 和 `_mbsncat_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *strncat(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
wchar_t *wcsncat(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
unsigned char *_mbsncat(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count  
);  
unsigned char *_mbsncat_l(  
   unsigned char *strDest,  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
char *strncat(  
   char (&strDest)[size],  
   const char *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
wchar_t *wcsncat(  
   wchar_t (&strDest)[size],  
   const wchar_t *strSource,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsncat(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count  
); // C++ only  
template <size_t size>  
unsigned char *_mbsncat_l(  
   unsigned char (&strDest)[size],  
   const unsigned char *strSource,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `strDest`  
 以NULL终止的目标字符串。  
  
 `strSource`  
 null 终止的源字符串。  
  
 `count`  
 要追加的字符数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回指向目标字符串的指针。  没有保留任何返回值以指示错误。  
  
## 备注  
 `strncat` 函数至多追加`strSource`的第一 `count` 字符到`strDest`。  `strSource` 的初始字符覆盖 `strDest`终止 null 字符。  在 `count` 字符追加之前，如果 null 字符出现在`strSource`中，`strncat` 追加`strSource`的所有字符，直到遇到 null 字符。  如果 `count` 比 `strSource`的长度更长时，使用`strSource`的长度代替 `count`。  任何情况下，结果字符串以 null 字符终结。  如果复制出现在重叠的字符串之间，则该行为不确定。  
  
> [!IMPORTANT]
>  `strncat` 不检查`strDest`是否有足够空间;因此它是缓冲区溢出的一个可能的原因。  注意 `count` 限制追加的字符数；它不是限制 `strDest`的范围。  请参见下面的示例。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 `wcsncat` 和 `_mbsncat` 是宽字符，属于 `strncat` 的多节字字符版本。  字符串参数和 `wcsncat` 的返回值是宽字符串；`_mbsncat` 的参数和返回值为多字节字符串。  否则这三个函数否则具有相同行为。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 在 C\+\+ 中，这些函数有重载模板。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsncat`|`strncat`|`_mbsnbcat`|`wcsncat`|  
|`_tcsncat_l`|`_strncat_l`|`_mbsnbcat_l`|`_wcsncat_l`|  
  
> [!NOTE]
>  `_strncat_l` 和 `_wcsncat_l` 没有区域设置依赖项，且不应该直接调用。  它们提供`_tcsncat_l`的内部使用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strncat`|\<string.h\>|  
|`wcsncat`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsncat`|\<mbstring.h\>|  
|`_mbsncat_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strncat.c  
// Use strcat and strncat to append to a string.  
#include <stdlib.h>  
  
#define MAXSTRINGLEN 39  
  
char string[MAXSTRINGLEN+1];  
// or char *string = malloc(MAXSTRINGLEN+1);  
  
void BadAppend( char suffix[], int n )  
{  
   strncat( string, suffix, n );  
}  
  
void GoodAppend( char suffix[], size_t n )  
{  
   strncat( string, suffix, __min( n, MAXSTRINGLEN-strlen(string)) );  
}  
  
int main( void )  
{  
   string[0] = '\0';  
   printf( "string can hold up to %d characters\n", MAXSTRINGLEN );  
  
   strcpy( string, "This is the initial string!" );  
   // concatenate up to 20 characters...  
   BadAppend( "Extra text to add to the string...", 20 );  
   printf( "After BadAppend :  %s (%d chars)\n", string, strlen(string) );  
  
   strcpy( string, "This is the initial string!" );  
   // concatenate up to 20 characters...  
   GoodAppend( "Extra text to add to the string...", 20 );  
   printf( "After GoodAppend:  %s (%d chars)\n", string, strlen(string) );  
}  
```  
  
## Output  
  
```  
string can hold up to 39 characters  
After BadAppend :  This is the initial string!Extra text to add to (47 chars)  
After GoodAppend:  This is the initial string!Extra text t (39 chars)  
```  
  
 请注意 `BadAppend` 导致缓冲区溢出。  
  
## .NET Framework 等效项  
 [System::String::Concat](https://msdn.microsoft.com/en-us/library/system.string.concat.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset、\_strset\_l、\_wcsset、\_wcsset\_l、\_mbsset、\_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)