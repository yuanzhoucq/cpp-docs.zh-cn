---
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: dd903aaf8b1c5772f2caaf58bda5d6c23bb59687
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920304"
---
# <a name="mbrlen"></a>mbrlen

确定填充当前区域设置中多字节字符所需的字节数，其中重启功能位于多字节字符的中间。

## <a name="syntax"></a>语法

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>参数

*字符串*<br/>
指向多字节字符字符串中要检查的下一字节的指针。

*计数*<br/>
要检查的最大字节数。

*mbstate*<br/>
指向*str*的第一个字节的当前移位状态的指针。

## <a name="return-value"></a>返回值

以下值之一：

|||
|-|-|
0|接下来的*计数*或更少的字节将填充代表宽 null 字符的多字节字符。
1到*计数*（含）|接下来的*计数*或更少的字节将完成有效的多字节字符。 返回的值是填充多字节字符的字节数。
(size_t)(-2)|下一个*计数*字节导致了不完整但可能有效的多字节字符，并且已处理所有*计数*字节。
(size_t)(-1)|发生编码错误。 下一个*计数*或更少的字节不涉及完整且有效的多字节字符。 在这种情况下， **errno**设置为 eilseq 且，而*mbstate*中的转换状态为未指定。

## <a name="remarks"></a>备注

**Mbrlen**函数最多检查以*str*指向的字节开头的最多*计数*字节，以确定完成下一个多字节字符（包括任何移位序列）所需的字节数。 它等效于调用`mbrtowc(NULL, str, count, &mbstate)` ，其中*mbstate*是用户提供的**mbstate_t**对象或由库提供的静态内部对象。

**Mbrlen**函数在*mbstate*参数中保存并使用不完整多字节字符的移位状态。 这样， **mbrlen**将在多字节字符中间重启的功能（如果需要），并检查最多的*计数*字节。 如果*mbstate*为 null 指针，则**mbrlen**将使用内部静态**mbstate_t**对象存储移位状态。 由于内部**mbstate_t**对象不是线程安全的，因此建议始终分配和传递自己的*mbstate*参数。

**Mbrlen**函数的可重启性不同于[_mbclen、mblen _mblen_l](mbclen-mblen-mblen-l.md) 。 移位状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用对**wcsrtombs**的后续调用而不是**wcstombs**，应用程序应使用**wcsrlen**而不是**wcslen** 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|不适用|不适用|**mbrlen**|不适用|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此示例演示多字节字符的解释如何取决于当前代码页，并演示了**mbrlen**的恢复功能。

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
