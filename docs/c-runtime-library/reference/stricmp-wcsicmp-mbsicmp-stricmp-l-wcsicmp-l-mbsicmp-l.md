---
title: _stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l
ms.date: 11/04/2016
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
ms.openlocfilehash: d27b2128d79d7ff3ab0150e182d494fed52d46ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353829"
---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l

执行不区分大小写的字符串比较。

> [!IMPORTANT]
> **_mbsicmp**并 **_mbsicmp_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*string1*， *string2*<br/>
要比较的 null 终止的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回值指示之间的关系*string1*到*string2* ，如下所示。

|返回值|描述|
|------------------|-----------------|
|< 0|*string1*小于*string2*|
|0|*string1*等于*string2*|
|> 0|*string1*大于*string2*|

发生错误时， **_mbsicmp**返回 **_NLSCMPERROR**，其定义中\<string.h > 和\<mbstring.h >。

## <a name="remarks"></a>备注

**_Stricmp**序号函数对比*string1*并*string2*之后转换为小写，并返回一个值，指示二者关系的每个字符。 **_stricmp**不同于 **_stricoll**在于 **_stricmp**比较仅受到**LC_CTYPE**，用于确定哪些字符被上部和小写。 **_Stricoll**函数对根据字符串进行比较**LC_CTYPE**并**LC_COLLATE**类别的区域设置，包括大小写和排序规则顺序。 有关详细信息**LC_COLLATE**类别中，请参阅[setlocale](setlocale-wsetlocale.md)并[区域设置类别](../../c-runtime-library/locale-categories.md)。 无需这些函数的版本 **_l**后缀的区域设置相关的行为使用当前区域设置。 带后缀的版本是相同的，只不过它们转而使用传入的区域设置。 如果尚未设置区域设置，则使用 C 区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> **_stricmp**等效于 **_strcmpi**。 它们可以互换使用，但 **_stricmp**是首选的标准。

**_Strcmpi**函数等同于 **_stricmp** ，提供是为了向后兼容性。

因为 **_stricmp**进行小写比较，它可能会导致意外行为。

为了说明何时大小写的转换 **_stricmp**影响结果的比较，假设你有两个字符串 JOHNSTON 和 john_henry。 字符串 JOHN_HENRY 被视为小于 JOHNSTON，因为“_”的 ASCII 值小于小写的 S。实际上，ASCII 值介于 91 和 96 之间的任何字符都将被视为小于任何字母。

如果[strcmp](strcmp-wcscmp-mbscmp.md)而不是使用函数 **_stricmp**，则 john_henry 将大于 JOHNSTON。

**_wcsicmp**并 **_mbsicmp**宽字符及多字节字符版本的 **_stricmp**。 参数和返回值 **_wcsicmp**是宽字符字符串; **_mbsicmp**是多字节字符字符串。 **_mbsicmp**根据当前的多字节代码页识别多字节字符序列，并返回 **_NLSCMPERROR**发生错误时。 有关详细信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。 否则这三个函数否则具有相同行为。

**_wcsicmp**并**wcscmp**行为方式相同，只不过**wcscmp**不转换为小写进行比较前其自变量。 **_mbsicmp**并 **_mbscmp**行为方式相同，只不过 **_mbscmp**不转换为小写进行比较前其自变量。

将需要调用[setlocale](setlocale-wsetlocale.md)有关 **_wcsicmp**使用 Latin 1 字符。 C 区域设置是有效的默认值，因此，例如，ä 将不之间的比较等于 Ä。 调用**setlocale**的调用之前的 C 区域设置以外的任何区域设置 **_wcsicmp**。 下面的示例演示如何 **_wcsicmp**是区域设置影响：

```C
// crt_stricmp_locale.c
#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

一种替代方法是调用[_create_locale、 _wcreate_locale](create-locale-wcreate-locale.md)并将返回的区域设置对象作为参数传递 **_wcsicmp_l**。

所有这些函数都验证其参数。 如果任一*string1*或*string2*是空指针，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，这些函数将返回 **_NLSCMPERROR**并设置**errno**到**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_stricmp**， **_stricmp_l**|\<string.h>|
|**_wcsicmp**， **_wcsicmp_l**|\<string.h> 或 \<wchar.h>|
|**_mbsicmp**， **_mbsicmp_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_stricmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>请参阅

[字符串操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp、wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp、_memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp、wcscmp、_mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn、wcsspn、_mbsspn、_mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
