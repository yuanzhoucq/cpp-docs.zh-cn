---
title: strstr、wcsstr、_mbsstr、_mbsstr_l
ms.date: 4/2/2020
api_name:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
- _o__mbsstr
- _o__mbsstr_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 1fb6c025ec324fceb1b11dd23ed61500f08b4535
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911003"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr、wcsstr、_mbsstr、_mbsstr_l

返回指向字符串中的搜索字符串的第一个匹配项的指针。

> [!IMPORTANT]
> `_mbsstr` 和 `_mbsstr_l` 无法用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*字符串*<br/>
要搜索的 null 终止的字符串。

*strSearch*<br/>
要搜索的以 null 结尾的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回指向*str*中第一次出现的*strSearch*的指针; 如果*strSearch*未出现在*str*中，则返回 NULL。 如果*strSearch*指向长度为零的字符串，则函数将返回*str*。

## <a name="remarks"></a>备注

`strstr`函数返回一个指针，该指针指向*str*中*strSearch*的第一个匹配项。 搜索不包括结尾的 null 字符。 `wcsstr` 是宽字符版本的 `strstr`；`_mbsstr` 是多字节字符版本。 `wcsstr` 的参数和返回值是宽字符字符串；而 `_mbsstr` 的则是多字节字符字符串。 `_mbsstr` 会验证其参数。 如果*str*或*strSearch*为 NULL，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续， `_mbsstr`则将设置`errno`为 EINVAL，并返回0。 `strstr` 和 `wcsstr` 不会验证其参数。 否则这三个函数否则具有相同行为。

> [!IMPORTANT]
> 这些函数可能从缓冲区溢出问题引发威胁。 缓冲区溢出问题可用来攻击系统，因为它们可能允许执行任意代码，这可能导致没有保证的权限提升。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

在 C 中，这些函数使用第一个参数的**常量**指针。 在 C++ 中，有两个重载可用。 采用指向**const**的指针的重载返回指向**const**的指针;采用指向非常**量**的指针的版本返回指向非常**量**的指针。 如果这些函数的**常量**和非常**量**版本都可用，则会定义宏 _CRT_CONST_CORRECT_OVERLOADS。 如果这两个 c + + 重载都需要非常**量**行为，请定义符号 _CONST_RETURN。

输出值受 LC_CTYPE 的区域设置类别设置的影响;有关详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md)。 没有 **_l**后缀的这些函数的版本对与区域设置相关的行为使用当前区域设置;具有 **_l**后缀的版本相同，只不过它们改用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**不适用**|**不适用**|`_mbsstr_l`|**不适用**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> 或 \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>另请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[本地](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::find](../../standard-library/basic-string-class.md#find)<br/>
