---
title: _mbclen、mblen、_mblen_l、_mbclen_l
description: 描述 Microsoft C 运行时库 （CRT） _mbclen、mblen、_mblen_l 和_mbclen_l功能。
ms.date: 4/2/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
- _o__mbclen
- _o__mbclen_l
- _o__mblen_l
- _o_mblen
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mblen
- ftclen
- _mbclen
- _mbclen_l
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: 76e8771898d8baa65f275304a9aefdcaeeb5b3bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341124"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen、mblen、_mblen_l、_mbclen_l

获取长度并确定多字节字符的有效性。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*C*\
多字节字符。

*姆布斯特*\
多字节字符序列的地址。

*计数*\
要检查的字节数。

*现场*\
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbclen**和 **_mbclen_l**返回 1 或 2，根据多字节字符*c*的长度。 无论*c*是否为多字节，函数始终返回 1 表示 UTF-8。 **_mbclen**没有错误返回。

如果*mbstr*不是**NULL，****则 mblen**和 **_mblen_l**返回多字节字符的长度（以字节为单位）。 **mblen**和 **_mblen_l**函数在 UTF-8 上正常工作，并且可能返回介于 1 和 3 之间的值。 当*mbstr*为**NULL（** 或指向宽字符空字符）时 **，mblen**和 **_mblen_l**返回 0。 *mbstr*指向的对象必须在第一个*计数*字符中形成有效的多字节字符，或**mblen**和 **_mblen_l**返回 -1。

## <a name="remarks"></a>备注

**_mbclen**函数返回多字节字符*c*的长度（以字节为单位）。 如果*c*不指向多字节字符的引线字节（由对[_ismbblead](ismbblead-ismbblead-l.md)的隐式调用确定，**则_mbclen**的结果是不可预知的。

**如果长度**为*mbstr，* 则返回长度（mbstr）。如果长度是有效的多字节字符。 它还确定与代码页关联的多字节字符有效性。 **mblen**检查*mbstr*中包含的*计数*或更少字节，但不超过**MB_CUR_MAX**字节。

输出值受区域设置**LC_CTYPE**类别设置的影响。 没有 **_l**后缀的这些函数的版本使用此与区域设置相关的行为的当前区域设置。 **_l**后缀版本具有相同的行为，但它们使用传入区域设置参数。 有关详细信息，请参阅[设置区域设置](setlocale-wsetlocale.md)[和区域设置](../../c-runtime-library/locale.md)。

**_mbclen、_mblen_l**和 **_mbclen_l**是特定于 Microsoft 的，而不是标准 C 库的一部分。 **_mblen_l** 我们不建议您在需要便携式代码的地方使用它们。 对于标准 C 兼容性，请使用**mblen**或**mbrlen。**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|映射到宏或内联函数|**_mbclen**|映射到宏或内联函数|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>另请参阅

[字符分类](../../c-runtime-library/character-classification.md)\
[现场](../../c-runtime-library/locale.md)\
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy，_mbccpy_l](mbccpy-mbccpy-l.md)\
[姆布伦](mbrlen.md)\
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
