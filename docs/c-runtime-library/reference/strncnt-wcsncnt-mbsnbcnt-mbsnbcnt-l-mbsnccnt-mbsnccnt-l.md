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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 77746af98e5d62b80d5a0d2d93eb1f717c74b33e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231333"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l

返回指定计数内的字符数或字节数。

> [!IMPORTANT]
> **_mbsnbcnt**、 **_mbsnbcnt_l**、 **_mbsnccnt**和 **_mbsnccnt_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

*字符串*<br/>
要检查的字符串。

*计数*<br/>
*字符串*中要检查的字符数或字节数。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsnbcnt**和 **_mbsnbcnt_l**返回*str*的多字节字符的第一个*计数*中找到的字节数。 **_mbsnccnt**和 **_mbsnccnt_l**返回*str*的第一个字节*计数*中找到的字符数。 如果在*str*的检查完成之前遇到 null 字符，则它们返回在空字符之前找到的字节数或字符数。 如果*str*包含的字符数或字节数少于*计数*，则它们将返回字符串中的字符数或字节数。 如果*count*小于零，则它们将返回0。 在以前的版本中，这些函数具有类型为的返回值， **`int`** 而不是**size_t**。

**_strncnt**返回单字节字符串*str*的第一个*计数*字节中的字符数。 **_wcsncnt**返回宽字符字符串*str*的第一个*计数*宽字符中的字符数。

## <a name="remarks"></a>备注

**_mbsnbcnt**和 **_mbsnbcnt_l**对*str*的多字节字符的第一个*计数*中找到的字节数进行计数。 **_mbsnbcnt**和 **_mbsnbcnt_l**替换**mtob** ，应使用代替**mtob**。

**_mbsnccnt**和 **_mbsnccnt_l**对*str*的第一个字节*计数*中找到的字符数进行计数。 如果 **_mbsnccnt**和 **_mbsnccnt_l**在双字节字符的第二个字节内遇到 null 字符，则第一个字节也被视为 null，并且不包含在返回的计数值中。 **_mbsnccnt**和 **_mbsnccnt_l**替换**btom** ，应使用代替**btom**。

如果*str*为**空**指针，或者*count*为0，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述， **errno**设置为**EINVAL**，并且该函数返回0。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)****。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|例程所返回的值|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|不适用|
|**_wcsncnt**|不适用|不适用|**_mbsnbcnt**|
|**_wcsncnt**|不适用|不适用|**_mbsnccnt**|
|不适用|不适用|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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

### <a name="output"></a>Output

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
