---
title: wctomb_s、_wctomb_s_l
ms.date: 11/04/2016
apiname:
- _wctomb_s_l
- wctomb_s
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
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 1eaa6f0b81daaa7d8c7626398fe30b45ead979c3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498919"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s、_wctomb_s_l

将一个宽字符转换为相应的多字节字符。 [wctomb、_wctomb_l](wctomb-wctomb-l.md) 的一个版本，具有 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全增强功能。

## <a name="syntax"></a>语法

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*pRetValue*<br/>
字节数或指明结果的代码。

*mbchar*<br/>
多字节字符的地址。

*sizeInBytes*<br/>
缓冲区*mbchar*的大小。

*wchar*<br/>
宽字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，返回零；如果失败，则返回错误代码。

错误条件

|*mbchar*|*sizeInBytes*|返回值|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|未修改|
|任何|>**INT_MAX**|**EINVAL**|未修改|
|任何|过小|**EINVAL**|未修改|

如果发生上述错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则**wctomb**将返回**EINVAL** , 并将**errno**设置为**EINVAL**。

## <a name="remarks"></a>备注

**Wctomb_s**函数将其*wchar*参数转换为相应的多字节字符, 并将结果存储在*mbchar*。 可以从任何程序的任何程序点调用该函数。

如果**wctomb_s**将宽字符转换为多字节字符, 则它会将宽字符中的字节数 (绝不大于**MB_CUR_MAX**) 放置在*pRetValue*所指向的整数中。 如果*wchar*为宽字符 null 字符 (L ' \ 0 '), 则**wctomb_s**将*pRetValue*填充为1。 如果目标指针*mbchar*为**NULL**, 则**wctomb_s**会将0放入*pRetValue*。 如果当前区域设置中不能进行转换, 则**wctomb_s**会将-1 置于*pRetValue*中。

**wctomb_s**对与区域设置相关的信息使用当前区域设置; **_wctomb_s_l**是相同的, 只不过它使用传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序演示**wctomb**函数的行为。

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
