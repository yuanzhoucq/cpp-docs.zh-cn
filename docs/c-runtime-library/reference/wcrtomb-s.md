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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ee25b18bfbb86b34e46c8c6776e8ab83157613e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328171"
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

*p 返回值*<br/>
返回写入的字节数，如果发生错误，则返回 -1。

*姆布查尔*<br/>
生成的多字节转换字符。

*大小Ofmbchar*<br/>
*mbchar*变量的大小（以字节为单位）。

*wchar*<br/>
要转换的宽字符。

*mbstate*<br/>
指向**mbstate_t**对象的指针。

## <a name="return-value"></a>返回值

如果发生错误，则返回零或**errno**值。

## <a name="remarks"></a>备注

**wcrtomb_s**函数将宽字符（从*mbstate*中包含的指定转换状态开始）从*wchar*中包含的值转换为*mbchar*表示的地址。 *pReturnValue*值将是转换的字节数，但如果发生错误，则不超过**MB_CUR_MAX**字节数或 -1。

如果*mbstate*为 null，则使用内部**mbstate_t**转换状态。 如果*wchar*中包含的字符没有相应的多字节字符，*则 pReturnValue*的值将为 -1，并且函数将返回**EILSEQ**的**errno**值 。

**wcrtomb_s**功能不同于[wctomb_s，_wctomb_s_l](wctomb-s-wctomb-s-l.md)它的可重新启动性。 转换状态以*mbstate*存储，用于后续对相同或其他可重新启动函数的调用。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用后续对**wcsrtombs_s**的调用而不是**wcstombs_s**，则应用程序将使用**wcsrlen**而不是**wcslen。**

在 C++ 中，模板重载简化了此函数的使用；重载可以自动推导出缓冲区长度（不再需要指定大小自变量），并且它们可以自动用更新、更安全的对应物替换不安全的旧函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

只要当前线程调用中没有函数在执行任务时**设置局部性**，*并且 mbstate*为空 **，wcrtomb_s**函数是多线程安全的。

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
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
