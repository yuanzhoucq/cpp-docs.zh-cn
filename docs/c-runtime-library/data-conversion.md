---
title: "数据转换 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.conversions"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "转换数据"
  - "数据转换例程 [C++]"
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 数据转换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些实例将数据从一个转化到另一个。  通常这些实例比您编写的转换的执行速度更快。  以`to` 为前缀开头的每个实例都实现为函数和作为宏。  有关选择实现的信息，请参见 [选择在函数和宏](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)。  
  
### 数据转换例程  
  
|例程|用途|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|找出整数的绝对值|[\<caps:sentence id\="tgt11" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|把字符串转换为`float`|[\<caps:sentence id\="tgt13" sentenceid\="363f8f2cb09f8ca850491a65df66522e" class\="tgtSentence"\>System::Convert::ToDouble\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi、\_atoi\_l、\_wtoi、\_wtoi\_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|把字符串转换为`int`|[System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)，[System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[\_atoi64、\_atoi64\_l、\_wtoi64、\_wtoi64\_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|把字符串转换为`__int64`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)，[System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[ato，\_atol\_l，\_wtol，\_wtol\_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|把字符串转换为`long`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)，[System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[\_ecvt](../c-runtime-library/reference/ecvt.md), [\_ecvt\_s](../c-runtime-library/reference/ecvt-s.md)|转换`double`为指定长度的字符串|[\<caps:sentence id\="tgt22" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_fcvt](../c-runtime-library/reference/fcvt.md), [\_fcvt\_s](../c-runtime-library/reference/fcvt-s.md)|转换 `double` 为十进制小数点后指定位数的字符串|[\<caps:sentence id\="tgt25" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_gcvt](../c-runtime-library/reference/gcvt.md),[\_gcvt\_s](../c-runtime-library/reference/gcvt-s.md)|转换`double`数字为字符串;存储字符串在缓冲区|[\<caps:sentence id\="tgt28" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_itoa、\_i64toa、\_ui64toa、\_itow、\_i64tow、\_ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md), [\_itoa\_s、\_i64toa\_s、\_ui64toa\_s、\_itow\_s、\_i64tow\_s、\_ui64tow\_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|转换`int`或者`__int64`为字符串|[\<caps:sentence id\="tgt31" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[labs](../misc/labs-llabs.md)|找出整数`long` 的绝对值|[\<caps:sentence id\="tgt34" sentenceid\="9594ba199e25e9de6b463c8efc9fbe95" class\="tgtSentence"\>System::Math::Abs\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[\_ltoa、\_ltow](../c-runtime-library/reference/ltoa-ltow.md), [\_ltoa\_s、\_ltow\_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|转换`long`为字符串|[\<caps:sentence id\="tgt37" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[\_mbbtombc、\_mbbtombc\_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|转换 1 个字节多字节字符转换为相应的 2 字节多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|转换日本行业标准 \(JIS\) 字符转换为日本微软\(JMS\) 字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|转换JMS字符为JIS字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbctohira、\_mbctohira\_l、\_mbctokata、\_mbctokata\_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|转换多字节字符转换为 1 字节平假名代码|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbctohira、\_mbctohira\_l、\_mbctokata、\_mbctokata\_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|转换多字节字符转换为 1 字节片假名代码|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_mbctombb、\_mbctombb\_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|转换 2 个字节多字节字符转换为相应的 1 字节多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[mbstowcs、\_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为宽字符的对应顺序|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[mbtowc、\_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为相应的宽字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|把字符串转换为`double`|[\<caps:sentence id\="tgt72" sentenceid\="363f8f2cb09f8ca850491a65df66522e" class\="tgtSentence"\>System::Convert::ToDouble\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[strtol、wcstol、\_strtol\_l、\_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|转换字符串为`long` 整数|[\<caps:sentence id\="tgt74" sentenceid\="e227c715eb07e76d963577b7a799c2bb" class\="tgtSentence"\>System::Convert::ToInt32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)|  
|[strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|转换字符串为`unsigned long` 整数|[\<caps:sentence id\="tgt76" sentenceid\="121858e0b5a36f51abe1c266ab6fba6a" class\="tgtSentence"\>System::Convert::ToUInt32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|将字符串转换为适于指定区域的形式|[\<caps:sentence id\="tgt78" sentenceid\="f57d3343223d1337ec503c6d3e02bac0" class\="tgtSentence"\>System::IFormattable::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.iformattable.tostring.aspx)|  
|[toascii \_\_toascii](../c-runtime-library/reference/toascii-toascii.md)|转换字符为ASCII码||  
|[tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|测试字符，如果当前大写就转换为小写的，|[\<caps:sentence id\="tgt82" sentenceid\="531bb90548dfdc9e9adea31b19ef1cc1" class\="tgtSentence"\>System::Char::ToLower\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.tolower.aspx)|  
|[tolower、\_tolower、towlower、\_tolower\_l、\_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|无条件的将字符转换为小写的|[\<caps:sentence id\="tgt84" sentenceid\="067c0d5e10b0facda111402483f5cd3a" class\="tgtSentence"\>System::String::ToLower\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|  
|[toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|测试字符，如果当前小写就转换为大写的，|[\<caps:sentence id\="tgt87" sentenceid\="fb184167443ee6ce1ae71a9ab9b01edb" class\="tgtSentence"\>System::Char::ToUpper\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.toupper.aspx)|  
|[toupper、\_toupper、towupper、\_toupper\_l、\_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|无条件的将字符转换为大写的|[\<caps:sentence id\="tgt89" sentenceid\="86a1b4a5abf74ef908414687bc4c78df" class\="tgtSentence"\>System::String::ToUpper\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)|  
|[\_ultoa、\_ultow](../c-runtime-library/reference/ultoa-ultow.md), [\_ultoa\_s、\_ultow\_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|把`unsigned` `long` 转化为字符串|[\<caps:sentence id\="tgt92" sentenceid\="ed8e24ad5c647dc4efa4fbe1e9bbc5e3" class\="tgtSentence"\>System::Convert::ToString\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[wcstombs、\_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符的顺序转换为多字节字符的对应序列|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[wctomb、\_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb\_s、\_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|转换宽字符字符串为 `double`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)，[System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)，[System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)，[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi、\_atoi\_l、\_wtoi、\_wtoi\_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|转换宽字符字符串为 `int`|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_atoi64、\_atoi64\_l、\_wtoi64、\_wtoi64\_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|转换宽字符字符串为 `__int64`|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ato，\_atol\_l，\_wtol，\_wtol\_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|转换宽字符字符串为 `long`|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)