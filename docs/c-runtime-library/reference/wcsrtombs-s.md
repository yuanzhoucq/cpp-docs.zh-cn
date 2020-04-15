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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 71a2206df9d3afb64fcaf62848988cf116d9071f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328106"
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

*p 返回值*<br/>
转换的字符串（包括空终止符）的大小（以字节为单位）。

*姆布斯特*<br/>
生成的已转换多字节字符字符串的缓冲区的地址。

*大小字节*<br/>
*mbstr*缓冲区的大小（以字节为单位）。

*wc斯特*<br/>
指向要转换的宽字符字符串的指针。

*count*<br/>
要存储在*mbstr*缓冲区或[_TRUNCATE](../../c-runtime-library/truncate.md)的最大字节数。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

|添加状态|返回值和**差错**|
|---------------------|------------------------------|
|*mbstr*为**NULL，***大小为*> 0|**埃因瓦尔**|
|*wcstr*为**NULL**|**埃因瓦尔**|
|目标缓冲区太小，无法包含转换后的字符串（除非*计数***_TRUNCATE;** 请参阅下面的备注）|**ERANGE**|

如果发生这些情况中的任何一个，都会调用无效参数异常，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将返回错误代码并设置表中指示的**errno。**

## <a name="remarks"></a>备注

**wcsrtombs_s**函数将*wcstr*指向的宽字符字符串转换为存储在*mbstr*指向的缓冲区中的多字节字符，使用*mbstate*中包含的转换状态。 在满足以下条件之一前，该转换将一直对每个字符执行：

- 遇到 null 宽字符

- 遇到无法转换的宽字符

- 存储在*mbstr*缓冲区中的字节数等于*计数*。

目标字符串始终以 null 结尾（即使在出错时）。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值，则**wcsrtombs_s**转换与目标缓冲区中一样多的字符串，同时仍为空终止符留出空间。

如果**wcsrtombs_s**成功转换源字符串，它将转换后的字符串（包括空终止符）的大小放入 *&#42;pReturnValue（* 前提是*pReturnValue*不是**NULL）。** 即使*mbstr*参数为**NULL，** 并提供一种确定所需缓冲区大小的方法，也会发生这种情况。 请注意，如果*mbstr*为**NULL，** 则忽略*计数*。

如果**wcsrtombs_s**遇到一个宽字符，它不能转换为多字节字符，它会在*\*pReturnValue*中放置 -1，将目标缓冲区设置为空字符串，将**errno**设置到**EILSEQ，** 并返回**EILSEQ**。

如果*wcstr*和*mbstr*指向的序列重叠，则**wcsrtombs_s**的行为未定义。 **wcsrtombs_s**受当前区域设置的LC_TYPE类别的影响。

> [!IMPORTANT]
> 确保*wcstr*和*mbstr*不重叠，并且*该计数*正确反映要转换的宽字符数。

**wcsrtombs_s**函数不同于[wcstombs_s，_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)其可重新启动性。 转换状态以*mbstate*存储，用于后续对相同或其他可重新启动函数的调用。 混合使用可重启函数和不可重启函数时，结果不确定。 例如，如果使用后续对**wcsrtombs_s**的调用而不是**wcstombs_s**，则应用程序将使用**wcsrlen**而不是**wcslen。**

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

只要执行此函数时当前线程调用中没有函数**设置局部性**，*并且 mbstate*为空 **，wcsrtombs_s**函数是多线程安全的。

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
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
