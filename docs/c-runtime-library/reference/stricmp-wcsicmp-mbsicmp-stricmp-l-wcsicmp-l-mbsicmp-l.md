---
title: _stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l
ms.date: 4/2/2020
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
- _o__mbsicmp
- _o__mbsicmp_l
- _o__stricmp
- _o__stricmp_l
- _o__wcsicmp
- _o__wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 315a86c5cf7e58219bad25f2b6633dd91275c09f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320460"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l

执行不区分大小写的字符串比较。

> [!IMPORTANT]
> **_mbsicmp**和 **_mbsicmp_l**不能在 Windows 运行时中执行的应用程序中使用。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

*字符串1*，*字符串2*<br/>
要比较的 null 终止的字符串。

*现场*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回值指示*string1*到*string2*的关系，如下所示。

|返回值|说明|
|------------------|-----------------|
|< 0|*字符串1*小于*字符串2*|
|0|*字符串1*与*字符串2*相同|
|> 0|*字符串1*大于*字符串2*|

在错误时 **，_mbsicmp**返回 **_NLSCMPERROR**，该返回\<在 string.h \<> 和 mbstring.h>中定义。

## <a name="remarks"></a>备注

**_stricmp**函数在将每个字符转换为小写后，将*string1*和*string2*进行二级比较，并返回指示其关系的值。 **_stricmp**不同于 **_stricoll，****因为_stricmp**比较只受LC_CTYPE的影响，而**LC_CTYPE**决定了哪些字符是大写字母和小写字母。 **_stricoll**函数根据区域设置**LC_CTYPE**和**LC_COLLATE**类别比较字符串，其中包括大小写和排序规则。 有关**LC_COLLATE**类别的详细信息，请参阅[设置区域设置](setlocale-wsetlocale.md)[和区域设置类别](../../c-runtime-library/locale-categories.md)。 没有 **_l**后缀的这些函数的版本使用当前区域设置进行与区域设置相关的行为。 带后缀的版本是相同的，只不过它们转而使用传入的区域设置。 如果尚未设置区域设置，则使用 C 区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> **_stricmp**相当于 **_strcmpi。** 它们可以互换使用，但 **_stricmp**是首选标准。

**_strcmpi**函数等效于 **_stricmp，** 并且仅针对向后兼容性提供。

由于 **_stricmp**进行小写比较，因此可能会导致意外行为。

要说明**大小写**转换_stricmp何时影响比较结果，假定您具有两个字符串 JOHNSTON 和JOHN_HENRY。 字符串 JOHN_HENRY 被视为小于 JOHNSTON，因为“_”的 ASCII 值小于小写的 S。实际上，ASCII 值介于 91 和 96 之间的任何字符都将被视为小于任何字母。

如果使用[strcmp](strcmp-wcscmp-mbscmp.md)函数而不是 **_stricmp，JOHN_HENRY**将大于约翰斯顿。

**_wcsicmp**和 **_mbsicmp**是宽字符和多字节字符版本的 **_stricmp。** **_wcsicmp**的参数和返回值是宽字符字符串;**_mbsicmp**的字符串是多字节字符串。 **_mbsicmp**根据当前多字节代码页识别多字节字符序列，并在错误时返回 **_NLSCMPERROR。** 有关详细信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。 否则这三个函数否则具有相同行为。

**_wcsicmp**和**wcscmp**行为相同，只是**wcscmp**在比较它们之前不会将其参数转换为小写。 **_mbsicmp**和 **_mbscmp**行为相同，只是 **_mbscmp**在比较它们之前不会将其参数转换为小写。

您需要调用[setlocale](setlocale-wsetlocale.md) **_wcsicmp**才能使用拉丁字符 1 个字符。 默认情况下，C 区域设置有效，因此，例如，_ 不会与 +进行比较。 调用**集区域设置**，在调用 **_wcsicmp**之前，除了 C 区域设置外的任何区域设置。 以下示例演示**了_wcsicmp**对区域设置的敏感性：

```C
// crt_stricmp_locale.c
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

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

另一种方法是调用[_create_locale，_wcreate_locale](create-locale-wcreate-locale.md)并将返回的区域设置对象作为参数传递给 **_wcsicmp_l**。

所有这些函数都验证其参数。 如果*string1*或*string2*都是空指针，则调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，这些函数将**返回_NLSCMPERROR**并将**errno**设置为**EINVAL**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_stricmp**， **_stricmp_l**|\<string.h>|
|**_wcsicmp**， **_wcsicmp_l**|\<string.h> 或 \<wchar.h>|
|**_mbsicmp**， **_mbsicmp_l**|\<mbstring.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

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
