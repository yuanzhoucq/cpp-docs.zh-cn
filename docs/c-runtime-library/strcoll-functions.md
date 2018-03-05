---
title: "strcoll 函数| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- strcoll
dev_langs:
- C++
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e5f025d90d4ffac5f9dc293f621023591b5eb4f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="strcoll-functions"></a>strcoll 函数
每个 `strcoll` 和 `wcscoll` 函数根据当前使用的区域设置代码页的 `LC_COLLATE` 类别设置来比较两个字符串。 每个 `_mbscoll` 函数根据当前使用的多字节代码页比较两个字符串。 在以下情况下使用 `coll` 函数进行字符串比较：当前代码页中的字符集顺序和字典字符顺序存在差异，以及此差异对于比较很有用。 使用相应的 `cmp` 函数仅测试字符串相等性。  
  
### <a name="strcoll-functions"></a>strcoll 函数  
  
|SBCS|Unicode|MBCS|描述|  
|----------|-------------|----------|-----------------|  
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|排序两个字符串|  
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|排序两个字符串（不区分大小写）|  
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|排序两个字符串的第一个 `count` 字符|  
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|排序两个字符串的第一个 `count` 字符（不区分大小写）|  
  
## <a name="remarks"></a>备注  
 这些函数（`strcoll`、`stricoll`、`_strncoll` 和 `_strnicoll`）的单字节字符 (SBCS) 版本根据当前区域设置的 `LC_COLLATE` 类别设置比较 `string1` 和 `string2`。 这些函数与相应的 `strcmp` 函数不同，因为 `strcoll` 函数使用提供排序序列的区域设置代码页信息。 对于在字符集顺序和字典字符顺序不同的区域设置中比较字符串，应使用 `strcoll` 函数而不是相应的 `strcmp` 函数。 有关 `LC_COLLATE` 的详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 对于一些代码页和相应的字符集，字符集中的字符顺序可能与字典的字符顺序不同。 在“C”区域设置中并非如此：ASCII 字符集中的字符顺序与字典的字符顺序相同。 但是，在某些欧洲代码页中，例如，字符“a”（值 0x61）位于字符“ä”（值 0xE4）之前，但在字典顺序中，字符“ä”位于字符“a”之前。 要在这种实例中执行字典比较，请使用 `strcoll` 而不是 `strcmp`。 或者，也可以对原始字符串使用 `strxfrm`，然后对结果字符串使用 `strcmp`。  
  
 `strcoll`、`stricoll`、`_strncoll` 和 `_strnicoll` 根据当前使用的区域设置代码页自动处理多字节字符串，如同处理其对应的宽字符 (Unicode) 部分一样。 然而，这些函数的多字节 (MBCS) 版本根据当前使用的多字节代码页以字符为基础排序字符串。  
  
 由于 `coll` 函数按字典顺序整理字符串以进行比较，而 `cmp` 函数仅测试字符串对等性，因此 `coll` 函数速度比相应的 `cmp` 版本慢得多。 因此，应仅在以下情况下使用 `coll` 函数：当前代码页中的字符集顺序和字典字符顺序存在差异，以及此差异对于字符串比较很有用。  
  
## <a name="see-also"></a>请参阅  
 [区域设置](../c-runtime-library/locale.md)   
 [字符串操作](../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp、wcscmp、_mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)