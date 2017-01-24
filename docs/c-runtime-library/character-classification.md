---
title: "字符分类 | Microsoft Docs"
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
  - "c.types.character"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字符分类例程"
  - "字符, 测试"
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字符分类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其中每个实例测试指定的单字节字符、宽字符或多字节字符情况的满意条件。（按照定义，ASCII 字符集（在0到127之间）是所有多字节字符集的子集。  例如，日文片假名包含 ASCII 以及非 ASCII 字符。\)  
  
 测试条件受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
 一般来说，这些程序可以编写执行速度比测试更快，应该更受欢迎。  例如，下面的代码执行比调用`isalpha(c)`慢：  
  
```  
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))  
    return TRUE;  
```  
  
### 字符分类例程  
  
|例程|字符测试条件|.NET Framework 等效项|  
|--------|------------|------------------------|  
|[isalnum、iswalnum、\_isalnum\_l、\_iswalnum\_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母数字|[System::Char::IsLetterOrDigit](https://msdn.microsoft.com/en-us/library/system.char.isletterordigit.aspx)。|  
|[\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母数字|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[isalpha、iswalpha、\_isalpha\_l、\_iswalpha\_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md), [\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphabetic|[\<caps:sentence id\="tgt20" sentenceid\="7985fd1b5b2aeb907c06a172679a27b2" class\="tgtSentence"\>System::Char::IsLetter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)|  
|[isascii，\_\_isascii、 iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|[\<caps:sentence id\="tgt22" sentenceid\="7985fd1b5b2aeb907c06a172679a27b2" class\="tgtSentence"\>System::Char::IsLetter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)|  
|[isblank、iswblank、\_isblank\_l、\_iswblank\_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md), [\_ismbcsblank, \_ismbcsblank\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白 \(空格或水平制表符\)|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[iscntrl、iswcntrl、\_iscntrl\_l、\_iswcntrl\_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|控件|[\<caps:sentence id\="tgt29" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[iscsym、 iscsymf、 \_\_iscsym、 \_\_iswcsym、 \_\_iscsymf、 \_\_iswcsymf、 \_iscsym\_l、 \_iswcsym\_l、 \_iscsymf\_l、 \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|字母、下划线或数字|[\<caps:sentence id\="tgt31" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[iscsym、 iscsymf、 \_\_iscsym、 \_\_iswcsym、 \_\_iscsymf、 \_\_iswcsymf、 \_iscsym\_l、 \_iswcsym\_l、 \_iscsymf\_l、 \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|字母或下划线|[\<caps:sentence id\="tgt33" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[isdigit、iswdigit、\_isdigit\_l、\_iswdigit\_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|十进制数字|[\<caps:sentence id\="tgt36" sentenceid\="20b77d76c6cf167a186925e085420e65" class\="tgtSentence"\>System::Char::IsDigit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)|  
|[isgraph、iswgraph、\_isgraph\_l、\_iswgraph\_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|打印除了空间以外|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[islower、iswlower、\_islower\_l、\_iswlower\_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小写|[\<caps:sentence id\="tgt44" sentenceid\="5e79724bd080c040f5d77abaa610244d" class\="tgtSentence"\>System::Char::IsLower\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)|  
|[\_ismbchira、\_ismbchira\_l、\_ismbckata、\_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|平假名|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbchira、\_ismbchira\_l、\_ismbckata、\_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|片假名|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbclegal、\_ismbclegal\_l、\_ismbcsymbol、\_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|合法多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本级 0 多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本级 1 多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本级 2 多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_ismbclegal、\_ismbclegal\_l、\_ismbcsymbol、\_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|非字母数字多字节字符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[isprint、iswprint、\_isprint\_l、\_iswprint\_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可打印|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ispunct、iswpunct、\_ispunct\_l、\_iswpunct\_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|标点|[\<caps:sentence id\="tgt80" sentenceid\="d38bbde5482b110a63876458567db603" class\="tgtSentence"\>System::Char::IsPunctuation\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)|  
|[isspace、iswspace、\_isspace\_l、\_iswspace\_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白|[\<caps:sentence id\="tgt83" sentenceid\="acbb8b5269b25caa0be79d70895dc079" class\="tgtSentence"\>System::Char::IsWhiteSpace\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)|  
|[Isupper, iswupper](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大写|[\<caps:sentence id\="tgt86" sentenceid\="7f17c3dfa91d5cdf120546eae2131f1f" class\="tgtSentence"\>System::Char::IsUpper\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)|  
|[\_isctype、iswctype、\_isctype\_l、\_iswctype\_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|`desc` 参数中指定的属性|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[isxdigit、iswxdigit、\_isxdigit\_l、\_iswxdigit\_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|十六进制数|[\<caps:sentence id\="tgt92" sentenceid\="ce7b0e5c510cf706d10a80a8594068ce" class\="tgtSentence"\>System::Char::IsNumber\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isnumber.aspx)|  
|[\_mbclen、mblen、\_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|返回有效的多字节字符的长度；结果取决于当前区域设置的 `LC_CTYPE` 类别|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)