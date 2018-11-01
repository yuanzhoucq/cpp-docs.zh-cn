---
title: wcrtomb_s
ms.date: 11/04/2016
apiname:
- wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 7fe7fba861eecec562928cf381973f62a4db60fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522455"
---
# <a name="wcrtombs"></a>wcrtomb_s

将宽字符转换为多字节字符表示形式。 [wcrtomb](wcrtomb.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>参数

*pReturnValue*<br/>
返回写入的字节数，如果发生错误，则返回 -1。

*mbchar*<br/>
生成的多字节转换字符。

*sizeOfmbchar*<br/>
大小*mbchar*变量以字节为单位。

*wchar*<br/>
要转换的宽字符。

*mbstate*<br/>
一个指向**mbstate_t**对象。

## <a name="return-value"></a>返回值

返回零或**errno**如果发生错误，则值。

## <a name="remarks"></a>备注

**Wcrtomb_s**函数将转换的宽字符，包含在指定的转换状态开始*mbstate*，从中包含的值*wchar*，到地址由*mbchar*。 *PReturnValue*值将数个字节转换，但不会超过**MB_CUR_MAX**字节，则为-1 如果出现错误。

如果*mbstate*为 null，内部**mbstate_t**使用转换状态。 如果包含的字符*wchar*不具有相应的多字节字符的值*pReturnValue*将为-1，则函数将返回**errno**值**EILSEQ**。

**Wcrtomb_s**函数不同于[wctomb_s、 _wctomb_s_l](wctomb-s-wctomb-s-l.md)通过其可重启性。 转换状态存储在*mbstate*以便后续调用相同或其他可重启函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，使用应用程序**wcsrlen**而非**wcslen**，则随后调用**wcsrtombs_s**而不是使用了**wcstombs_s**.

在 C++ 中，模板重载简化了此函数的使用；重载可以自动推导出缓冲区长度（不再需要指定大小自变量），并且它们可以自动用更新、更安全的对应物替换不安全的旧函数。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="exceptions"></a>异常

**Wcrtomb_s**函数是多线程安全，只要当前线程中的函数不调用**setlocale**执行此函数时， *mbstate*为 null。

## <a name="example"></a>示例

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
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
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
