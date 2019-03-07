---
title: strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
ms.date: 11/04/2016
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
- ntoskrnl.exe
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
ms.openlocfilehash: 24a945742f3db82e41f662a337eef1f79ef13bd6
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210583"
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l

通过使用当前区域设置或传入的区域设置，查找字符串中的下一个标记。 这些版本的 [strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> **_mbstok_s**并 **_mbstok_s_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*str*<br/>
包含或多个令牌，若要查找的字符串。

*delimiters*<br/>
要使用的分隔符字符组。

*context*<br/>
用于存储对函数的调用之间的位置信息。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回一个指向下一个令牌中找到*str*。 返回**NULL**找到没有更多标记时。 每个调用都会修改*str* ，只需替换 null 字符在返回的令牌后发生的第一个分隔符。

### <a name="error-conditions"></a>错误条件

|*str*|*delimiters*|*context*|返回值|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**NULL**|任何|指向空指针的指针|**NULL**|**EINVAL**|
|任何|**NULL**|任何|**NULL**|**EINVAL**|
|任何|任何|**NULL**|**NULL**|**EINVAL**|

如果*str*是**NULL**但*上下文*的指针到有效的上下文指针时，没有错误。

## <a name="remarks"></a>备注

**Strtok_s**系列函数查找中的下一步标记*str*。 中的字符组*分隔符*指定的令牌中找到可能的分隔符*str*在当前调用上。 **wcstok_s**并 **_mbstok_s**宽字符及多字节字符版本的**strtok_s**。 参数和返回值**wcstok_s**并 **_wcstok_s_l**是宽字符字符串; **_mbstok_s**和 **_mbstok_s_l**都是多字节字符字符串。 否则这些函数具有相同行为。

此函数验证其参数。 如果出现错误条件表中的错误条件，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将设置**errno**到**EINVAL**并返回**NULL**。

在首次调用**strtok_s**函数跳过前导分隔符并返回一个指针中的第一个标记*str*，终止空字符的标记。 更多标记可以分离出的余数*str*的调用的一系列**strtok_s**。 每次调用**strtok_s**修改*str*的方法是通过调用返回标记后插入空字符。 *上下文*所读取的字符串，其中在字符串中的下一个标记是要读取跟踪的指针。 若要读取的下一个令牌*str*，调用**strtok_s**与**NULL**值*str*参数，并传递同一*上下文*参数。 **NULL** *str*参数可以使**strtok_s**搜索中的修改后的下一个标记*str*。 *分隔符*参数可使用从到下一次调用的任何值，以使分隔符集可能会有所不同。

由于*上下文*形参取代了使用中的静态缓冲区**strtok**并 **_strtok_l**，可以分析同时在同一线程中的两个字符串。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 无需这些函数的版本 **_l**后缀的区域设置相关的行为使用当前线程区域设置。 与版本 **_l**后缀完全相同，只不过它们改用*区域设置*参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> 或 \<wchar.h>|
|**_mbstok_s**，<br />**_mbstok_s_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|\_UNICODE & \_MBCS 未定义|\_MBCS 定义|已定义 _UNICODE|
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

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
