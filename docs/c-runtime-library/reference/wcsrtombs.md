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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: af22a7d55c5f4958db6962e98f212fb5bb89e61e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328061"
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

*姆布斯特*<br/>
生成的已转换多字节字符字符串的地址位置。

*wc斯特*<br/>
间接指向要转换的宽字符字符串的位置。

*count*<br/>
要转换的字符数。

*mbstate*<br/>
指向**mbstate_t**转换状态对象的指针。

## <a name="return-value"></a>返回值

返回已成功转换的字节数，不包括 null 终止 null 字节（如果有），发生错误时则为 -1。

## <a name="remarks"></a>备注

**wcsrtombs**函数将一串宽字符（从*mbstate*中包含的指定转换状态开始）从间接指向*wcstr*的值转换为*mbstr*的地址。 每个字符的转换将继续，直到：遇到空终止宽字符后，遇到非对应字符或下一个字符将超过*计数*中包含的限制。 如果**wcsrtombs**在*计数*发生之前或发生计数时遇到宽字符 null 字符 （L'_0'），它将转换为 8 位 0 并停止。

因此 *，mbstr*处的多字节字符串仅在**wcsrtombs**在转换期间遇到宽字符 null 字符时才为 null 终止。 如果*wcstr*和*mbstr*指向的序列重叠，则**wcsrtombs**的行为未定义。 **wcsrtombs**受当前区域设置LC_TYPE类别的影响。

**wcsrtombs**函数不同于[wcstombs，_wcstombs_l](wcstombs-wcstombs-l.md)它的可重新启动性。 转换状态以*mbstate*存储，用于后续对相同或其他可重新启动函数的调用。 混合使用可重启函数和不可重启函数时，结果不确定。  例如，如果使用随后对**wcsrtombs**的调用而不是**wcstombs，** 则应用程序将使用**wcsrlen**而不是**wcsnlen。**

如果*mbstr*参数为**NULL，****则 wcsrtombs**返回目标字符串的所需大小（以字节为单位）。 如果*mbstate*为 null，则使用内部**mbstate_t**转换状态。 如果字符序列*wchar*没有相应的多字节字符表示形式，则返回 -1 并将**errno**设置为**EILSEQ**。

在 C++ 中，此函数具有一个调用此函数的更新、更安全副本的模板重载。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="exceptions"></a>例外

**wcsrtombs**函数是多线程安全的，只要当前线程调用中没有函数在执行任务时**设置局部性**，*并且 mbstate*不为 null。

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
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
