---
title: wcrtomb_s
ms.date: 4/2/2020
api_name:
- wcrtomb_s
- _o_wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 51985b008565cbe550065b85261b8beb53ed6f89
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915963"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

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
*Mbchar*变量的大小（以字节为单位）。

*wchar*<br/>
要转换的宽字符。

*mbstate*<br/>
指向**mbstate_t**对象的指针。

## <a name="return-value"></a>返回值

如果发生错误，则返回零或**errno**值。

## <a name="remarks"></a>备注

**Wcrtomb_s**函数将从*mbstate*中包含的指定转换状态开始，从*wchar*中包含的值转换为*mbchar*表示的地址中的宽字符。 *PReturnValue*值将是已转换的字节数，但不能超过**MB_CUR_MAX**字节，如果出现错误，则为-1。

如果*mbstate*为 null，则使用内部**mbstate_t**转换状态。 如果*wchar*中包含的字符没有对应的多字节字符，则*pReturnValue*的值将为-1，并且函数将返回**eilseq 且**的**errno**值。

**Wcrtomb_s**函数不同于可重启性[_wctomb_s_l wctomb_s](wctomb-s-wctomb-s-l.md) 。 转换状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用了对**wcsrtombs_s**的后续调用而不是**wcstombs_s**，应用程序将使用**wcsrlen**而不是**wcslen**。

在 C++ 中，模板重载简化了此函数的使用；重载可以自动推导出缓冲区长度（不再需要指定大小自变量），并且它们可以自动用更新、更安全的对应物替换不安全的旧函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

只要当前线程中的任何函数在执行此函数时都不会调用**setlocale** ，并且*mbstate*为 null， **wcrtomb_s**函数就是多线程安全的。

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

|例程|必需的标头|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
