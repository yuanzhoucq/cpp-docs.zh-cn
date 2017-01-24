---
title: "区域设置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.international"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "国家/地区信息"
  - "语言信息例程"
  - "区域设置例程"
  - "本地化, 区域设置"
  - "setlocale 函数"
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 区域设置
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*区域设置*是指您可以用来自定义程序的国家\/地区和语言设置。  一些区域设置相关的类别包括日期和货币值的显示格式。  有关详细信息，请参阅[区域设置类别](../c-runtime-library/locale-categories.md)。  
  
 当使用函数，而无需 `_l` 后缀时，请使用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函数更改或查询部分或全部当前程序或线程区域设置信息。  带有 `_l` 后缀的函数将使用仅在该特定函数的执行过程中传递的区域设置信息区域设置参数。  用带有 `_l` 后缀的函数创建一个区域设置用于，请使用 [\_create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)。  若要释放该区域设置，请使用 [\_free\_locale](../c-runtime-library/reference/free-locale.md)。  若要获取当前区域设置，请使用 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)。  
  
 使用 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 控制每个线程是否有其自己的区域设置，或者在程序中的所有线程共享同一区域设置。  有关详细信息，请参阅 [区域设置和代码页](../text/locales-and-code-pages.md)。  
  
 函数的更安全版本可用在下面表格中显示，由 `_s` \(“安全”\) 后缀表示。  有关详细信息，请参阅[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。  
  
### 与区域设置相关的例程  
  
|例程|用途|`setlocale` 分类设置依赖项|  
|--------|--------|-------------------------|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将字符转换为浮点值|`LC_NUMERIC`|  
|[atoi、\_atoi\_l、\_wtoi、\_wtoi\_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|将字符转换为整数值|`LC_NUMERIC`|  
|[\_atoi64、\_atoi64\_l、\_wtoi64、\_wtoi64\_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|将字符转换为 64 位整数值|`LC_NUMERIC`|  
|[ato，\_atol\_l，\_wtol，\_wtol\_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|将字符转换为长整数值|`LC_NUMERIC`|  
|[\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|将字符转换为双长整数值|`LC_NUMERIC`|  
|[是例程](../c-runtime-library/is-isw-routines.md)|测试特定条件的特定整数。|`LC_CTYPE`|  
|[isleadbyte、\_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|测试前导字节|`LC_CTYPE`|  
|[localeconv](../c-runtime-library/reference/localeconv.md)|读取适当的值来格式化数字量|`LC_MONETARY, LC_NUMERIC`|  
|[MB\_CUR\_MAX](../c-runtime-library/mb-cur-max.md)|在当前区域设置中任何多字节字符的最大字节长度（在 STDLIB.H定义的宏\)|`LC_CTYPE`|  
|[\_mbccpy、\_mbccpy\_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[\_mbccpy\_s、\_mbccpy\_s\_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|复制一个多字节字符|`LC_CTYPE`|  
|[\_mbclen、mblen、\_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|验证并返回在多字节字符的字节数|`LC_CTYPE`|  
|[strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|对于多字节字符字符串：验证在字符串中的每个字符；返回字符串的长度|`LC_CTYPE`|  
|[mbstowcs、\_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为宽字符的对应序列|`LC_CTYPE`|  
|[mbtowc、\_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为相应的宽字符|`LC_CTYPE`|  
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函数|编写格式化的输出|`LC_NUMERIC` \(确定基数字符输出\)|  
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函数|读取格式化的输入|`LC_NUMERIC` \(确定基数字符标识\)|  
|[setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|为程序选择区域设置|不适用|  
|[strcoll、wcscoll、\_mbscoll、\_strcoll\_l、\_wcscoll\_l、\_mbscoll\_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|比较两个字符串的字符|`LC_COLLATE`|  
|[\_stricmp、\_wcsicmp、\_mbsicmp、\_stricmp\_l、\_wcsicmp\_l、\_mbsicmp\_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|比较两个字符串不需要考虑用例|`LC_CTYPE`|  
|[\_stricoll、\_wcsicoll、\_mbsicoll、\_stricoll\_l、\_wcsicoll\_l、\_mbsicoll\_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|比较两个字符串字符 \(不区分大小写\)|`LC_COLLATE`|  
|[\_strncoll、\_wcsncoll、\_mbsncoll、\_strncoll\_l、\_wcsncoll\_l、\_mbsncoll\_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|比较两个字符串的第一个 `n` 字符|`LC_COLLATE`|  
|[\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|比较两个字符串字符不考虑大小写。|`LC_CTYPE`|  
|[\_strnicoll、\_wcsnicoll、\_mbsnicoll、\_strnicoll\_l、\_wcsnicoll\_l、\_mbsnicoll\_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|比较两个字符串的第一个`n`字符 \(不区分大小写\)|`LC_COLLATE`|  
|[strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|根据所提供的 `format` 自变量设置日期和时间值的形式|`LC_TIME`|  
|[\_strlwr、\_wcslwr、\_mbslwr、\_strlwr\_l、\_wcslwr\_l、\_mbslwr\_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[\_strlwr\_s、\_strlwr\_s\_l、\_mbslwr\_s、\_mbslwr\_s\_l、\_wcslwr\_s、\_wcslwr\_s\_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|转换，例如，把特定字符串的每个大写字母转换为小写|`LC_CTYPE`|  
|[strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|将字符字符串转换为 `double` 值的字符串。|`LC_NUMERIC` \(确定基数字符标识\)|  
|[strtol、wcstol、\_strtol\_l、\_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|将字符字符串转换为 `long` 值的字符串。|`LC_NUMERIC` \(确定基数字符标识\)|  
|[strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|将字符字符串转换为无符号长整数值|`LC_NUMERIC` \(确定基数字符标识\)|  
|[\_strupr、\_strupr\_l、\_mbsupr、\_mbsupr\_l、\_wcsupr\_l、\_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[\_strupr\_s、\_strupr\_s\_l、\_mbsupr\_s、\_mbsupr\_s\_l、\_wcsupr\_s、\_wcsupr\_s\_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|转换，例如，把字符串的每个小写字母转换为大写|`LC_CTYPE`|  
|[strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|根据窗体区域设置，将字符串转换为列形式|`LC_COLLATE`|  
|[tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|将特定的字符转换为相应的小写字母|`LC_CTYPE`|  
|[toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|将特定的字符转换为相应的大写字母|`LC_CTYPE`|  
|[wcstombs、\_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符序列转换为多字节字符的对应序列|`LC_CTYPE`|  
|[wctomb、\_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb\_s、\_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|`LC_CTYPE`|  
  
> [!NOTE]
>  对于多字节实例，多字节代码页必须等效于区域设置设有 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  [\_setmbcp](../c-runtime-library/reference/setmbcp.md)，与 `_MB_CP_LOCALE` 的参数使多字节代码页与 `setlocale` 代码页相同。  
  
## 请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)