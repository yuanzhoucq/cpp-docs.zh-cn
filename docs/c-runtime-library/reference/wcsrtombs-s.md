---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: c804d232dbcce67b8d467eaa37ccf2b15282881a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910600"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

将宽字符字符串转换为多字节字符串表示形式。 [wcsrtombs](wcsrtombs.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>参数

*pReturnValue*<br/>
转换后的字符串（包括 null 终止符）的大小（以字节为单位）。

*mbstr*<br/>
生成的已转换多字节字符字符串的缓冲区的地址。

*sizeInBytes*<br/>
*Mbstr*缓冲区的大小（以字节为单位）。

*wcstr*<br/>
指向要转换的宽字符字符串的指针。

*计数*<br/>
要存储在*mbstr*缓冲区中的最大字节数，或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

|添加状态|返回值和**errno**|
|---------------------|------------------------------|
|*mbstr*为**NULL** ， *sizeInBytes* > 0|**EINVAL**|
|*wcstr*为**NULL**|**EINVAL**|
|目标缓冲区太小，无法包含转换后的字符串（除非 **_TRUNCATE**了*count* ; 请参阅下面的备注）|**ERANGE**|

如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将返回错误代码并按表中所示设置**errno** 。

## <a name="remarks"></a>备注

**Wcsrtombs_s**函数使用*mbstate*中包含的转换状态，将*wcstr*指向的宽字符字符串转换为存储在由*mbstr*指向的缓冲区中的多字节字符。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到 null 宽字符

- 遇到无法转换的宽字符

- *Mbstr*缓冲区中存储的字节数等于*计数*。

目标字符串始终以 null 结尾（即使在出错时）。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值，则**wcsrtombs_s**会将尽可能多的字符串转换为目标缓冲区的大小，同时仍然为 null 终止符留下空间。

如果**wcsrtombs_s**成功转换源字符串，则会将转换后的字符串的大小（以字节为单位）放入 *&#42;pReturnValue* （提供的*pReturnValue*不为**null**）。 即使*mbstr*参数为**NULL** ，并且提供了一种方法来确定所需的缓冲区大小，也会发生这种情况。 请注意，如果*mbstr*为**NULL**，则忽略*count* 。

如果**wcsrtombs_s**遇到不能转换为多字节字符的宽字符，则它将* \*pReturnValue*中的-1，将目标缓冲区设置为空字符串，**将 errno**设置为**eilseq 且**，并返回**eilseq 且**。

如果由*wcstr*和*mbstr*指向的序列重叠，则**wcsrtombs_s**的行为是不确定的。 **wcsrtombs_s**受当前区域设置的 LC_TYPE 类别的影响。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*不重叠，并且该*计数*正确反映了要转换的宽字符数。

**Wcsrtombs_s**函数不同于可重启性[_wcstombs_s_l wcstombs_s](wcstombs-s-wcstombs-s-l.md) 。 转换状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用了对**wcsrtombs_s**的后续调用而不是**wcstombs_s**，应用程序将使用**wcsrlen**而不是**wcslen**。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

只要当前线程中的任何函数在执行此函数时都不会调用**setlocale** ，并且*mbstate*为 null， **wcsrtombs_s**函数就是多线程安全的。

## <a name="example"></a>示例

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

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
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
