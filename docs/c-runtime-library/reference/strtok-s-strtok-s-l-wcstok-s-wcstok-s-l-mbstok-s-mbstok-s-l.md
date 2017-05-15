---
title: "strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
dev_langs:
- C++
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 4313f785ba5197c3659e74384b7d6ecda8e8c7be
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
通过使用当前区域设置或传入的区域设置，查找字符串中的下一个标记。 这些版本的 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](../../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbstok_s` 和 `_mbstok_s_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 `strToken`  
 包含一个或多个标记的字符串。  
  
 `strDelimit`  
 分隔符字符组。  
  
 `context`  
 用于存储调用 `strtok_s` 之间的位置信息  
  
 `locale`  
 要使用的区域设置。  
  
## <a name="return-value"></a>返回值  
 返回 `strToken` 中找到的指向下一个标记的指针。 它们在未找到更多标记时返回 `NULL`。 每次调用都会修改 `strToken`，方法是通过在标记返回后，为出现的第一个分隔符替换 `NULL` 字符。  
  
### <a name="error-conditions"></a>错误条件  
  
|`strToken`|`strDelimit`|`context`|返回值|`errno`|  
|----------------|------------------|---------------|------------------|-------------|  
|`NULL`|任何|指向空指针的指针|`NULL`|`EINVAL`|  
|任何|`NULL`|任何|`NULL`|`EINVAL`|  
|任何|任何|`NULL`|`NULL`|`EINVAL`|  
  
 如果 `strToken` 为 `NULL`，但上下文是指向有效上下文指针的指针，则不会有任何错误。  
  
## <a name="remarks"></a>备注  
 `strtok_s` 函数查找 `strToken` 中的下一个标记。 `strDelimit` 中的字符组指定在当前调用上的 `strToken` 中找到的可能的标记分隔符。 `wcstok_s` 和 `_mbstok_s` 分别是 `strtok_s` 的宽字符及多字节字符版本。 `wcstok_s` 和 `_wcstok_s_l` 的参数和返回值是宽字符字符串；而 `_mbstok_s` 和 `_mbstok_s_l` 是多字节字符字符串。 否则这三个函数否则具有相同行为。  
  
 此函数验证其参数。 如果出现错误条件表中的错误条件，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `NULL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstok_s`|`strtok_s`|`_mbstok_s`|`wcstok_s`|  
|`_tcstok_s_l`|`_strtok_s_l`|`_mbstok_s_l`|`_wcstok_s_l`|  
  
 首次调用 `strtok_s` 时，函数跳过前导分隔符并返回指向 `strToken` 中的第一个标记的指针，终止空字符的标记。 通过对 `strtok_s` 的一系列调用，可以从 `strToken` 的其余部分中分离出更多标记。 每次调用 `strtok_s` 都会修改 `strToken`，方法是在通过调用返回标记后插入空字符。 `context` 指针跟踪要读取的字符串以及在字符串中读取下一个标记的位置。 若要读取来自 `strToken` 的下一个标记，请使用 `strToken` 实参的 `NULL` 值调用 `strtok_s`并传递同一 `context` 形参。 `NULL``strToken` 参数使 `strtok_s` 在修改的 `strToken` 中搜索下一个标记。 `strDelimit` 实参可以采用从第一个调用到下一个调用的任何值，以使分隔符集有所不同。  
  
 由于 `context` 形参取代了 `strtok` 和 `_strtok_l` 中使用的静态缓冲区，因此，可以在同一线程中同时分析两个字符串。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅[区域设置](../../c-runtime-library/locale.md)。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`strtok_s`|\<string.h>|  
|`_strtok_s_l`|\<string.h>|  
|`wcstok_s`,<br /><br /> `_wcstok_s_l`|\<string.h> 或 \<wchar.h>|  
|`_mbstok_s`,<br /><br /> `_mbstok_s_l`|\<mbstring.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Tokens:  
 A  
        Another  
 string  
        string  
 of  
        parsed  
 tokens  
        at  
 and  
        the  
 some  
        same  
 more  
        time.  
 tokens  
```  
  
## <a name="see-also"></a>另请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、_mbscspn、_mbscspn_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strspn、wcsspn、_mbsspn、_mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)
