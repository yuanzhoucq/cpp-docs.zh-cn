---
title: "数据转换 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
caps.latest.revision: 12
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
translationtype: Human Translation
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: 466085ab36a977cbd7bf412b01d0803e46d04807
ms.lasthandoff: 02/28/2017

---
# <a name="data-conversion"></a>数据转换
这些例程可将数据从一种形式转换为另一种形式。 通常，这些例程比可能编写的转换执行速度更快。 每个以 `to` 前缀开头的例程都作为函数和宏实现。 请参阅[在函数和宏之间选择](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)，了解关于选择实现的信息。  
  
### <a name="data-conversion-routines"></a>数据转换例程  
  
|例程|使用|.NET Framework 等效项|  
|-------------|---------|-------------------------------|  
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|查找整数的绝对值|[System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将字符串转换为 `float`|[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi、_atoi_l、_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|将字符串转换为 `int`|[System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)、[System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[_atoi64、_atoi64_l、_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|将字符串转换为 `__int64`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)、[System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[ato、_atol_l、_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|将字符串转换为 `long`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)、[System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[_ecvt](../c-runtime-library/reference/ecvt.md)、[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|将 `double` 转换为指定长度的字符串|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_fcvt](../c-runtime-library/reference/fcvt.md)、[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|将 `double` 转换为小数点后具有指定位数的字符串|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_gcvt](../c-runtime-library/reference/gcvt.md)、[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|将 `double` 数字转换为字符串；将字符串存储于缓存分区中|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)、[_itoa_s、_i64toa_s、_ui64toa_s、_itow_s、_i64tow_s、_ui64tow_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|将 `int` 或 `__int64` 转换为字符串|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|查找 `long` 整数的绝对值|[System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|查找 `long long` 整数的绝对值|[System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[_ltoa、_ltow](../c-runtime-library/reference/ltoa-ltow.md)、[_ltoa_s、_ltow_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|将 `long` 转换为字符串|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_mbbtombc、_mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|将 1 字节多字节字符转换为相应的 2 字节多字节字符|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|将日本行业标准 (JIS) 字符转换为日本 Microsoft (JMS) 字符|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|将 JMS 字符转换为 JIS 字符|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|将多字节字符转换为 1 字节平假名代码|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|将多字节字符转换为 1 字节片假名代码|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_mbctombb、_mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|将 2 字节多字节字符转换为相应的 1 字节多字节字符|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为对应的宽字符序列|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为对应的宽字符|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|将字符串转换为 `double`|[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|将字符串转换为 `long` 整数|[System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)|  
|[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|将字符串转换为 `unsigned long` 整数|[System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|根据特定于区域设置的信息将字符串转换为排序格式|[System::IFormattable::ToString](https://msdn.microsoft.com/en-us/library/system.iformattable.tostring.aspx)|  
|[toascii、__toascii](../c-runtime-library/reference/toascii-toascii.md)|将字符转换为 ASCII 代码||  
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|测试字符，并且如果当前为大写形式，将其转换为小写形式|[System::Char::ToLower](https://msdn.microsoft.com/en-us/library/system.char.tolower.aspx)|  
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|无条件将字符转换为小写形式|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|  
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|测试字符，并且如果当前为小写形式，将其转换为大写形式|[System::Char::ToUpper](https://msdn.microsoft.com/en-us/library/system.char.toupper.aspx)|  
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|无条件将字符转换为大写形式|[System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)|  
|[_ultoa、_ultow](../c-runtime-library/reference/ultoa-ultow.md)、[_ultoa_s、_ultow_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|将 `unsigned long` 转换为字符串|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符序列转换为相应的多字节字符序列|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|将宽字符字符串转换为 `double`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)、[System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)、[System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)、[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi、_atoi_l、_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|将宽字符字符串转换为 `int`|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_atoi64、_atoi64_l、_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|将宽字符字符串转换为 `__int64`|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[ato、_atol_l、_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|将宽字符字符串转换为 `long`|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)
