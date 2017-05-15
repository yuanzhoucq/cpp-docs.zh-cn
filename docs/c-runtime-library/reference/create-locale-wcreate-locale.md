---
title: "_create_locale、_wcreate_locale | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: 5068d509e335fd99246d5dff5fd51f2b0b1493b6
ms.contentlocale: zh-cn
ms.lasthandoff: 02/28/2017

---
# <a name="createlocale-wcreatelocale"></a>_create_locale、_wcreate_locale
创建区域设置对象。  
  
## <a name="syntax"></a>语法  
  
```  
_locale_t _create_locale(  
   int category,  
   const char *locale   
);  
_locale_t _wcreate_locale(  
   int category,  
   const wchar_t *locale   
);  
```  
  
#### <a name="parameters"></a>参数  
 `category`  
 类别。  
  
 `locale`  
 区域设置说明符。  
  
## <a name="return-value"></a>返回值  
 如果给定了有效的 `locale` 和 `category`则返回指定区域设置作为 `_locale_t` 对象。 不更改程序的当前区域设置。  
  
## <a name="remarks"></a>备注  
 `_create_locale` 函数允许创建表示某个特定于区域的设置的对象，以供许多特定于区域设置版本的 CRT 函数（具有 `_l` 后缀的函数）使用。 行为类似于 `setlocale`但将设置保存在返回的 `_locale_t` 结构中，而不是向当前环境应用指定的区域设置。 不再需要 `_locale_t` 结构时，应使用 [_free_locale](../../c-runtime-library/reference/free-locale.md) 将其释放。  
  
 `_wcreate_locale` 是 `_create_locale` 的宽字符版本；`locale` 的 `_wcreate_locale` 参数是宽字符字符串。 除此以外，`_wcreate_locale` 和 `_create_locale` 的行为完全相同。  
  
 `category` 参数指定受影响的特定于区域设置的行为部分。 用于 `category` 的标志及其影响的程序部分如下表中所示。  
  
 `LC_ALL`  
 以下列出了所有类别。  
  
 `LC_COLLATE`  
 `strcoll`、`_stricoll`、`wcscoll`、`_wcsicoll`、`strxfrm`、`_strncoll`、`_strnicoll`、`_wcsncoll`、`_wcsnicoll` 和 `wcsxfrm` 函数。  
  
 `LC_CTYPE`  
 字符处理函数（不受影响的 `isdigit`、`isxdigit`、`mbstowcs` 和 `mbtowc` 除外）。  
  
 `LC_MONETARY`  
 `localeconv` 函数返回的货币格式信息。  
  
 `LC_NUMERIC`  
 格式化输出例程（例如 `printf`）、数据转换例程和 `localeconv` 所返回的非货币格式设置信息的十进制点字符。 除小数点字符之外，`LC_NUMERIC` 还设置 [localeconv](../../c-runtime-library/reference/localeconv.md) 返回的千位分隔符和分组控制字符串。  
  
 `LC_TIME`  
 `strftime` 和 `wcsftime` 函数。  
  
 此函数验证 `category` 和 `locale` 参数。 如果类别参数不是上表中给定的值之一，或者如果 `locale` 是 `NULL`，则该函数将返回 `NULL`。  
  
 `locale` 参数是指向指定区域设置的字符串的指针。 有关 `locale` 参数的格式信息，请参阅[区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。  
  
 `locale` 参数可以采用区域设置名称、语言字符串、语言字符串和国家/地区代码、代码页或语言字符串、国家/地区代码和代码页。 可用区域设置名称、语言、国家/地区代码和代码页集包含 Windows NLS API 支持的所有内容，要求每个字符对应两个以上的字节的代码页除外（例如，UTF-7 和 UTF-8）。 如果提供诸如 UTF-7 或 UTF-8 的代码页，则 `_create_locale` 将失败并返回 NULL。 [区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)中介绍了 `_create_locale` 所支持的区域设置名称集合。 [语言字符串](../../c-runtime-library/language-strings.md)和[国家/地区字符串](../../c-runtime-library/country-region-strings.md)中列出了 `_create_locale` 所支持的语言和国家/地区字符串集合。  
  
 有关区域设置的详细信息，请参阅[setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 已弃用此函数之前的名称 `__create_locale`（带两个前导下划线）。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_create_locale`|\<locale.h>|  
|`_wcreate_locale`|\<locale.h> 或 \<wchar.h>|  
  
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
 [区域设置名称、语言和国家/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [语言字符串](../../c-runtime-library/language-strings.md)   
 [国家/地区字符串 ](../../c-runtime-library/country-region-strings.md)  
 [_free_locale](../../c-runtime-library/reference/free-locale.md)   
 [_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [setlocale、_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)
