---
title: _strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l
ms.date: 11/04/2016
apiname:
- _strlwr_l
- _strlwr
- _wcslwr_l
- _mbslwr_l
- _wcslwr
- _mbslwr
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _strlwr
- wcslwr_l
- _ftcslwr
- mbslwr_l
- _mbslwr
- _wcslwr
- strlwr_l
- _tcslwr
- mbslwr
helpviewer_keywords:
- tcslwr function
- _strlwr function
- converting case
- string conversion [C++], case
- mbslwr function
- _strlwr_l function
- strlwr_l function
- _wcslwr function
- ftcslwr function
- strings [C++], case
- _tcslwr_l function
- _wcslwr_l function
- wcslwr_l function
- mbslwr_l function
- tcslwr_l function
- _tcslwr function
- converting case, CRT functions
- _ftcslwr function
- _mbslwr function
- case, converting
- strings [C++], converting case
- _mbslwr_l function
ms.assetid: d279181d-2e7d-401f-ab44-6e7c2786a046
ms.openlocfilehash: c9749a319d28d869babdb54859a80fa7f1916394
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210570"
---
# <a name="strlwr-wcslwr-mbslwr-strlwrl-wcslwrl-mbslwrl"></a>_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l

将字符串转换成小写形式。 这些函数的更安全版本已经发布，请参阅 [_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l ](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)。

> [!IMPORTANT]
> **_mbslwr**并 **_mbslwr_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
char *_strlwr(
   char * str
);
wchar_t *_wcslwr(
   wchar_t * str
);
unsigned char *_mbslwr(
   unsigned char * str
);
char *_strlwr_l(
   char * str,
   _locale_t locale
);
wchar_t *_wcslwr_l(
   wchar_t * str,
   _locale_t locale
);
unsigned char *_mbslwr_l(
   unsigned char * str,
   _locale_t locale
);
template <size_t size>
char *_strlwr(
   char (&str)[size]
); // C++ only
template <size_t size>
wchar_t *_wcslwr(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
unsigned char *_mbslwr(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
char *_strlwr_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
wchar_t *_wcslwr_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbslwr_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>参数

*str*<br/>
null 终止的字符串转换为小写。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

这些函数均返回指向已转换字符串的指针。 由于修改是就地完成的，因此所返回的指针与作为输入参数传递的指针相同。 没有保留任何返回值以指示错误。

## <a name="remarks"></a>备注

**_Strlwr**函数将转换中的任何大写字母*str*为小写，具体取决于**LC_CTYPE**类别设置的区域设置。 其他字符不受影响。 有关详细信息**LC_CTYPE**，请参阅[setlocale](setlocale-wsetlocale.md)。 无需这些函数的版本 **_l**后缀的当前区域设置用于其区域设置相关的行为; 的版本与 **_l**后缀完全相同，只不过它们使用传入的区域设置改为。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

**_Wcslwr**并 **_mbslwr**函数是宽字符及多字节字符版本的 **_strlwr**。 自变量和返回值 **_wcslwr**是宽字符字符串; **_mbslwr**是多字节字符字符串。 否则这三个函数否则具有相同行为。

如果*str*是**NULL**调用指针，无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回原始字符串并设置**errno**到**EINVAL**。

在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslwr**|**_strlwr**|**_mbslwr**|**_wcslwr**|
|**_tcslwr_l**|**_strlwr_l**|**_mbslwr_l**|**_wcslwr_l**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_strlwr**， **_strlwr_l**|\<string.h>|
|**_wcslwr**， **_wcslwr_l**|\<string.h> 或 \<wchar.h>|
|**_mbslwr**， **_mbslwr_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_strlwr.c
// compile with: /W3
// This program uses _strlwr and _strupr to create
// uppercase and lowercase copies of a mixed-case string.
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[100] = "The String to End All Strings!";
   char * copy1 = _strdup( string ); // make two copies
   char * copy2 = _strdup( string );

   _strlwr( copy1 ); // C4996
   // Note: _strlwr is deprecated; consider using _strlwr_s instead
   _strupr( copy2 ); // C4996
   // Note: _strupr is deprecated; consider using _strupr_s instead

   printf( "Mixed: %s\n", string );
   printf( "Lower: %s\n", copy1 );
   printf( "Upper: %s\n", copy2 );

   free( copy1 );
   free( copy2 );
}
```

```Output
Mixed: The String to End All Strings!
Lower: the string to end all strings!
Upper: THE STRING TO END ALL STRINGS!
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)<br/>
