---
title: wctob
ms.date: 11/04/2016
api_name:
- wctob
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 151325b0d66e6d57156cdf94828ca1d4b151d437
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944933"
---
# <a name="wctob"></a>wctob

确定宽字符对应多字节字符，并返回该多字节字符的表示形式。

## <a name="syntax"></a>语法

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>参数

*wchar*<br/>
要转换的值。

## <a name="return-value"></a>返回值

如果**wctob**成功地转换宽字符，则它仅在多字节字符正好为一个字节时返回其多字节字符表示形式。 如果**wctob**遇到不能转换为多字节字符的宽字符，或者多字节字符的长度不能正好为一个字节，则返回-1。

## <a name="remarks"></a>备注

如果多字节字符的长度正好为一个字节，则**wctob**函数会将*wchar*中包含的宽字符转换为返回**int**值传递的相应多字节字符。

如果**wctob**不成功且未找到相应的多字节字符，则该函数将**Errno**设置为**eilseq 且**并返回-1。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序演示**wcstombs**函数的行为。

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
