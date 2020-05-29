---
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: cad31f28c5542a96eae9f144344882b71806052a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910618"
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

*计数*<br/>
要转换的字符数。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。

## <a name="return-value"></a>返回值

返回已成功转换的字节数，不包括 null 终止 null 字节（如果有），发生错误时则为 -1。

## <a name="remarks"></a>备注

**Wcsrtombs**函数将从*mbstate*中包含的指定转换状态（从*wcstr*中的间接指向的值）转换为*mbstr*的地址。 在以下情况下，转换将继续对每个字符进行：在遇到 null 终止宽字符之后、遇到非相应字符时或者当下一个字符超出*计数*中包含的限制时。 如果**wcsrtombs**在*count 或 count*发生前后遇到宽字符 null 字符（L ' \ 0 '），则它会将其转换为8位0并停止。

因此，仅当**wcsrtombs**在转换期间遇到宽字符 null 字符时， *mbstr*处的多字节字符串才以 null 结尾。 如果由*wcstr*和*mbstr*指向的序列重叠，则**wcsrtombs**的行为不确定。 **wcsrtombs**受当前区域设置的 LC_TYPE 类别的影响。

**Wcsrtombs**函数不同于[wcstombs，](wcstombs-wcstombs-l.md)其可重启性 _wcstombs_l。 转换状态存储在*mbstate*中，以便后续调用相同的或其他可重启的函数。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用了对**wcsrtombs**的后续调用而不是**wcstombs**，应用程序将使用**wcsrlen**而不是**wcsnlen**。

如果*mbstr*参数为**NULL**，则**wcsrtombs**返回目标字符串所需的大小（以字节为单位）。 如果*mbstate*为 null，则使用内部**mbstate_t**转换状态。 如果字符序列*wchar*没有对应的多字节字符表示形式，则返回-1，并将**Errno**设置为**eilseq 且**。

在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

只要当前线程中的函数都不调用**setlocale** ，而此函数正在执行且*mbstate*不为 null 时， **wcsrtombs**函数就是多线程安全的。

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

|例程|必需的标头|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
