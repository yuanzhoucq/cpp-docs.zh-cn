---
title: _strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l
ms.date: 4/2/2020
api_name:
- _wcsset
- _mbsset
- _strset_l
- _strset
- _wcsset_l
- _mbsset_l
- _o__mbsset
- _o__mbsset_l
- _o__wcsset
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsset
- _strset_l
- _mbsset
- _strset
- mbsset_l
- strset_l
- _wcsset
- _ftcsset
- wcsset_l
- _tcsset_l
- _mbsset_l
- _wcsset_l
- _fstrset
- _tcsset
helpviewer_keywords:
- _wcsset_l function
- _tcsset function
- wcsset_l function
- _ftcsset function
- characters [C++], setting
- _strset function
- ftcsset function
- strings [C++], setting characters
- mbsset function
- tcsset_l function
- _fstrset function
- mbsset_l function
- strset_l function
- _wcsset function
- _mbsset function
- _mbsset_l function
- tcsset function
- _strset_l function
- fstrset function
- _tcsset_l function
ms.assetid: c42ded42-2ed9-4f06-a0a9-247ba305473a
ms.openlocfilehash: 99cf969714115effcfd7f8f82b2247556d5dd110
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233998"
---
# <a name="_strset-_strset_l-_wcsset-_wcsset_l-_mbsset-_mbsset_l"></a>_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l

将字符串的字符设置为一个字符。 这些函数的更安全版本已经发布；请参阅 [_strset_s、_strset_s_l、_wcsset_s、_wcsset_s_l、_mbsset_s、_mbsset_s_l](strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md)。

> [!IMPORTANT]
> 不能在 Windows 运行时中执行的应用程序中使用 **_mbsset**和 **_mbsset_l** 。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *_strset(
   char *str,
   int c
);
char *_strset_l(
   char *str,
   int c,
   locale_t locale
);
wchar_t *_wcsset(
   wchar_t *str,
   wchar_t c
);
wchar_t *_wcsset_l(
   wchar_t *str,
   wchar_t c,
   locale_t locale
);
unsigned char *_mbsset(
   unsigned char *str,
   unsigned int c
);
unsigned char *_mbsset_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*字符串*<br/>
要设置的 null 终止字符串。

*ansi-c*<br/>
字符设置。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回指向修改后的字符串的指针。

## <a name="remarks"></a>备注

**_Strset**函数将*str*的所有字符（终止 null 字符除外）设置为*c*，并将其转换为 **`char`** 。 **_wcsset**和 **_mbsset_l**是 **_strset**的宽字符和多字节字符版本，参数和返回值的数据类型也有所不同。 否则这些函数具有相同行为。

**_mbsset**验证其参数。 如果*str*为空指针，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行， **_mbsset**将返回**NULL** ，并将**errno**设置为**EINVAL**。 **_strset**和 **_wcsset**不会验证其参数。

输出值受区域设置的**LC_CTYPE**类别设置的设置的影响;有关详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md) 。 这些函数的版本相同，不同之处在于没有 **_l**后缀的函数使用当前区域设置，而使用了 **_l**后缀的区域设置，则使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

> [!IMPORTANT]
> 这些函数可能容易受到的缓冲区溢出的威胁。 缓冲区溢出可以用于系统攻击，因为它们可能使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsset**|**_strset**|**_mbsset**|**_wcsset**|
|**_tcsset_l**|**_strset_l**|**_mbsset_l**|**_wcsset_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_strset**|\<string.h>|
|**_strset_l**|\<tchar.h>|
|**_wcsset**|\<string.h> 或 \<wchar.h>|
|**_wcsset_l**|\<tchar.h>|
|**_mbsset**， **_mbsset_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strset.c
// compile with: /W3

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[] = "Fill the string with something.";
   printf( "Before: %s\n", string );
   _strset( string, '*' ); // C4996
   // Note: _strset is deprecated; consider using _strset_s instead
   printf( "After:  %s\n", string );
}
```

```Output
Before: Fill the string with something.
After:  *******************************
```

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbset、_mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[memset、wmemset](memset-wmemset.md)<br/>
[strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
