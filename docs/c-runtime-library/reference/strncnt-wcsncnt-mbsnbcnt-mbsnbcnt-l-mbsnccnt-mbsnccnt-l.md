---
title: _strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l
ms.date: 11/04/2016
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 6322f9511f0813eeaeb49383f49c73e361048cd9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573417"
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l

返回指定计数内的字符数或字节数。

> [!IMPORTANT]
> **_mbsnbcnt**， **_mbsnbcnt_l**， **_mbsnccnt**，并且 **_mbsnccnt_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

*str*<br/>
要检查的字符串。

*count*<br/>
字符数或字节中要检查其*str*。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

**_mbsnbcnt**并 **_mbsnbcnt_l**返回找到的字节数在第一个*计数*的多字节字符*str*。 **_mbsnccnt**并 **_mbsnccnt_l**返回找到的字符数在第一个*计数*的字节数*str*。 如果的检查之前遇到 null 字符*str*已完成，它们返回的字节数或 null 字符之前找到的字符数。 如果*str*组成少于*计数*字符或字节数，它们在字符串中返回的字符或字节数。 如果*计数*小于零，则它们返回 0。 在早期版本中，这些函数必须返回值类型**int**而非**size_t**。

**_strncnt**在第一个返回的字符数*计数*单字节字符串的字节*str*。 **_wcsncnt**在第一个返回的字符数*计数*宽字符的宽字符字符串*str*。

## <a name="remarks"></a>备注

**_mbsnbcnt**并 **_mbsnbcnt_l**计数找到的字节数在第一个*计数*的多字节字符*str*。 **_mbsnbcnt**并 **_mbsnbcnt_l**替换为**mtob** ，应使用来代替**mtob**。

**_mbsnccnt**并 **_mbsnccnt_l**计数找到的字符数在第一个*计数*的字节数*str*。 如果 **_mbsnccnt**并 **_mbsnccnt_l**遇到双字节字符的第二个字节中的 null 字符，则第一个字节也被视为为 null，不包含在返回的计数值。 **_mbsnccnt**并 **_mbsnccnt_l**替换为**btom** ，应使用来代替**btom**。

如果*str*是**NULL**指针或是*计数*为 0，则这些函数将调用无效参数处理程序中所述[参数验证](../../c-runtime-library/parameter-validation.md)， **errno**设置为**EINVAL**，并且该函数返回 0。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|例程所返回的值|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|n/a|
|**_wcsncnt**|n/a|n/a|**_mbsnbcnt**|
|**_wcsncnt**|n/a|n/a|**_mbsnccnt**|
|n/a|n/a|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
