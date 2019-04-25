---
title: wcstombs、_wcstombs_l
ms.date: 11/04/2016
apiname:
- wcstombs
- _wcstombs_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: d102cd74061faeb0c41823e6cf5c9a8ef335294f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188579"
---
# <a name="wcstombs-wcstombsl"></a>wcstombs、_wcstombs_l

将宽字符序列转换为对应的多字节字符序列。 提供这些函数的更多安全版本；请参阅 [wcstombs_s、_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)。

## <a name="syntax"></a>语法

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*mbstr*<br/>
多字节字符序列的地址。

*wcstr*<br/>
宽字符序列的地址。

*count*<br/>
多字节输出字符串可以存储的最大字节数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果**wcstombs**成功转换多字节字符串，它将返回到不包括终止 null （如果有） 的多字节输出字符串写入的字节数。 如果*mbstr*自变量是**NULL**， **wcstombs**返回以字节为单位的目标字符串所需的大小。 如果**wcstombs**遇到无法转换为多字节字符的宽字符则返回-1 强制转换为类型**size_t**并设置**errno**到**EILSEQ**.

## <a name="remarks"></a>备注

**Wcstombs**函数将转换的指向的宽字符字符串*wcstr*到相应的多字节字符，并将存储中的结果*mbstr*数组。 *计数*参数指示的最大可以为多字节输出字符串中存储的字节数 (即，大小*mbstr*)。 一般情况下，转换宽字符字符串时不会知道需要多少个字节。 某些宽字符在输出字符串中仅占一个字节；其他的字符则占两个。 如果输入字符串 （包括宽字符 null） 中的每个宽字符的多字节输出字符串中有两个字节，保证结果以适合。

如果**wcstombs**遇到宽字符 null 字符 (L '\0) 之前或当*计数*发生时，会将其转换为 8 位 0 并停止。 因此，在多字节字符字符串*mbstr*是 null 终止的仅当**wcstombs**在转换期间遇到宽字符 null 字符。 如果指向的序列*wcstr*并*mbstr*重叠的行为**wcstombs**是不确定的。

如果*mbstr*自变量是**NULL**， **wcstombs**返回以字节为单位的目标字符串所需的大小。

**wcstombs**验证其参数。 如果*wcstr*是**NULL**，或者，如果*计数*大于**INT_MAX**，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，该函数将设置**errno**到**EINVAL**并返回-1。

**wcstombs**的任何区域设置相关的行为; 使用当前区域设置 **_wcstombs_l**是完全相同，只不过它改用已传入的区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

本程序演示的行为**wcstombs**函数。

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
