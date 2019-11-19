---
title: strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l
ms.date: 11/04/2016
api_name:
- _wcsncat_s_l
- wcsncat_s
- _mbsncat_s_l
- _mbsncat_s
- strncat_s
- _strncat_s_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strncat_s_l
- _mbsncat_s_l
- _tcsncat_s
- wcsncat_s
- wcsncat_s_l
- strncat_s
- _mbsncat_s
- _tcsncat_s_l
helpviewer_keywords:
- concatenating strings
- _mbsncat_s function
- mbsncat_s_l function
- _tcsncat_s function
- _mbsncat_s_l function
- strncat_s function
- strings [C++], appending
- strncat_s_l function
- string concatenation [C++]
- _tcsncat_s_l function
- wcsncat_s function
- appending strings
- wcsncat_s_l function
- mbsncat_s function
ms.assetid: de77eca2-4d9c-4e66-abf2-a95fefc21e5a
ms.openlocfilehash: 7b76f20516cbf20530f20d3f5b6d1978cfeaaef4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626173"
---
# <a name="strncat_s-_strncat_s_l-wcsncat_s-_wcsncat_s_l-_mbsncat_s-_mbsncat_s_l"></a>strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l

向字符串追加字符。 这些版本的 [strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) 具有安全性增强功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

> [!IMPORTANT]
> **_mbsncat_s**和 **_mbsncat_s_l**不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t strncat_s(
   char *strDest,
   size_t numberOfElements,
   const char *strSource,
   size_t count
);
errno_t _strncat_s_l(
   char *strDest,
   size_t numberOfElements,
   const char *strSource,
   size_t count,
   _locale_t locale
);
errno_t wcsncat_s(
   wchar_t *strDest,
   size_t numberOfElements,
   const wchar_t *strSource,
   size_t count
);
errno_t _wcsncat_s_l(
   wchar_t *strDest,
   size_t numberOfElements,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
errno_t _mbsncat_s(
   unsigned char *strDest,
   size_t numberOfElements,
   const unsigned char *strSource,
   size_t count
);
errno_t _mbsncat_s_l(
   unsigned char *strDest,
   size_t numberOfElements,
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t strncat_s(
   char (&strDest)[size],
   const char *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _strncat_s_l(
   char (&strDest)[size],
   const char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
template <size_t size>
errno_t wcsncat_s(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _wcsncat_s_l(
   wchar_t (&strDest)[size],
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbsncat_s(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsncat_s_l(
   unsigned char (&strDest)[size],
   const unsigned char *strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*strDest*<br/>
null 终止的目标字符串。

*numberOfElements*<br/>
目标缓冲区的大小。

*strSource*<br/>
null 终止的源字符串。

*count*<br/>
要追加的字符数或 [_TRUNCATE](../../c-runtime-library/truncate.md)。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果成功，则返回 0；如果失败，则为错误代码。

### <a name="error-conditions"></a>错误条件

|*strDestination*|*numberOfElements*|*strSource*|返回值|*StrDestination*的内容|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL**或未终止|any|any|**EINVAL**|未修改|
|any|any|**NULL**|**EINVAL**|未修改|
|any|0 或过小|any|**ERANGE**|未修改|

## <a name="remarks"></a>备注

这些函数尝试将*strSource*的前*D*个字符追加到*StrDest*的末尾，其中*D*是*计数*的较小和*strSource*的长度。 如果将这些*D*字符追加到*strDest* （其大小被指定为*numberOfElements*），并且仍为 null 终止符留出空间，则会追加这些字符，从*strDest*，并追加新的终止 null 值;否则， *strDest*[0] 设置为 null 字符，并调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。

在上段描述的内容中有一个例外。 如果*count*为[_TRUNCATE](../../c-runtime-library/truncate.md) ，则在仍有空间追加终止 null 值时，会在*StrDest*中追加最多*strSource* 。

例如，应用于对象的

```C
char dst[5];
strncpy_s(dst, _countof(dst), "12", 2);
strncat_s(dst, _countof(dst), "34567", 3);
```

表示我们要求**strncat_s**将三个字符追加到缓冲区中的两个字符（长度为5个字符）;这将不会为 null 终止符留出空间，因此**strncat_s**将字符串输出为零，并调用无效的参数处理程序。

如果需要截断行为，请使用 **_TRUNCATE**或相应地调整*size*参数：

```C
strncat_s(dst, _countof(dst), "34567", _TRUNCATE);
```

或

```C
strncat_s(dst, _countof(dst), "34567", _countof(dst)-strlen(dst)-1);
```

在所有情况下，结果字符串以 null 字符终止。 如果复制出现在重叠的字符串之间，则该行为不确定。

如果*strSource*或*strDest*为**NULL**，或者*numberOfElements*为0，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数返回**EINVAL** ，而不修改其参数。

**wcsncat_s**和 **_mbsncat_s**是**strncat_s**的宽字符和多字节字符版本。 **Wcsncat_s**的字符串参数和返回值是宽字符字符串; **_mbsncat_s**的这些字符串是多字节字符字符串。 否则这三个函数否则具有相同行为。

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 (不再需要指定大小自变量)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。 有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。

这些函数的调试库版本首先用0xFE 填充缓冲区。 若要禁用此行为，请使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncat_s**|**strncat_s**|**_mbsnbcat_s**|**wcsncat_s**|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

**_strncat_s_l**和 **_wcsncat_s_l**没有区域设置依赖关系;它们只是为 **_tcsncat_s_l**提供的。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**strncat_s**|\<string.h>|
|**wcsncat_s**|\<string.h> 或 \<wchar.h>|
|**_mbsncat_s**、 **_mbsncat_s_l**|\<mbstring.h>|

有关其他兼容性信息，请参见 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```cpp
// crt_strncat_s.cpp
// compile with: /MTd

// These #defines enable secure template overloads
// (see last part of Examples() below)
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <crtdbg.h>  // For _CrtSetReportMode
#include <errno.h>

// This example uses a 10-byte destination buffer.

errno_t strncat_s_tester( const char * initialDest,
                          const char * src,
                          int count )
{
   char dest[10];
   strcpy_s( dest, _countof(dest), initialDest );

   printf_s( "\n" );

   if ( count == _TRUNCATE )
      printf_s( "Appending '%s' to %d-byte buffer dest with truncation semantics\n",
               src, _countof(dest) );
   else
      printf_s( "Appending %d chars of '%s' to %d-byte buffer dest\n",
              count, src, _countof(dest) );

   printf_s( "    old contents of dest: '%s'\n", dest );

   errno_t err = strncat_s( dest, _countof(dest), src, count );

   printf_s( "    new contents of dest: '%s'\n", dest );

   return err;
}

void Examples()
{
   strncat_s_tester( "hi ", "there", 4 );
   strncat_s_tester( "hi ", "there", 5 );
   strncat_s_tester( "hi ", "there", 6 );

   printf_s( "\nDestination buffer too small:\n" );
   strncat_s_tester( "hello ", "there", 4 );

   printf_s( "\nTruncation examples:\n" );

   errno_t err = strncat_s_tester( "hello ", "there", _TRUNCATE );
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"
                                                       : "did not" );

   err = strncat_s_tester( "hello ", "!", _TRUNCATE );
   printf_s( "    truncation %s occur\n", err == STRUNCATE ? "did"
                                                       : "did not" );

   printf_s( "\nSecure template overload example:\n" );

   char dest[10] = "cats and ";
   strncat( dest, "dachshunds", 15 );
   // With secure template overloads enabled (see #define
   // at top of file), the preceding line is replaced by
   //    strncat_s( dest, _countof(dest), "dachshunds", 15 );
   // Instead of causing a buffer overrun, strncat_s invokes
   // the invalid parameter handler.
   // If secure template overloads were disabled, strncat would
   // append "dachshunds" and overrun the dest buffer.
   printf_s( "    new contents of dest: '%s'\n", dest );
}

void myInvalidParameterHandler(
   const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf_s(L"Invalid parameter handler invoked: %s\n", expression);
}

int main( void )
{
   _invalid_parameter_handler oldHandler, newHandler;

   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);
   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   Examples();
}
```

```Output
Appending 4 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hi '
    new contents of dest: 'hi ther'

Appending 5 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hi '
    new contents of dest: 'hi there'

Appending 6 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hi '
    new contents of dest: 'hi there'

Destination buffer too small:

Appending 4 chars of 'there' to 10-byte buffer dest
    old contents of dest: 'hello '
Invalid parameter handler invoked: (L"Buffer is too small" && 0)
    new contents of dest: ''

Truncation examples:

Appending 'there' to 10-byte buffer dest with truncation semantics
    old contents of dest: 'hello '
    new contents of dest: 'hello the'
    truncation did occur

Appending '!' to 10-byte buffer dest with truncation semantics
    old contents of dest: 'hello '
    new contents of dest: 'hello !'
    truncation did not occur

Secure template overload example:
Invalid parameter handler invoked: (L"Buffer is too small" && 0)
    new contents of dest: ''
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[多字节字符序列的解释](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[strcat、wcscat、_mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy、wcscpy、_mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
