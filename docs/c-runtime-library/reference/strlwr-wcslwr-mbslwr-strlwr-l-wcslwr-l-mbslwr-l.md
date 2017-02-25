---
title: "_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strlwr_l"
  - "_strlwr"
  - "_wcslwr_l"
  - "_mbslwr_l"
  - "_wcslwr"
  - "_mbslwr"
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
  - "_strlwr"
  - "wcslwr_l"
  - "_ftcslwr"
  - "mbslwr_l"
  - "_mbslwr"
  - "_wcslwr"
  - "strlwr_l"
  - "_tcslwr"
  - "mbslwr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcslwr 函数"
  - "_mbslwr 函数"
  - "_mbslwr_l 函数"
  - "_strlwr 函数"
  - "_strlwr_l 函数"
  - "_tcslwr 函数"
  - "_tcslwr_l 函数"
  - "_wcslwr 函数"
  - "_wcslwr_l 函数"
  - "大小写, 转换"
  - "转换大小写"
  - "转换大小写, CRT 函数"
  - "ftcslwr 函数"
  - "mbslwr 函数"
  - "mbslwr_l 函数"
  - "字符串转换 [C++], 大小写"
  - "字符串 [C++], 大小写"
  - "字符串 [C++], 转换大小写"
  - "strlwr_l 函数"
  - "tcslwr 函数"
  - "tcslwr_l 函数"
  - "wcslwr_l 函数"
ms.assetid: d279181d-2e7d-401f-ab44-6e7c2786a046
caps.latest.revision: 36
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 36
---
# _strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串转换为小写字母。  有关这些函数的更多安全版本，请参见 [\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbslwr` 和 `_mbslwr_l` 不能在 Windows 运行时中执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
char *_strlwr(  
   char * str  
);  
wchar_t *_wcslwr(  
   wchar_t * str  
);  
unsigned char *_mbslwr(  
   unsigned char * str  
);  
char *_strlwr_l(  
   char * str,  
   _locale_t locale  
);  
wchar_t *_wcslwr_l(  
   wchar_t * str,  
   _locale_t locale  
);  
unsigned char *_mbslwr_l(  
   unsigned char * str,  
   _locale_t locale   
);  
template <size_t size>  
char *_strlwr(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wcslwr(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
unsigned char *_mbslwr(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
char *_strlwr_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
wchar_t *_wcslwr_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
unsigned char *_mbslwr_l(  
   unsigned char (&str)[size],  
   _locale_t locale   
); // C++ only  
```  
  
#### 参数  
 `str`  
 转换空终止字符串为小写。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 这些函数均返回指向转换字符串的指针。  由于修改就地完成，返回的指针与作为输入参数传递的指针相同。  没有保留任何返回值以指示错误。  
  
## 备注  
 `_strlwr` 函数将 `str` 的所有大写字母转换为小写，这取决于 `LC_CTYPE` 类别设置区域设置。  其他字符不受影响。  有关`LC_CTYPE`的详细信息, 请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l`  后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
 `_wcslwr` 和 `_mbslwr` 函数是 `_strlwr`的宽字符和多字节字符版本。  参数和 `_wcslwr` 的返回值是宽字符字符串；`_mbslwr` 的参数和返回值为多字节字符字符串。  否则这三个函数否则具有相同行为。  
  
 如果 `str` 是一个 `NULL` 指针，无效参数处理程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回原始字符串并将 `errno` 设置为 `EINVAL` 。  
  
 在 C\+\+ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcslwr`|`_strlwr`|`_mbslwr`|`_wcslwr`|  
|`_tcslwr_l`|`_strlwr_l`|`_mbslwr_l`|`_wcslwr_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strlwr`, `_strlwr_l`|\<string.h\>|  
|`_wcslwr`, `_wcslwr_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbslwr`, `_mbslwr_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strlwr.c  
// compile with: /W3  
// This program uses _strlwr and _strupr to create  
// uppercase and lowercase copies of a mixed-case string.  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The String to End All Strings!";  
   char * copy1 = _strdup( string ); // make two copies  
   char * copy2 = _strdup( string );  
  
   _strlwr( copy1 ); // C4996  
   // Note: _strlwr is deprecated; consider using _strlwr_s instead  
   _strupr( copy2 ); // C4996  
   // Note: _strupr is deprecated; consider using _strupr_s instead  
  
   printf( "Mixed: %s\n", string );  
   printf( "Lower: %s\n", copy1 );  
   printf( "Upper: %s\n", copy2 );  
  
   free( copy1 );  
   free( copy2 );  
}  
```  
  
  **Mixed：所有字符串的结束字符串！**  
**Lower：所有字符串的结束字符串！**  
**Upper：所有字符串的结束字符串！**   
## .NET Framework 等效项  
 [System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [\_strupr、\_strupr\_l、\_mbsupr、\_mbsupr\_l、\_wcsupr\_l、\_wcsupr](../../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)