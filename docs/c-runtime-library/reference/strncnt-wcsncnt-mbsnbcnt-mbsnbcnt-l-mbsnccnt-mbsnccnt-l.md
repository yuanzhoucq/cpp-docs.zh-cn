---
title: _strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
ms.date: 4/2/2020
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
- _o__mbsnbcnt
- _o__mbsnbcnt_l
- _o__mbsnccnt
- _o__mbsnccnt_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: bfd339a38dd5df30ece72059525860603ee10748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364181"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l

返回指定计数内的字符数或字节数。

> [!IMPORTANT]
> **_mbsnbcnt**_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt 和 **_mbsnccnt_l**不能在 Windows 运行时中执行的应用程序中使用。 **_mbsnbcnt_l** **_mbsnccnt** 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*Str*<br/>
要检查的字符串。

*count*<br/>
要在*str*中检查的字符或字节数。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsnbcnt**和 **_mbsnbcnt_l**返回在*str*的多字节字符的第一*个计数*中找到的字节数。 **_mbsnccnt****和_mbsnccnt_l**返回在第一*个计数* *str*中找到的字符数。 如果在检查*str*完成之前遇到空字符，则返回在空字符之前找到的字节或字符数。 如果*str*由少于*计数*字符或字节组成，它们将返回字符串中的字符数或字节数。 如果*计数*小于零，则返回 0。 在以前的版本中，这些函数的返回值为**int，** 而不是**size_t**。

**_strncnt**返回单字节字符串*的第*一*个计数*字节中的字符数。 **_wcsncnt**返回宽字符字符串*str*的第一*个计数*宽字符中的字符数。

## <a name="remarks"></a>备注

**_mbsnbcnt**和 **_mbsnbcnt_l**计算*str*的多字节字符的第一*个计数*中找到的字节数。 **_mbsnbcnt**和 **_mbsnbcnt_l**替换**mtob，** 应代替**mtob。**

**_mbsnccnt****和_mbsnccnt_l**计算*在 str*字节的第一*个计数*中找到的字符数。 如果 **_mbsnccnt**和 **_mbsnccnt_l**双字节字符的第二个字节中遇到空字符，则第一个字节也被视为 null，并且不包括在返回的计数值中。 **_mbsnccnt****和_mbsnccnt_l**取代**btom，** 应该用代替**btom。**

如果*str*是**NULL**指针或*计数*为 0，则这些函数将调用参数[验证](../../c-runtime-library/parameter-validation.md)中所述的无效参数处理程序 **，errno**设置为**EINVAL，** 函数返回 0。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)****。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|不适用|
|**_wcsncnt**|不适用|不适用|**_mbsnbcnt**|
|**_wcsncnt**|不适用|不适用|**_mbsnccnt**|
|不适用|不适用|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>输出

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
