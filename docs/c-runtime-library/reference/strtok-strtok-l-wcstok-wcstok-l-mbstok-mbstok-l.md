---
title: strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l
ms.date: 03/25/2019
apiname:
- _mbstok_l
- _mbstok
- wcstok
- _mbstok
- strtok
- _wcstok_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstok
- strtok
- _tcstok
- wcstok
helpviewer_keywords:
- mbstok_l function
- strings [C++], searching
- tcstok function
- _tcstok function
- _strtok_l function
- strtok function
- mbstok function
- wcstok_l function
- _mbstok function
- tcstok_l function
- tokens, finding in strings
- _mbstok_l function
- wcstok function
- _wcstok_l function
- _tcstok_l function
- strtok_l function
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
ms.openlocfilehash: 13fbc0e305f7ad183db06ec0060b2059b4964fe7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500795"
---
# <a name="strtok-_strtok_l-wcstok-_wcstok_l-_mbstok-_mbstok_l"></a>strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l

通过使用当前区域设置或传入的指定区域设置，查找在字符串中的下一个标记。 提供这些函数的更多安全版本；请参阅 [strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)。

> [!IMPORTANT]
> **_mbstok**和 **_mbstok_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *strtok(
   char *strToken,
   const char *strDelimit
);
char *strtok_l(
   char *strToken,
   const char *strDelimit,
   _locale_t locale
);
wchar_t *wcstok(
   wchar_t *strToken,
   const wchar_t *strDelimit
);
wchar_t *wcstok_l(
   wchar_t *strToken,
   const wchar_t *strDelimit,
   _locale_t locale
);
unsigned char *_mbstok(
   unsigned char *strToken,
   const unsigned char *strDelimit
);
unsigned char *_mbstok_l(
   unsigned char *strToken,
   const unsigned char *strDelimit,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*strToken*<br/>
包含一个或多个标记的字符串。

*strDelimit*<br/>
分隔符字符组。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回一个指针, 该指针指向在*strToken*中找到的下一个标记。 当找不到更多的标记时, 函数将返回**NULL** 。 每个调用都通过将 null 字符替换为在返回的标记后出现的第一个分隔符来修改*strToken* 。

## <a name="remarks"></a>备注

**Strtok**函数查找*strToken*中的下一个标记。 *StrDelimit*中的字符集指定要在当前调用的*strToken*中找到的令牌的可能分隔符。 **wcstok**和 **_mbstok**是**strtok**的宽字符和多字节字符版本。 **Wcstok**的参数和返回值是宽字符字符串; **_mbstok**的这些字符串是多字节字符字符串。 否则这三个函数否则具有相同行为。

> [!IMPORTANT]
> 这些函数会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](/windows/win32/SecBP/avoiding-buffer-overruns)。

第一次调用**strtok**时, 函数跳过前导分隔符并返回指向*strToken*中第一个标记的指针, 并将标记终止为 null 字符。 通过一系列对**strtok**的调用, 可以将更多标记分解出*strToken*的剩余部分。 对**strtok**的每次调用都会通过在该调用返回的**标记**后插入一个 Null 字符来修改*strToken* 。 若要从*strToken*中读取下一个令牌, 请对*strToken*参数调用**strtok** , 并为其提供**NULL**值。 **NULL** *strToken*参数会导致**Strtok**在修改后的*strToken*中搜索下一个标记。 *StrDelimit*参数可以从一个调用到下一个调用, 以使分隔符集不同。

输出值受区域设置的**LC_CTYPE**类别设置的设置影响。 有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。

这些不带 **_l**后缀的函数的版本对与区域设置相关的行为使用当前区域设置。 带有 **_l**后缀的版本是相同的, 只不过它们使用传入的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> 每个函数均使用线程本地静态变量，以将字符串分析为标记。 因此，多线程可以同时调用这些函数，不会产生不良影响。 但是，在单个线程内，对任一这些函数的交替调用很可能导致数据损坏和结果不准确。 解析不同的字符串时，在解析完一个字符串后再开始解析下一个字符串。 此外，请注意，从调用其他函数的循环内调用其中任一函数可能引发潜在危险。 如果其他函数最终使用这些函数之一，则导致调用交错的序列，从而触发数据损坏。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok**|**strtok**|**_mbstok**|**wcstok**|
|**_tcstok**|**_strtok_l**|**_mbstok_l**|**_wcstok_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strtok**|\<string.h>|
|**wcstok**|\<string.h> 或 \<wchar.h>|
|**_mbstok**、 **_mbstok_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strtok.c
// compile with: /W3
// In this program, a loop uses strtok
// to print all the tokens (separated by commas
// or blanks) in the string named "string".
//
#include <string.h>
#include <stdio.h>

char string[] = "A string\tof ,,tokens\nand some  more tokens";
char seps[]   = " ,\t\n";
char *token;

int main( void )
{
   printf( "Tokens:\n" );

   // Establish string and get the first token:
   token = strtok( string, seps ); // C4996
   // Note: strtok is deprecated; consider using strtok_s instead
   while( token != NULL )
   {
      // While there are tokens in "string"
      printf( " %s\n", token );

      // Get next token:
      token = strtok( NULL, seps ); // C4996
   }
}
```

```Output
Tokens:
A
string
of
tokens
and
some
more
tokens
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn、wcscspn、_mbscspn、_mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
