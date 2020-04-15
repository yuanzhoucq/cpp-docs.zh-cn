---
title: strchr、wcschr、_mbschr、_mbschr_l
ms.date: 4/2/2020
api_name:
- strchr
- wcschr
- _mbschr_l
- _mbschr
- _o__mbschr
- _o__mbschr_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcschr
- strchr
- wcschr
- _tcschr
- _mbschr
helpviewer_keywords:
- strings [C++], searching
- mbschr function
- _ftcschr function
- _mbschr function
- characters [C++], finding in strings
- _mbschr_l function
- ftcschr function
- wcschr function
- strchr function
- _tcschr function
- tcschr function
- mbschr_l function
ms.assetid: 2639905d-e983-43b7-b885-abef32cfac43
ms.openlocfilehash: ddfb90efdda4b5eccfcb8d8b4efeea528604fa68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354086"
---
# <a name="strchr-wcschr-_mbschr-_mbschr_l"></a>strchr、wcschr、_mbschr、_mbschr_l

使用当前区域设置或指定的 LC_CTYPE 转换状态类别查找字符串中的字符。

> [!IMPORTANT]
> `_mbschr` 和 `_mbschr_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *strchr(
   const char *str,
   int c
);  // C only
char *strchr(
   char * str,
   int c
); // C++ only
const char *strchr(
   const char * str,
   int c
); // C++ only
wchar_t *wcschr(
   const wchar_t *str,
   wchar_t c
); // C only
wchar_t *wcschr(
   wchar_t *str,
   wchar_t c
);  // C++ only
const wchar_t *wcschr(
   const wchar_t *str,
   wchar_t c
);  // C++ only
unsigned char *_mbschr(
   const unsigned char *str,
   unsigned int c
); // C only
unsigned char *_mbschr(
   unsigned char *str,
   unsigned int c
); // C++ only
const unsigned char *_mbschr(
   const unsigned char *str,
   unsigned int c
); // C++ only
unsigned char *_mbschr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C only
unsigned char *_mbschr_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
const unsigned char *_mbschr_l(
   const unsigned char *str,
   unsigned int c,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*Str*<br/>
null 终止的源字符串。

*C*<br/>
要查找的字符。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果找不到*c，* 则每个函数都会返回指向第一个在*str*中出现*c*的指针，或 NULL。

## <a name="remarks"></a>备注

函数`strchr`在*str*中查找*c*的第一次出现，或者如果找不到*c，* 则返回 NULL。 搜索中包括 null 终止的字符。

`wcschr`、`_mbschr` 和 `_mbschr_l` 是 `strchr` 的宽字符及多字节字符版本。 `wcschr` 的参数和返回值是宽字符字符串；而 `_mbschr` 的则是多字节字符字符串。 `_mbschr` 可识别多字节字符序列。 同样，如果字符串为空指针，则 `_mbschr` 将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，`_mbschr`则返回 NULL 并`errno`设置到 EINVAL。 `strchr` 和 `wcschr` 不会验证其参数。 否则这三个函数否则具有相同行为。

输出值受区域设置LC_CTYPE类别设置的影响;有关详细信息，请参阅[设置区域设置](setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C 中，这些函数为第一个参数采用**const**指针。 在 C++ 中，有两个重载可用。 带指针到**const**的重载返回指向**const 的**指针。将指针指向非**const**的版本返回指向非**const 的**指针。 如果这些函数的**const**版本和非**const**版本都可用，则定义宏_CRT_CONST_CORRECT_OVERLOADS。 如果两C++重载都需要非**const**行为，请定义符号_CONST_RETURN。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcschr`|`strchr`|`_mbschr`|`wcschr`|
|**_n/a**|**不适用**|`_mbschr_l`|**不适用**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|`strchr`|\<string.h>|
|`wcschr`|\<string.h> 或 \<wchar.h>|
|`_mbschr`, `_mbschr_l`|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strchr.c
//
// This program illustrates searching for a character
// with strchr (search forward) or strrchr (search backward).
//

#include <string.h>
#include <stdio.h>

int  ch = 'r';

char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int result;

   printf_s( "String to be searched:\n      %s\n", string );
   printf_s( "      %s\n      %s\n\n", fmt1, fmt2 );
   printf_s( "Search char:   %c\n", ch );

   // Search forward.
   pdest = strchr( string, ch );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf_s( "Result:   first %c found at position %d\n",
              ch, result );
   else
      printf_s( "Result:   %c not found\n", ch );

   // Search backward.
   pdest = strrchr( string, ch );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf_s( "Result:   last %c found at position %d\n", ch, result );
   else
      printf_s( "Result:\t%c not found\n", ch );
}
```

```Output
String to be searched:
      The quick brown dog jumps over the lazy fox
               1         2         3         4         5
      12345678901234567890123456789012345678901234567890

Search char:   r
Result:   first r found at position 12
Result:   last r found at position 30
```

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strstr、wcsstr、_mbsstr、_mbsstr_l](strstr-wcsstr-mbsstr-mbsstr-l.md)<br/>
