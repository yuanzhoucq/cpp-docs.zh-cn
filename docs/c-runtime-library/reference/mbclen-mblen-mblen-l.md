---
title: _mbclen、mblen、_mblen_l、_mbclen_l
ms.date: 01/22/2019
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
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
ms.openlocfilehash: 96775f513b33eb407981480c17cb609dd85383f6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952561"
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

*c*<br/>
多字节字符。

*mbstr*<br/>
多字节字符序列的地址。

*count*<br/>
要检查的字节数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

根据多字节字符*c*的长度是否为1或2字节， **_mbclen**返回1或2。 **_Mbclen**不会返回错误。 如果*mbstr*不**为 NULL**，则**mblen**将返回多字节字符的长度（以字节为单位）。 如果*mbstr*为**null**或它指向宽字符 null 字符，则**mblen**将返回0。 当*mbstr*指向的对象未形成第一个*计数*字符内的有效多字节字符时， **mblen**将返回-1。

## <a name="remarks"></a>备注

**_Mbclen**函数返回多字节字符*c*的长度（以字节为单位）。 如果*c*不指向由隐式调用 **_ismbblead**确定的多字节字符的前导字节，则 **_mbclen**的结果是不可预知的。

如果是有效的多字节字符，则**mblen**返回*mbstr*的长度（以字节为单位），并确定与代码页相关的多字节字符有效性。 **mblen**检查*mbstr*中包含的字节*数*或更少的字节数，但不能超过**MB_CUR_MAX**个字节。

输出值受区域设置的**LC_CTYPE**类别设置影响;有关详细信息，请参阅[setlocale](setlocale-wsetlocale.md) 。 这些不带 **_l**后缀的函数的版本对与区域设置相关的行为使用当前区域设置。 **_L**后缀版本的行为相同，但它们使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|映射到宏或内联函数|**_mbclen**|映射到宏或内联函数|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbccpy、_mbccpy_l](mbccpy-mbccpy-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
