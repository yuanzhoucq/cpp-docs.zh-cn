---
title: "strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 868d9d3fc206931b20858ee360c2380cc5f03d61
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l

通过使用当前区域设置或传入的区域设置，查找字符串中的下一个标记。 这些版本的 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](../../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbstok_s` 和 `_mbstok_s_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。  
  
## <a name="syntax"></a>语法  
  
```
char* strtok_s(  
   char* str,  
   const char* delimiters,  
   char** context  
);

char* _strtok_s_l(  
   char* str,  
   const char* delimiters,  
   char** context,  
   _locale_t locale  
);  

wchar_t* wcstok_s(  
   wchar_t* str,  
   const wchar_t* delimiters,   
   wchar_t** context  
); 
 
wchar_t *_wcstok_s_l(  
   wchar_t* str,  
   const wchar_t* delimiters,   
   wchar_t** context,  
   _locale_t locale  
);  

unsigned char* _mbstok_s(  
   unsigned char* str,  
   const unsigned char* delimiters,   
   char** context  
);  

unsigned char* _mbstok_s(  
   unsigned char* str,  
   const unsigned char* delimiters,   
   char** context,  
   _locale_t locale  
);  
```  
  
### <a name="parameters"></a>参数  

*str*  
包含或多个令牌若要查找的字符串。  
  
*分隔符*  
若要使用的分隔符集。  
  
*context*  
用于存储对函数的调用之间的位置信息。  
  
*locale*  
要使用的区域设置。  
  
## <a name="return-value"></a>返回值  

将指针返回到下一步中找到的令牌*str*。 返回`NULL`当找到没有更多的令牌时。 每个调用修改*str* ，只需替换`NULL`字符在返回的令牌之后第一个分隔符。  
  
### <a name="error-conditions"></a>错误条件  
  
|*str*|*分隔符*|*context*|返回值|`errno`|  
|----------------|------------------|---------------|------------------|-------------|  
|`NULL`|任何|指向空指针的指针|`NULL`|`EINVAL`|  
|任何|`NULL`|任何|`NULL`|`EINVAL`|  
|任何|任何|`NULL`|`NULL`|`EINVAL`|  
  
如果*str*是`NULL`但*上下文*是一个指针，到有效的上下文指针时，没有错误。  
  
## <a name="remarks"></a>备注  

`strtok_s`系列函数查找中的下一个标记*str*。 中的字符组*分隔符*指定可能要在中找到的标记分隔符*str*上当前的调用。 `wcstok_s` 和 `_mbstok_s` 分别是 `strtok_s` 的宽字符及多字节字符版本。 `wcstok_s` 和 `_wcstok_s_l` 的参数和返回值是宽字符字符串；而 `_mbstok_s` 和 `_mbstok_s_l` 是多字节字符字符串。 否则这些函数具有相同行为。  

此函数验证其参数。 如果出现错误条件表中的错误条件，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `NULL`。

在第一个调用`strtok_s`函数跳过前导分隔符，并将指针返回到中的第一个标记*str*，终止 null 字符的标记。 多个令牌的更改会损坏外的其余部分*str*对的调用一系列`strtok_s`。 每次调用`strtok_s`修改*str*的方法是在该调用返回的标记后插入 null 字符。 *上下文*正在读取的字符串和其中字符串中的下一个标记是要读取跟踪的指针。 若要读取下一个令牌以从*str*，调用`strtok_s`与`NULL`值*str*自变量，并将传递相同*上下文*参数。 `NULL` *Str*参数可以使`strtok_s`搜索中修改后的下一个标记*str*。 *分隔符*自变量可以采用到下一次调用之间的任何值，以便分隔符集可能会有所不同。

由于*上下文*参数将取代中使用的静态缓冲区`strtok`和`_strtok_l`，可以分析同时在同一线程中的两个字符串。

输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。 版本的这些功能，而不必`_l`后缀区域设置相关的行为使用当前线程区域设置。 版本与`_l`后缀是相同，只不过它们改用*区域设置*参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|`strtok_s`|\<string.h>|
|`_strtok_s_l`|\<string.h>|
|`wcstok_s`,<br />`_wcstok_s_l`|\<string.h> 或 \<wchar.h>|
|`_mbstok_s`,<br />`_mbstok_s_l`|\<mbstring.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|\_UNICODE （& a) \_MBCS 未定义|\_MBCS 定义|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcstok_s`|`strtok_s`|`_mbstok_s`|`wcstok_s`|
|`_tcstok_s_l`|`_strtok_s_l`|`_mbstok_s_l`|`_wcstok_s_l`|

## <a name="example"></a>示例

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

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

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
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
  
## <a name="see-also"></a>请参阅  

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)  
[区域设置](../../c-runtime-library/locale.md)  
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)  
[strcspn、wcscspn、_mbscspn、_mbscspn_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)  
[strspn、wcsspn、_mbsspn、_mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)