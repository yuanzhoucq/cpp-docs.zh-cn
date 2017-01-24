---
title: "strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l | Microsoft Docs"
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
  - "_mbspbrk"
  - "wcspbrk"
  - "_mbspbrk_l"
  - "strpbrk"
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
  - "_fstrpbrk"
  - "_mbspbrk"
  - "strpbrk"
  - "_tcspbrk"
  - "_ftcspbrk"
  - "wcspbrk"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrpbrk 函数"
  - "_ftcspbrk 函数"
  - "_mbspbrk 函数"
  - "_mbspbrk_l 函数"
  - "_tcspbrk 函数"
  - "字符集 [C++], 扫描字符串以查找字符"
  - "字符 [C++], 扫描字符串"
  - "fstrpbrk 函数"
  - "ftcspbrk 函数"
  - "mbspbrk 函数"
  - "mbspbrk_l 函数"
  - "字符串 [C++], 扫描"
  - "strpbrk 函数"
  - "tcspbrk 函数"
  - "wcspbrk 函数"
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
caps.latest.revision: 30
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指定的字符集扫描字符的字符串。  
  
> [!IMPORTANT]
>  `_mbspbrk` 和 `_mbspbrk_l` 不能在 Windows 运行时执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C only  
char *strpbrk(  
   char *str,  
   const char *strCharSet   
); // C++ only  
const char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C++ only  
wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C only  
wchar_t *wcspbrk(  
   wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
const wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C only  
unsigned char *_mbspbrk(  
   unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
const unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C only  
unsigned char *_mbspbrk_l(  
   unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char* strCharSet,  
   _locale_t locale  
); // C++ only  
```  
  
#### 参数  
 `str`  
 以null 终止的搜索字符串。  
  
 `strCharSet`  
 null 终止的字符集。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 例如，如果两个字符串实参没有相同的字符，返回指向`str`中的`strCharSet`任意字符第一个匹配的指针 或 `NULL` 指针。  
  
## 备注  
 `strpbrk` 函数返回指向`str` 中出现的第一个匹配项的指针，该指针属于 `strCharSet`字符集 。  搜索不包括终止空字符。  
  
 `wcspbrk` 和 `_mbspbrk` 是宽字符，属于 `strpbrk` 的多节字字符版本。  参数和 `wcspbrk` 的返回值是宽字符字符串；`_mbspbrk` 的参数和返回值为多字节字符字符串。  
  
 `_mbspbrk`验证其参数。  如果 `str` 或 `strCharSet` 为 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行， `_mbspbrk` 返回 `NULL`并设置`errno` 为 `EINVAL`。  `strpbrk` 和 `wcspbrk` 不验证其参数。  否则这三个函数否则具有相同行为。  
  
 `_mbspbrk` 类似于 `_mbscspn`，但 `_mbspbrk` 返回指针而不是类型 [size\_t](../../c-runtime-library/standard-types.md)的值。  
  
 在 C 中，这些函数采用第一个参数的一个 `const` 指针。  在 C\+\+ 中，有两个重载可用。  采用指向 `const` 的指针的重载返回指向 `const` 的指针；采用指向非`const` 的版本的指针返回指向非`const` 的指针。  如果这些函数的 `const` 和非`const` 版本可用，则会定义宏 \_CONST\_CORRECT\_OVERLOADS。  如果这两个 C\+\+ 重载都需要非 `const` 行为，请定义符号 \_CONST\_RETURN。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用通过的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|  
|**无**|**无**|`_mbspbrk_l`|**无**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strpbrk`|\<string.h\>|  
|`wcspbrk`|\<string.h\> 或 \<wchar.h\>|  
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strpbrk.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";  
   char *result = NULL;  
  
   // Return pointer to first digit in "string".  
   printf( "1: %s\n", string );  
   result = strpbrk( string, "0123456789" );  
   printf( "2: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "3: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "4: %s\n", result );  
}  
```  
  
  **1：3 个人和 2 个男孩吃了 5 头猪**  
**2：3 个人和 2 个男孩吃了 5 头猪**  
**3：2 个男孩吃了 5 头猪**  
**4：5 头猪**   
## .NET Framework 等效项  
 [System::String::IndexOfAny](https://msdn.microsoft.com/en-us/library/system.string.indexofany.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strchr、wcschr、\_mbschr、\_mbschr\_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)