---
title: _create_locale、_wcreate_locale
ms.date: 11/04/2016
apiname:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: 0ede14d56dc093b83078bf28eb01f5b5c55d8949
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545920"
---
# <a name="createlocale-wcreatelocale"></a>_create_locale、_wcreate_locale

创建区域设置对象。

## <a name="syntax"></a>语法

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>参数

*category*<br/>
类别。

*locale*<br/>
区域设置说明符。

## <a name="return-value"></a>返回值

如果提供了有效*区域设置*并*类别*，则返回指定的区域设置作为 **_locale_t**对象。 不更改程序的当前区域设置。

## <a name="remarks"></a>备注

**_Create_locale**功能，您可以创建一个对象，表示某些特定于区域设置，以便在很多 CRT 函数的特定于区域设置的版本中使用 (使用函数 **_l**后缀). 行为是类似于**setlocale**，只不过而不是将指定的区域设置设置应用于当前环境，这些设置保存在 **_locale_t**返回的结构。 **_Locale_t**应使用释放结构[_free_locale](free-locale.md)不再需要时。

**_wcreate_locale**是宽字符版本 **_create_locale**;*区域设置*参数 **_wcreate_locale**是宽字符字符串。 **_wcreate_locale**并 **_create_locale**行为相同。

*类别*参数指定受影响的特定于区域设置的行为部分。 有关使用的标志*类别*和及其影响的程序的部分是下表中所示。

|*类别*标志|影响|
|-|-|
**LC_ALL**|以下列出了所有类别。
LC_COLLATE|**Strcoll**， **_stricoll**， **wcscoll**， **_wcsicoll**， **strxfrm**， **_strncoll**， **_strnicoll**， **_wcsncoll**， **_wcsnicoll**，并且**wcsxfrm**函数。
LC_CTYPE|字符处理函数 (除**isdigit**， **isxdigit**， **mbstowcs**，以及**mbtowc**，不受影响)。
**LC_MONETARY**|返回的货币格式信息**localeconv**函数。
LC_NUMERIC|小数点字符格式化的输出例程 (如**printf**)、 数据转换例程，以及返回的非货币格式设置信息**localeconv**。 除小数点字符之外**LC_NUMERIC**集千位分隔符和分组控制返回字符串[localeconv](localeconv.md)。
LC_TIME|**Strftime**并**wcsftime**函数。

此函数验证*类别*并*区域设置*参数。 如果类别参数不是上表中给定的值之一，或如果*区域设置*是**NULL**，该函数将返回**NULL**。

*区域设置*参数是指向指定的区域设置的字符串。 有关格式的详细信息*区域设置*自变量，请参阅[区域设置名称、 语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。

*区域设置*参数可使用区域设置名称、 语言字符串、 语言字符串和国家/地区代码、 代码页或语言字符串、 国家/地区代码和代码页。 可用区域设置名称、语言、国家/地区代码和代码页集包含 Windows NLS API 支持的所有内容，要求每个字符对应两个以上的字节的代码页除外（例如，UTF-7 和 UTF-8）。 如果提供如 utf-7 或 utf-8 代码页 **_create_locale**将失败并且返回**NULL**。 支持的区域设置名称的一套 **_create_locale**中所述[区域设置名称、 语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。 支持的语言和国家/地区字符串的一套 **_create_locale**中列出[语言字符串](../../c-runtime-library/language-strings.md)并[国家/地区字符串](../../c-runtime-library/country-region-strings.md)。

有关区域设置的详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md)。

此函数的以前名称 **__create_locale** （带两个前导下划线），已被弃用。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>请参阅

[区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[语言字符串](../../c-runtime-library/language-strings.md)<br/>
[国家/地区字符串](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[区域设置](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll 函数](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
