---
title: "strcoll 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strcoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "代码页, 用于字符串比较"
  - "strcoll 函数"
  - "字符串比较 [C++], 区域性特定"
  - "字符串 [C++], 按代码页进行比较"
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcoll 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个 `strcoll` 和 `wcscoll` 函数根据正在使用区域设置的代码页的 `LC_COLLATE` 类别设置比较两个字符串。  每个 `_mbscoll` 函数根据正在使用的多字节代码页\) 来比较这两个字符串。  只有在当前代码页中的字符集排序和字典字符存在差异时， `coll` 函数才能使用，这些差异是字符串比较感兴趣的。  使用对应的 `cmp` 函数仅测试字符串相等性。  
  
### strcoll 函数  
  
|SBCS|Unicode|MBCS|说明|  
|----------|-------------|----------|--------|  
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[\_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|排列两个字符串|  
|[\_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[\_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[\_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|排列两字符串 \(不区分大小写\)|  
|[\_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[\_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[\_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|比较两个字符串的第一个 `count` 字符|  
|[\_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[\_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[\_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|比较两个字符串的第一个`count`字符 \(不区分大小写\)|  
  
## 备注  
 单字节字符 \(SBCS\) 生成这些函数 \(`strcoll`、`stricoll`、`_strncoll`和 `_strnicoll`\) 将根据当前区域设置的 `LC_COLLATE` 类别设置比较 `string1` 和 `string2`。  这些函数与 `strcmp` 函数对应的不同因为 `strcoll` 函数使用区域设置提供排序序列的代码页的信息。  对于字符串比较。字符集顺序和字典的字符顺序不同的区域设置，应使用 `strcoll` 函数而不是相应的 `strcmp` 函数。  有关`LC_COLLATE`的详细信息, 请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 对于某些代码页和对应的字符集，该字符集的字符序列可能与字典字符排序不同。  在“C”区域设置，这不是用例：ASCII 字符集中的字符排序与字符的字典排序相同。  但是，在某些欧洲代码页中，例如，在字符集中，字符“a”\(值 0x61\) 位于字符“ä”\(值 0xE4\)之前，但是，在字典序列中，字符“ä”在字符" a ”之前。  若要执行一个字典将在此类实例，使用 `strcoll` 而不是 `strcmp`。  或者，可以使用在原始字符串的 `strxfrm`，然后对结果字符串使用 `strcmp`。  
  
 `strcoll`、`stricoll`、`_strncoll`和 `_strnicoll` 按正在使用区域设置的代码页自动处理多字节字符字符串，就像它们的宽字符 \(Unicode\) 复制。  这些函数对多字节字符 \(MBCS\) 版本，但是，根据正在使用的多字节代码页排列基于基本字符类型的字符串。  
  
 由于 `coll`函数按字典顺序校对字符串的比较，而 `cmp` 函数简单地测试字符串的相等，`coll` 函数执行起来比`cmp`的相关版本慢。  因此，`coll`函数只能使用在字符集顺序和当前代码页的字典字符顺序存在区别时，且该区别引起了字符串比较的不同。  
  
## 请参阅  
 [区域设置](../c-runtime-library/locale.md)   
 [字符串操作](../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [\_mbsnbcoll、\_mbsnbcoll\_l、\_mbsnbicoll、\_mbsnbicoll\_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp、wcscmp、\_mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)