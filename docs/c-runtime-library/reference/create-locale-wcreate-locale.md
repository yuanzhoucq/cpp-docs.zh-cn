---
title: _create_locale、_wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 611eaf342776b9a0f57c4f55c52a841c3fd13fb5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348258"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale、_wcreate_locale

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

*类别*<br/>
类别。

*现场*<br/>
区域设置说明符。

## <a name="return-value"></a>返回值

如果提供了有效的*区域设置*和*类别*，则返回指定的区域设置作为 **_locale_t**对象。 不更改程序的当前区域设置。

## <a name="remarks"></a>备注

**_create_locale**函数允许您创建表示特定区域设置的对象，以便在许多 CRT 函数的区域设置特定版本中使用（具有 **_l**后缀的函数）。 该行为类似于**setlocale，** 只不过，这些设置不是将指定的区域设置应用于当前环境，而是保存在返回 **_locale_t**结构中。 当不再需要 **_locale_t**结构时，应使用[_free_locale](free-locale.md)释放结构。

**_wcreate_locale**是 **_create_locale**的宽字符版本;到 **_wcreate_locale***区域设置*参数是宽字符字符串。 **_wcreate_locale**和 **_create_locale**行为相同。

*类别*参数指定受影响的特定于区域设置的行为的部分。 用于*类别*的标志及其影响的程序部分如下表所示：

| *类别*标志 | 影响 |
|-----------------|---------|
| **LC_ALL** |以下列出了所有类别。 |
| LC_COLLATE**** |**斯特科尔****，_stricoll，wcscoll，_wcsicoll，****斯特克斯弗姆****_stricoll****_wcsicoll**，_strncoll，_strnicoll，_wcsncoll，_wcsnicoll，和**wcsxfrm**功能。 **_strncoll** **_strnicoll** **_wcsncoll** **_wcsnicoll** |
| LC_CTYPE**** | 字符处理函数（除**数字****、isxdigit、mbstowcs**和**mbtowc**（未受影响） **mbstowcs** |
| **LC_MONETARY** | **本地 econv**函数返回的货币格式信息。 |
| LC_NUMERIC**** | 格式化的输出例程（如**printf**）的数据转换例程和**localeconv**返回的非货币格式信息的十进制点字符。 除了小数点字符外 **，LC_NUMERIC**设置数千分隔符和[由 localeconv](localeconv.md)返回的分组控制字符串。 |
| LC_TIME**** | **稳时**和**wcsftime**函数。 |

此函数验证*类别*和*区域设置*参数。 如果类别参数不是上表中给出的值之一，或者如果*区域设置*为**NULL，** 则函数将返回**NULL**。

*区域设置*参数是指向指定区域设置的字符串的指针。 有关*区域设置*参数格式的信息，请参阅[区域设置名称、语言和国家/区域字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。

*区域设置*参数可以采用区域设置名称、语言字符串、语言字符串和国家/地区代码、代码页或语言字符串、国家/区域代码和代码页。 可用的区域设置名称、语言、国家/地区代码和代码页集包括 Windows NLS API 支持的所有区域设置名称、 语言/区域代码和代码页。 **_create_locale**支持的区域设置名称集在[区域设置名称、语言和国家/区域字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中描述。 **_create_locale**支持的语言和国家/区域字符串集列在[语言字符串](../../c-runtime-library/language-strings.md)和国家[/区域字符串](../../c-runtime-library/country-region-strings.md)中。

有关区域设置的详细信息，请参阅[setlocale、_wsetlocale](setlocale-wsetlocale.md)。

此函数的前一个名称 **__create_locale（** 具有两个前导下划线）已被弃用。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[区域设置名称、语言和国家/区域字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[语言字符串](../../c-runtime-library/language-strings.md)<br/>
[国家/地区字符串](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[现场](../../c-runtime-library/locale.md)<br/>
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
