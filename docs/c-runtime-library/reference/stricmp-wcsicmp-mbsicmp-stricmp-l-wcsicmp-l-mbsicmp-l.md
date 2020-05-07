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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 786c2bd2738bb82b3edac5c811ccfd3f9f8bc854
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920012"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l

执行不区分大小写的字符串比较。

> [!IMPORTANT]
> 不能在 Windows 运行时中执行的应用程序中使用 **_mbsicmp**和 **_mbsicmp_l** 。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

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

*string1*、 *string2*<br/>
要比较的 null 终止的字符串。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

返回值指示*string1*与*string2*的关系，如下所示。

|返回值|说明|
|------------------|-----------------|
|< 0|*string1*小于*string2*|
|0|*string1*等于*string2*|
|> 0|*string1*大于*string2*|

出现错误时， **_mbsicmp**返回在 string .h> 和\<mbstring.h \<> 中定义 **_NLSCMPERROR**。

## <a name="remarks"></a>备注

**_Stricmp**函数按序号在将每个字符转换为小写后比较*string1*和*string2* ，并返回一个指示它们关系的值。 **_stricmp**与 **_stricoll**的不同之处在于， **_stricmp**比较仅受**LC_CTYPE**影响，这将确定哪些字符是大写和小写字符。 **_Stricoll**函数根据区域设置的**LC_CTYPE**和**LC_COLLATE**类别来比较字符串，其中包括大小写和排序规则顺序。 有关 " **LC_COLLATE** " 类别的详细信息，请参阅[Setlocale](setlocale-wsetlocale.md)和[区域设置类别](../../c-runtime-library/locale-categories.md)。 这些不带 **_l**后缀的函数的版本对与区域设置相关的行为使用当前区域设置。 带后缀的版本是相同的，只不过它们转而使用传入的区域设置。 如果尚未设置区域设置，则使用 C 区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

> [!NOTE]
> **_stricmp**等效于 **_strcmpi**。 它们可以互换使用，但 **_stricmp**是首选标准。

**_Strcmpi**函数等效于 **_stricmp**并且提供仅用于向后兼容性。

因为 **_stricmp**执行小写比较，所以它可能会导致意外的行为。

为了说明 **_stricmp**的 case 转换如何影响比较的结果，假定您有两个字符串在约翰上并且 JOHN_HENRY。 字符串 JOHN_HENRY 被视为小于 JOHNSTON，因为“_”的 ASCII 值小于小写的 S。实际上，ASCII 值介于 91 和 96 之间的任何字符都将被视为小于任何字母。

如果使用[strcmp](strcmp-wcscmp-mbscmp.md)函数而不是 **_stricmp**，JOHN_HENRY 将大于约翰。

**_wcsicmp**和 **_mbsicmp**是 **_stricmp**的宽字符和多字节字符版本。 **_Wcsicmp**的参数和返回值都是宽字符字符串;**_mbsicmp**的是多字节字符字符串。 **_mbsicmp**根据当前的多字节代码页识别多字节字符序列，并在发生错误时返回 **_NLSCMPERROR** 。 有关详细信息，请参阅[代码页](../../c-runtime-library/code-pages.md)。 否则这三个函数否则具有相同行为。

**_wcsicmp**和**wcscmp**的行为相同，只是**wcscmp**在比较它们之前不会将其参数转换为小写。 **_mbsicmp**和 **_mbscmp**的行为是相同的，但在比较它们之前， **_mbscmp**不会将其参数转换为小写。

需要调用[setlocale](setlocale-wsetlocale.md) ，以便 **_wcsicmp**使用拉丁语1个字符。 默认情况下，C 区域设置是有效的，因此，例如，ä的比较结果不等于Ä。 调用 **_wcsicmp**之前，请先在 C 区域设置以外的任何区域设置调用**setlocale** 。 下面的示例演示 **_wcsicmp**对区域设置的区分方式：

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

一种替代方法是调用[_create_locale，_wcreate_locale](create-locale-wcreate-locale.md)并将返回的区域设置对象作为参数传递给 **_wcsicmp_l**。

所有这些函数都验证其参数。 如果*string1*或*string2*为 null 指针，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 **_NLSCMPERROR** ，并将**Errno**设置为**EINVAL**。

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
