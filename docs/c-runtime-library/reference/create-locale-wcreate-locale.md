---
title: "_create_locale、_wcreate_locale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_create_locale"
  - "__create_locale"
  - "_wcreate_locale"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "create_locale"
  - "_create_locale"
  - "__create_locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__create_locale 函数"
  - "_create_locale 函数"
  - "create_locale 函数"
  - "区域设置, 创建"
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _create_locale、_wcreate_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建一个区域设置对象。  
  
## 语法  
  
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
  
#### 参数  
 `category`  
 分类  
  
 `locale`  
 区域设置说明符。  
  
## 返回值  
 如果给定有效的 `locale` 和 `category`，返回指定的区域设置作为 `_locale_t` 对象。  不更改程序的当前区域设置。  
  
## 备注  
 `_create_locale` 功能在许多 CRT 函数 \(与 `_l` 后缀的功能\) 区域设置特定版本中允许您创建具有某些特定区域设置的对象。  该行为类似于 `setlocale`，除此之外，而不是应用针对当前环境指定的区域设置，该设置保存在已返回的 `_locale_t` 结构。  不必要时，释放 `_locale_t` 结构通过使用[\_free\_locale](../../c-runtime-library/reference/free-locale.md)。  
  
 `_wcreate_locale` 是 `_create_locale` 的宽字符版本；`_wcreate_locale` 的 `locale` 参数是宽字符字符串。  否则`_wcreate_locale` 和 `_create_locale` 行为相同。  
  
 `category` 参数指定受影响该特定区域行为的一部分。  用于 `category` 的标志，受它们影响的部分程序如下表所示。  
  
 `LC_ALL`  
 所有类别，如下所示。  
  
 `LC_COLLATE`  
 `strcoll`、 `_stricoll`, `wcscoll`、`_wcsicoll`、 `strxfrm`、 `_strncoll`、 `_strnicoll`、`_wcsncoll`、 `_wcsnicoll` 和 `wcsxfrm` 函数。  
  
 `LC_CTYPE`  
 字符处理函数 \(除 `isdigit`、`isxdigit`、`mbstowcs`和 `mbtowc`不受影响\)。  
  
 `LC_MONETARY`  
 `localeconv` 函数返回货币格式信息。  
  
 `LC_NUMERIC`  
 十进制点字符格式化输出实例 \(例如 `printf`\)，数据转换实例和对于 `localeconv`返回的非货币的格式设置信息。  除小数点点字符之外，`LC_NUMERIC` 设置的千位分隔符和分组控件字符串返回的[localeconv](../../c-runtime-library/reference/localeconv.md)。  
  
 `LC_TIME`  
 `strftime`和 `wcsftime` 函数。  
  
 此函数验证 `category` 和 `locale` 参数.  如果类别参数不是前面表中提供的一个值，或者 `locale` 是 `NULL`，则函数返回 `NULL`。  
  
 `locale` 参数是指向指定区域设置的字符串指针。  有关 `locale` 参数的格式的信息，请参阅 [区域设置名称、语言和国家\/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。  
  
 `locale` 自变量可以采用区域设置名称、语言字符串、语言字符串和国家\/地区代码、代码页或语言字符串、国家\/地区代码和代码页。  可用区域设置名称、语言、国家\/地区代码和代码页的设置包含除代码页需要每个字符多于两个字节，例如 UTF\-7、UTF\-8 的代码页外的所有被Windows NLS API 支持的。  如果您提供像 UTF\-7 或 UTF\-8 的代码页，`_create_locale` 将失败并返回 null。  设置 `_create_locale` 支持的区域设置名称，如 [区域设置名称、语言和国家\/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) 所述。  通过 `_create_locale` 支持的设置语言和国家\/地区字符串列在 [语言字符串](../../c-runtime-library/language-strings.md) 和 [国家\/地区字符串](../../c-runtime-library/country-region-strings.md)。  
  
 有关这些设置的更多信息，请参见[setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 `__create_locale`函数\(带有两个前导下划线）之前的名字已弃用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_create_locale`|\<locale.h\>|  
|`_wcreate_locale`|\<locale.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
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
       //  
       if (!_strftime_l((char *)str, 100, "%#x",   
                     (const struct tm *)&thetime, locale))  
               printf("_strftime_l failed!\n");  
       else  
               printf("In de-CH locale, _strftime_l returns '%s'\n",   
                      str);  
  
       _free_locale(locale);  
  
       // Create a locale object representing the default C locale  
       locale = _create_locale(LC_ALL, "C");  
       time (&ltime);  
       _gmtime64_s(&thetime, &ltime);  
  
       if (!_strftime_l((char *)str, 100, "%#x",   
                     (const struct tm *)&thetime, locale))  
               printf("_strftime_l failed!\n");  
       else  
               printf("In 'C' locale, _strftime_l returns '%s'\n",   
                      str);  
  
       _free_locale(locale);  
}  
```  
  
## 示例输出  
  
```  
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'  
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'  
```  
  
## .NET Framework 等效项  
 [System::Globalization::CultureInfo Class](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)  
  
## 请参阅  
 [区域设置名称、语言和国家\/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [语言字符串](../../c-runtime-library/language-strings.md)   
 [国家\/地区字符串](../../c-runtime-library/country-region-strings.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)   
 [\_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函数](../../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)