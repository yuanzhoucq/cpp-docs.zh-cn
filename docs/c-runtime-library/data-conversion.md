---
title: 数据转换
ms.date: 03/21/2018
f1_keywords:
- c.conversions
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
ms.openlocfilehash: 80acfefa7368d293b466230a26b6a609597166fe
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331147"
---
# <a name="data-conversion"></a>数据转换

这些例程可将数据从一种形式转换为另一种形式。 通常，这些例程比可能编写的转换执行速度更快。 每个以 to 前缀开头的例程都作为函数和宏实现。 请参阅[在函数和宏之间选择](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)，了解关于选择实现的信息。

## <a name="data-conversion-routines"></a>数据转换例程

|例程所返回的值|使用|
|-------------|---------|
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|查找整数的绝对值|
|[atof、_atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将字符串转换为单精度浮点型|
|[atoi、_atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|将字符串转换为整型|
|[_atoi64、_atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|将字符串转换为 __int64 型或超长整型|
|[atol、_atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|将字符串转换为长整型|
|[c16rtomb、c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|将 UTF-16 或 UTF-32 字符转换为等效多字节字符|
|[_ecvt](../c-runtime-library/reference/ecvt.md)、[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|将双精度浮点型转换为指定长度的字符串|
|[_fcvt](../c-runtime-library/reference/fcvt.md)、[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|将双精度浮点型转换为小数点后具有指定位数的字符串|
|[_gcvt](../c-runtime-library/reference/gcvt.md)、[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|将双精度浮点型数字转换为字符串；将字符串存储于缓存分区中|
|[_itoa、_ltoa、_ultoa、_i64toa、_ui64toa、_itow、_ltow、ultow、_i64tow、_ui64tow](../c-runtime-library/reference/itoa-itow.md)、[_itoa_s、_ltoa_s、_ultoa_s、_i64toa_s、_ui64toa_s、_itow_s、_ltow_s、_ultow_s、_i64tow_s、_ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|将整数类型转换为字符串|
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|查找长整型整数的绝对值|
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|查找超长整型整数的绝对值|
|[_mbbtombc、_mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|将 1 字节多字节字符转换为相应的 2 字节多字节字符|
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|将日本行业标准 (JIS) 字符转换为日本 Microsoft (JMS) 字符|
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|将 JMS 字符转换为 JIS 字符|
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|将多字节字符转换为 1 字节平假名代码|
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|将多字节字符转换为 1 字节片假名代码|
|[_mbctombb、_mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|将 2 字节多字节字符转换为相应的 1 字节多字节字符|
|[mbrtoc16、mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|将多字节字符转换为等效 UTF-16 或 UTF-32 字符|
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为对应的宽字符序列|
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为对应的宽字符|
|[strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|将字符串转换为双精度浮点型。|
|[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|将字符串转换为长整型整数|
|[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|将字符串转换为无符号长整型整数|
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|根据特定于区域设置的信息将字符串转换为排序格式|
|[toascii、__toascii](../c-runtime-library/reference/toascii-toascii.md)|将字符转换为 ASCII 代码|
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|测试字符，并且如果当前为大写形式，将其转换为小写形式|
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|无条件将字符转换为小写形式|[System::String::ToLower](https://msdn.microsoft.com/library/system.string.tolower.aspx)|
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|测试字符，并且如果当前为小写形式，将其转换为大写形式|
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|无条件将字符转换为大写形式|
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符序列转换为相应的多字节字符序列|
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|
|[_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将宽字符字符串转换为双精度浮点型|
|[_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|将宽字符字符串转换为整型|
|[_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|将宽字符字符串转换为 __int64 型或超长整型|
|[_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|将宽字符字符串转换为长整型|

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
