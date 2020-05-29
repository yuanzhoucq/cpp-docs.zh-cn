---
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: 4107ae6cb6366fa8ad80251ce94ee35ca59501bd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910646"
---
# <a name="wcrtomb"></a>wcrtomb

将宽字符转换为多字节字符表示形式。 此函数有一个更安全的版本；请参阅 [wcrtomb_s](wcrtomb-s.md)。

## <a name="syntax"></a>语法

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>参数

*mbchar*<br/>
生成的多字节转换字符。

*wchar*<br/>
要转换的宽字符。

*mbstate*<br/>
指向**mbstate_t**对象的指针。

## <a name="return-value"></a>返回值

返回表示已转换多字节字符所需的字节数，如果发生错误则为 -1。

## <a name="remarks"></a>备注

**Wcrtomb**函数将从*mbstate**中包含*的指定转换状态开始的宽字符转换为*mbchar*所表示的地址。 返回值是表示相应的多字节字符所需的字节数，但不会返回超过**MB_CUR_MAX**个字节。

如果*mbstate*为 null，则使用包含*mbchar*转换状态的内部**mbstate_t**对象。 如果字符序列*wchar*没有对应的多字节字符表示形式，则返回-1，并将**Errno**设置为**eilseq 且**。

**Wcrtomb**函数不同于[wctomb，](wctomb-wctomb-l.md)其可重启性 _wctomb_l。 转换状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用了对**wcsrtombs**的后续调用而不是**wcstombs**，应用程序将使用**wcsrlen**而不是**wcsnlen**。

在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

只要当前线程中的函数都不调用**setlocale** ，而此函数正在执行且*mbstate*为 null， **wcrtomb**函数就是多线程安全的。

## <a name="example"></a>示例

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
