---
title: "区域设置 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
caps.latest.revision: 16
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 748d880d8b00a1d9576a70e79b45cdc66a878e72
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="locale"></a>区域设置
区域设置指你可以用来自定义程序的国家/地区和语言设置。 一些与区域设置相关的类别包括日期和货币值的显示格式。 有关详细信息，请参阅[区域设置类别](../c-runtime-library/locale-categories.md)。  
  
 在使用不带 `_l` 后缀的函数时，可使用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函数来更改或查询当前的程序或线程区域设置信息的一部分或全部。 带有 `_l` 后缀的函数仅在其执行过程中使用传入的区域设置参数来获取区域设置信息。 若要创建用于带有 `_l` 后缀的函数的区域设置，请使用 [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)。 若要释放此区域设置，请使用 [_free_locale](../c-runtime-library/reference/free-locale.md)。 若要获取当前区域设置，请使用 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md).。  
  
 使用 [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 可控制是每个线程都有自己的区域设置，还是程序中的所有线程都共享同一区域设置。 有关详细信息，请参阅[区域设置和代码页](../text/locales-and-code-pages.md)。  
  
 下表中的函数还有更安全的版本，由 `_s`（“secure”）后缀指示。 有关详细信息，请参阅 [CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。  
  
### <a name="locale-dependent-routines"></a>与区域设置相关的例程  
  
|例程|使用|`setlocale` 类别设置依赖项|  
|-------------|---------|---------------------------------------------|  
|[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将字符转换为浮点值|`LC_NUMERIC`|  
|[atoi、_atoi_l、_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|将字符转换为整数值|`LC_NUMERIC`|  
|[_atoi64、_atoi64_l、_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|将字符转换为 64 位整数值|`LC_NUMERIC`|  
|[ato、_atol_l、_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|将字符转换为长值|`LC_NUMERIC`|  
|[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|将字符转换为长双精度值|`LC_NUMERIC`|  
|[is 例程](../c-runtime-library/is-isw-routines.md)|针对特定条件测试给定整数。|`LC_CTYPE`|  
|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|测试前导字节|`LC_CTYPE`|  
|[localeconv](../c-runtime-library/reference/localeconv.md)|读取合适的值来格式化数字量|`LC_MONETARY, LC_NUMERIC`|  
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|当前区域设置中任何多字节字符的最大长度（字节数）（STDLIB.H 中定义的宏）|`LC_CTYPE`|  
|[_mbccpy、_mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md)、[_mbccpy_s、_mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|复制一个多字节字符|`LC_CTYPE`|  
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|验证并返回多字节字符中的字节数|`LC_CTYPE`|  
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|对于多字节字符串：验证字符串中的每个字符；返回字符串的长度|`LC_CTYPE`|  
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为对应的宽字符序列|`LC_CTYPE`|  
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为对应的宽字符|`LC_CTYPE`|  
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函数|写入格式化的输出|`LC_NUMERIC`（确定基数字符输出）|  
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函数|读取格式化的输入|`LC_NUMERIC` (确定基数字符标识)|  
|[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|选择程序的区域设置|不适用|  
|[strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|比较两个字符串的字符|`LC_COLLATE`|  
|[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|比较两个字符串（不考虑大小写）|`LC_CTYPE`|  
|[_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|比较两个字符串的字符（不区分大小写）|`LC_COLLATE`|  
|[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|比较两个字符串的第一个 `n` 字符|`LC_COLLATE`|  
|[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|比较两个字符串的字符（不考虑大小写）。|`LC_CTYPE`|  
|[_strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|比较两个字符串的第一个 `n` 字符（不区分大小写）|`LC_COLLATE`|  
|[strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|根据提供的 `format` 参数设置日期和时间值的格式|`LC_TIME`|  
|[_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)，[_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|将给定字符串中的每个大写字母就地转换为小写字母|`LC_CTYPE`|  
|[strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|将字符串转换为 `double` 值|`LC_NUMERIC` (确定基数字符标识)|  
|[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|将字符串转换为 `long` 值|`LC_NUMERIC` (确定基数字符标识)|  
|[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|将字符串转换为无符号长值|`LC_NUMERIC` (确定基数字符标识)|  
|[_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)，[_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|将字符串的每个小写字母就地转换为大写字母|`LC_CTYPE`|  
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|根据区域设置将字符串转换为排序格式|`LC_COLLATE`|  
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)，[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|将给定的字符转换为相应的小写字母|`LC_CTYPE`|  
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)，[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|将给定的字符转换为相应的大写字母|`LC_CTYPE`|  
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)，[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符序列转换为相应的多字节字符序列|`LC_CTYPE`|  
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)，[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|`LC_CTYPE`|  
  
> [!NOTE]
>  对于多字节例程，多字节代码页必须与使用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 设置的区域设置等效。 带有 `_MB_CP_LOCALE` 参数的 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 使多字节代码页与 `setlocale` 代码页相同。  
  
## <a name="see-also"></a>另请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
