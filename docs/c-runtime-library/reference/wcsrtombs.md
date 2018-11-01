---
title: wcsrtombs
ms.date: 11/04/2016
apiname:
- wcsrtombs
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: 46ef195ec4685c327c4b5951ec44e5c363214b59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494414"
---
# <a name="wcsrtombs"></a>wcsrtombs

将宽字符字符串转换为多字节字符串表示形式。 此函数有一个更安全的版本；请参阅 [wcsrtombs_s](wcsrtombs-s.md)。

## <a name="syntax"></a>语法

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>参数

*mbstr*<br/>
生成的已转换多字节字符字符串的地址位置。

*wcstr*<br/>
间接指向要转换的宽字符字符串的位置。

*count*<br/>
要转换的字符数。

*mbstate*<br/>
一个指向**mbstate_t**转换状态对象。

## <a name="return-value"></a>返回值

返回已成功转换的字节数，不包括 null 终止 null 字节（如果有），发生错误时则为 -1。

## <a name="remarks"></a>备注

**Wcsrtombs**函数将转换的宽字符，包含在指定的转换状态开始字符串*mbstate*，从中指向的值间接*wcstr*，地址中的*mbstr*。 该转换将一直对每个字符之前： 时遇到非相应字符遇到 null 终止宽字符后或在下一个字符将超过中的限制时*计数*。 如果**wcsrtombs**遇到宽字符 null 字符 (L '\0) 之前或当*计数*发生时，会将其转换为 8 位 0 并停止。

因此，在多字节字符字符串*mbstr*是 null 终止的仅当**wcsrtombs**在转换期间遇到宽字符 null 字符。 如果指向的序列*wcstr*并*mbstr*重叠的行为**wcsrtombs**是不确定的。 **wcsrtombs**受当前区域设置中 LC_TYPE 类别。

**Wcsrtombs**函数不同于[wcstombs、 _wcstombs_l](wcstombs-wcstombs-l.md)通过其可重启性。 转换状态存储在*mbstate*以便后续调用相同或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，使用应用程序**wcsrlen**而非**wcsnlen**，则随后调用**wcsrtombs**而不是使用了**wcstombs**.

如果*mbstr*自变量是**NULL**， **wcsrtombs**返回以字节为单位的目标字符串所需的大小。 如果*mbstate*为 null，内部**mbstate_t**使用转换状态。 如果字符序列*wchar*不具有相应的多字节字符表示形式，则返回-1 并**errno**设置为**EILSEQ**。

在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>异常

**Wcsrtombs**函数是多线程安全，只要当前线程中的函数不调用**setlocale**执行此函数时， *mbstate*不为 null。

## <a name="example"></a>示例

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
