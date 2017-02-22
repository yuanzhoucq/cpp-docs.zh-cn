---
title: "strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcstok_s_l"
  - "_mbstok_s_l"
  - "_mbstok_s"
  - "strtok_s"
  - "wcstok_s"
  - "_strtok_s_l"
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
  - "_tcstok_s_l"
  - "_wcstok_s_l"
  - "_tcstok_s"
  - "_mbstok_s_l"
  - "strtok_s"
  - "wcstok_s"
  - "_mbstok_s"
  - "_strtok_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbstok_s 函数"
  - "_mbstok_s_l 函数"
  - "_strtok_s_l 函数"
  - "_tcstok_s 函数"
  - "_tcstok_s_l 函数"
  - "_wcstok_s_l 函数"
  - "mbstok_s 函数"
  - "mbstok_s_l 函数"
  - "字符串 [C++], 搜索"
  - "strtok_s 函数"
  - "strtok_s_l 函数"
  - "标记, 在字符串中查找"
  - "wcstok_s 函数"
  - "wcstok_s_l 函数"
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用当前区域设置或通过的区域设置，查找在字符串中的下一个标记。  [strtok、\_strtok\_l、wcstok、\_wcstok\_l、\_mbstok、\_mbstok\_l](../../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  `_mbstok_s` 和 `_mbstok_s_l` 不能在 Windows 运行，执行的应用程序中使用。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
      char *strtok_s(  
char *strToken,  
const char *strDelimit,  
   char **context  
);  
char *_strtok_s_l(  
char *strToken,  
const char *strDelimit,  
   char **context,  
_locale_tlocale  
);  
wchar_t *wcstok_s(  
wchar_t *strToken,  
const wchar_t *strDelimit,   
   wchar_t**context  
);  
wchar_t *_wcstok_s_l(  
wchar_t *strToken,  
const wchar_t *strDelimit,   
   wchar_t**context,  
_locale_tlocale  
);  
unsigned char *_mbstok_s(  
unsigned char*strToken,  
const unsigned char *strDelimit,   
   char **context  
);  
unsigned char *_mbstok_s(  
unsigned char*strToken,  
const unsigned char *strDelimit,   
   char **context,  
_locale_tlocale  
);  
```  
  
#### 参数  
 `strToken`  
 字符串包含一个标记或一个以上的标记。  
  
 `strDelimit`  
 分隔符的设置。  
  
 `context`  
 用于存储调用 `strtok_s` 之间位置信息  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回指向在 `strToken`中的下一个标记的指针。  当未找到其他标记时，它们返回 `NULL` 。  每个调用都通过用在返回的标记后面的第一个分隔符替换 `NULL` 字符，修改 `strToken` 。  
  
### 错误情况  
  
|`strToken`|`strDelimit`|`context`|返回值|`errno`|  
|----------------|------------------|---------------|---------|-------------|  
|`NULL`|any|指向一个空指针|`NULL`|`EINVAL`|  
|any|`NULL`|any|`NULL`|`EINVAL`|  
|any|any|`NULL`|`NULL`|`EINVAL`|  
  
 如果 `strToken` 为 `NULL`，但上下文是一个指针指向有效的上下文指针，则不会产生错误。  
  
## 备注  
 `strtok_s` 函数来查找在 `strToken`的下一个标记。  将 `strDelimit` 字符的设置指定标记分隔符可能在当前调用的 `strToken` 找到的。  `wcstok_s` 和 `_mbstok_s`是宽字符，`strtok_s`是多节字字符版本。   `wcstok_s` 和 `_wcstok_s_l`参数和返回值都是宽字符字符串；`_mbstok_s` 和 `_mbstok_s_l`的参数和返回值为多字节字符字符串。  否则这三个函数否则具有相同行为。  
  
 此函数验证其参数。  如果出现一个错误状态，则当处于错误状态表中，将调用无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回`NULL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstok_s`|`strtok_s`|`_mbstok_s`|`wcstok_s`|  
|`_tcstok_s_l`|`_strtok_s_l`|`_mbstok_s_l`|`_wcstok_s_l`|  
  
 在第一次调用 `strtok_s` 函数跳过前导分隔符并返回指向在 `strToken`的第一个标记的指针，以空字符终止标记。  通过一系列 `strtok_s` 的调用，多个标记将被从 `strToken` 的其余部分拆开。  每个调用 `strtok_s` 通过插入 null 字符修改 `strToken` 在该返回的标记之后调用。  `context` 指针记录哪个字符串被读取，并记录将字符串下一个标记要读取的位置。  若要读取 `strToken`的下一个标记，请调用带有一个 `strToken` 参数的`NULL` 值的 `strtok_s` ，并传递相同的 `context` 参数。  `NULL` `strToken` 参数引起 `strtok_s` 搜索修改的 `strToken`的下一个标记。  `strDelimit` 参数可以接收一个调用到另一调用的任何值对，以便分隔符的设置可以更改。  
  
 因为 `context` 参数可用于 `strtok` 和 `_strtok_l`的静态缓冲区区域，同时在同一线程上分析两个字符串是可能的。  
  
 输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`strtok_s`|\<string.h\>|  
|`_strtok_s_l`|\<string.h\>|  
|`wcstok_s,`<br /><br /> `_wcstok_s_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbstok_s,`<br /><br /> `_mbstok_s_l`|\<mbstring.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strtok_s.c  
// In this program, a loop uses strtok_s  
// to print all the tokens (separated by commas  
// or blanks) in two strings at the same time.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
char string1[] =  
    "A string\tof ,,tokens\nand some  more tokens";  
char string2[] =  
    "Another string\n\tparsed at the same time.";  
char seps[]   = " ,\t\n";  
char *token1 = NULL;  
char *token2 = NULL;  
char *next_token1 = NULL;  
char *next_token2 = NULL;  
  
int main( void )  
{  
    printf( "Tokens:\n" );  
  
    // Establish string and get the first token:  
    token1 = strtok_s( string1, seps, &next_token1);  
    token2 = strtok_s ( string2, seps, &next_token2);  
  
    // While there are tokens in "string1" or "string2"  
    while ((token1 != NULL) || (token2 != NULL))  
    {  
        // Get next token:  
        if (token1 != NULL)  
        {  
            printf( " %s\n", token1 );  
            token1 = strtok_s( NULL, seps, &next_token1);  
        }  
        if (token2 != NULL)  
        {  
            printf("        %s\n", token2 );  
            token2 = strtok_s (NULL, seps, &next_token2);  
        }  
    }  
}  
```  
  
  **标记：**  
 **A**  
 **另一个**  
 **string**  
 **string**  
 **的**  
 **解析**  
 **标记**  
 **at**  
 **和**   
 **节中的连接**  
 **一些**  
 **相同的**  
 **more**  
 **。**  
 **标记**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)