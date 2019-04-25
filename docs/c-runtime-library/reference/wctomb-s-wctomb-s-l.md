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
ms.openlocfilehash: 08e8cb0ddaac342682776600fd0fd8b3d26b8953
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188480"
---
# <a name="wctombs-wctombsl"></a>wctomb_s、_wctomb_s_l

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
缓冲区的大小*mbchar*。

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

如果发生上述错误情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**wctomb**返回**EINVAL**并设置**errno**到**EINVAL**。

## <a name="remarks"></a>备注

**Wctomb_s**函数将其*wchar*参数的相应多字节字符，并将存储在结果*mbchar*。 可以从任何程序的任何程序点调用该函数。

如果**wctomb_s**将宽字符转换为多字节字符，它会将字节数 (即永远不会大于**MB_CUR_MAX**) 中由指向整数的宽字符*pRetValue*。 如果*wchar*是宽字符 null 字符 (L '\0)， **wctomb_s**填充*pRetValue* 1。 如果目标指针*mbchar*是**NULL**， **wctomb_s**将 0 放入*pRetValue*。 如果在当前区域设置中不支持转换，则**wctomb_s** -1 放*pRetValue*。

**wctomb_s**的区域设置相关的信息; 使用当前区域设置 **_wctomb_s_l**是完全相同，只不过它改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

本程序演示的行为**wctomb**函数。

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
