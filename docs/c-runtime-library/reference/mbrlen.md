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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 7503de22a8310335ddd678335916d3e74dab6e70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340994"
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

*Str*<br/>
指向多字节字符字符串中要检查的下一字节的指针。

*count*<br/>
要检查的最大字节数。

*mbstate*<br/>
指向 str 的初始字节的当前移位状态的*指针*。

## <a name="return-value"></a>返回值

以下值之一：

|||
|-|-|
0|下一*个计数*或更少字节完成表示宽空字符的多字节字符。
1*计数*， 包括|下一*个计数*或更少字节完成有效的多字节字符。 返回的值是填充多字节字符的字节数。
(size_t)(-2)|下一个*计数*字节有助于不完整但可能有效的多字节字符，并且所有*计数*字节都已处理。
(size_t)(-1)|发生编码错误。 下一个*计数*或更少的字节不会贡献为完整且有效的多字节字符。 在这种情况下 **，errno**设置为 EILSEQ，并且未指定*mbstate*中的转换状态。

## <a name="remarks"></a>备注

**mbrlen**函数最多检查*计数*字节，以*str*指向的字节开头，以确定完成下一个多字节字符（包括任何移位序列）所需的字节数。 它等效于`mbrtowc(NULL, str, count, &mbstate)`*mbstate*是用户提供的**mbstate_t**对象的调用，或者库提供的静态内部对象。

**mbrlen**函数保存并使用*mbstate*参数中不完整的多字节字符的移位状态。 这使**mbrlen**能够在需要时在多字节字符中间重新启动，检查最多*计数*字节。 如果*mbstate*是空指针，**则 mbrlen**使用内部静态**mbstate_t**对象来存储移位状态。 由于内部**mbstate_t**对象不是线程安全的，因此我们建议您始终分配并传递自己的*mbstate*参数。

**mbrlen**函数不同于[_mbclen，mblen，_mblen_l](mbclen-mblen-mblen-l.md)它的可重新启动性。 移位状态以*mbstate*存储，以便随后调用相同或其他可重新启动函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用后续对**wcsrtombs**的调用而不是**wcstombs，** 则应用程序应使用**wcsrlen**而不是**wcslen。**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

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

此示例演示如何对多字节字符的解释依赖于当前代码页，并演示**了 mbrlen**的恢复功能。

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
[现场](../../c-runtime-library/locale.md)<br/>
