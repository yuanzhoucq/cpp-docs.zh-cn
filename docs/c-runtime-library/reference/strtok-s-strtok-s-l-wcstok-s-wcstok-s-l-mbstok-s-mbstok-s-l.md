---
title: strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
api_location:
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
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
ms.openlocfilehash: 52c998f14fee080efc1d288abbba012752757632
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912670"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l

通过使用当前区域设置或传入的区域设置，查找字符串中的下一个标记。 这些版本的 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> 不能在 Windows 运行时中执行的应用程序中使用 **_mbstok_s**和 **_mbstok_s_l** 。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
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

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*字符串*<br/>
一个包含要查找的标记的字符串。

*限定符*<br/>
要使用的分隔符字符集。

*上下文*<br/>
用于在对函数的调用之间存储位置信息。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回指向*str*中找到的下一个标记的指针。 当找不到更多的标记时，返回**NULL** 。 每个调用都通过将 null 字符替换为在返回的标记后出现的第一个分隔符来修改*str* 。

### <a name="error-conditions"></a>错误条件

|*字符串*|*限定符*|*上下文*|返回值|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**Null**|any|指向空指针的指针|**Null**|**EINVAL**|
|any|**Null**|any|**Null**|**EINVAL**|
|any|any|**Null**|**Null**|**EINVAL**|

如果*str*为**NULL** ，但*上下文*是指向有效上下文指针的指针，则没有任何错误。

## <a name="remarks"></a>备注

**Strtok_s**系列函数查找*str*中的下一个标记。 *分隔符*中的字符集指定要在当前调用的*str*中找到的标记的可能分隔符。 **wcstok_s**和 **_mbstok_s**是**strtok_s**的宽字符和多字节字符版本。 **Wcstok_s**和 **_wcstok_s_l**的参数和返回值都是宽字符字符串;**_mbstok_s**和 **_mbstok_s_l**的是多字节字符字符串。 否则这些函数具有相同行为。

此函数验证其参数。 出现错误条件时（如错误条件表中所述），将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL** ，并返回**NULL**。

在对**strtok_s**的第一次调用时，函数跳过前导分隔符并返回指向*str*中第一个标记的指针，并以 null 字符终止标记。 通过一系列对**strtok_s**的调用，可以将更多标记分解出*str*的其余部分。 **Strtok_s**对的每个调用通过在该调用返回的标记后插入一个空字符来修改*str* 。 *上下文*指针跟踪正在读取的字符串，以及在字符串中要读取下一个标记的位置。 若要读取*str*中的下一个标记，请使用*Str*参数的**NULL**值调用**strtok_s** ，并传递相同的*上下文*参数。 **NULL** *str*参数会导致**strtok_s**搜索修改后的*str*中的下一个标记。 *分隔符*参数可以从一个调用到下一个调用，以使分隔符集不同。

由于*上下文*参数取代了**strtok**和 **_strtok_l**中使用的静态缓冲区，因此可以同时在同一线程中分析两个字符串。

输出值受区域设置的**LC_CTYPE**类别设置的设置影响。 有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。

这些不带 **_l**后缀的函数的版本对与区域设置相关的行为使用当前线程区域设置。 带有 **_l**后缀的版本是相同的，只不过它们改为使用*locale*参数指定的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**，<br />**_wcstok_s_l**|\<string.h> 或 \<wchar.h>|
|**_mbstok_s**，<br />**_mbstok_s_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|\_未定义\_UNICODE & MBCS|\_定义 MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

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

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
