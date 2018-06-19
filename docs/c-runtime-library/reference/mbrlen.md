---
title: mbrlen | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrlen
dev_langs:
- C++
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77e5cb106a971bcaf02662bfd8459267a134173a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404436"
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

*str*<br/>
指向多字节字符字符串中要检查的下一字节的指针。

*count*<br/>
要检查的最大字节数。

*mbstate*<br/>
指向的初始字节当前移位状态*str*。

## <a name="return-value"></a>返回值

以下值之一：

|||
|-|-|
0|下一步*计数*或更少字节将填充代表宽 null 字符的多字节字符。
1 到*计数*(含） 之间|下一步*计数*或更少的字节填充有效多字节字符。 返回的值是填充多字节字符的字节数。
(size_t)(-2)|下一步*计数*字节数有利于实现不完整但可能有效的多字节字符和所有*计数*已处理的字节数。
(size_t)(-1)|发生编码错误。 下一步*计数*或更少字节数不有利于实现完整且有效的多字节字符。 在这种情况下， **errno**设置为 EILSEQ 且中的转换状态*mbstate*未指定。

## <a name="remarks"></a>备注

**Mbrlen**函数最多检查*计数*字节的字节开头的指向*str*来确定完成下一步所需的字节数多字节字符，包括任何位移序列。 它等效于调用`mbrtowc(NULL, str, count, &mbstate)`其中*mbstate*是任一用户提供**mbstate_t**对象或库提供的静态内部对象。

**Mbrlen**函数将保存并使用中的不完整多字节字符的位移状态*mbstate*参数。 这使**mbrlen**如果位于多字节字符的中间重启功能需要最多检查*计数*字节。 如果*mbstate*是 null 指针， **mbrlen**使用内部静态**mbstate_t**对象来存储位移状态。 因为内部**mbstate_t**对象不是线程安全，我们建议你始终分配并传递你自己*mbstate*参数。

**Mbrlen**函数不同于[_mbclen、 mblen、 _mblen_l](mbclen-mblen-mblen-l.md)通过其可重启性。 位移状态存储在*mbstate*以便后续调用相同的或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，应用程序应使用**wcsrlen**而不是**wcslen**如果的后续调用**wcsrtombs**而不是使用**wcstombs**.

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|不适用|不适用|**mbrlen**|不适用|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此示例演示如何多字节字符的解释取决于当前代码页，并演示的恢复功能**mbrlen**。

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

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
