---
title: "_ismbc 例程 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: _ismbc
dev_langs: C++
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b512bad001ed86ad0720002cd49c54b21b6e555
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ismbc-routines"></a>_ismbc 例程
每个 **_ismbc** 例程都针对特定条件测试给定多字节字符 `c`。  
  
|||  
|-|-|  
|[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|  
|[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|  
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|  
  
## <a name="remarks"></a>备注  
 每个 **_ismbc** 例程的测试结果取决于有效的多字节代码页。 多字节代码页具有单字节字母字符。 默认情况下，多字节代码页设置为在程序启动时从操作系统获取的系统默认 ANSI 代码页。 可分别使用 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 和 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 查询和更改使用中的多字节代码页。  
  
 输出值受区域设置的 `LC_CTYPE` 类别设置影响；有关详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
|例程|测试条件|代码页 932 示例|  
|-------------|--------------------|---------------------------|  
|[_ismbcalnum、_ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母数字|当且仅当 `c` 是 ASCII 英文字母的单字节表示形式时返回非零值：请参见 `_ismbcdigit` 和 `_ismbcalpha` 的示例。|  
|[_ismbcalpha、_ismbcalpha\_](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphabetic|当且仅当出现以下情况时返回非零值：`c` 是 ASCII 英文字母的单字节表示形式：查看 `_ismbcupper` 和 `_ismbclower` 的示例；或是片假名字母的单字节表示形式：0xA6<=`c`<=0xDF。|  
|[_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|数字|当且仅当 `c` 是 ASCII 数字 0x30<=`c`<=0x39 的单字节表示形式时返回非零值。|  
|[_ismbcgraph、_ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|图形|当且仅当 `c` 是除空格 () 之外的任何 ASCII 或片假名可打印字符的单字节表示形式时返回非零值。 请参阅 `_ismbcdigit`、`_ismbcalpha` 和 `_ismbcpunct` 的示例。|  
|[_ismbclegal、_ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|有效的多字节字符|当且仅当 `c` 的第一个字节在 0x81 - 0x9F 或 0xE0 - 0xFC 范围内，同时第二个字节在 0x40 - 0x7E 或 0x80 - FC 范围内时返回非零值。|  
|[_ismbclower、_ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小写字母|当且仅当 `c` 是 ASCII 小写英文字母 0x61<=`c`<=0x7A 的单字节表示形式时返回非零值。|  
|[_ismbcprint、_ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可打印|当且仅当 `c` 是包括空格 () 的任何 ASCII 或片假名可打印字符的单字节表示形式时返回非零值：查看 `_ismbcspace`、`_ismbcdigit`、`_ismbcalpha` 和 `_ismbcpunct` 的示例。|  
|[_ismbcpunct、_ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|标点|当且仅当 `c` 是任何 ASCII 或片假名标点字符的单字节表示形式时返回非零值。|  
|[_ismbcblank、_ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|空格或水平制表符|当且仅当 `c` 是空格字符或水平制表符的单字节表示形式时，返回非零值：`c` = 0x20 或 `c` = 0x09。|  
|[_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|当且仅当 `c` 是空白字符 `c`=0x20 或 0x09<=`c`<=0x0D 时返回非零值。|  
|[_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|多字节字符|当且仅当 0x8141<=`c`<=0x81AC 时返回非零值。|  
|[_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大写字母|当且仅当 `c` 是 ASCII 大写英文字母 0x41<=`c`<=0x5A 的单字节表示形式时返回非零值。|  
  
 **特定于代码页 932**   
  
 下面的例程特定于代码页 932。  
  
|例程|测试条件（仅代码页 932）|  
|-------------|-------------------------------------------|  
|[_ismbchira、_ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|双字节平假名：0x829F<=`c`<=0x82F1。|  
|[_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|双字节片假名：0x8340<=`c`<=0x8396。|  
|[_ismbcl0、_ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 非日本汉字：0x8140<=`c`<=0x889E。|  
|[_ismbcl1、_ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 1 级：0x889F<>`c`<=0x9872。|  
|[_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 2 级：0x989F<=`c`<=0xEA9E。|  
  
 `_ismbcl0`、`_ismbcl1` 和 `_ismbcl2` 将检查指定值 `c` 是否匹配上表中所述的测试条件，但不会检查 `c` 是否为有效的多字节字符。 如果低字节位于范围 0x00 - 0x3F、0x7F 或 0xFD - 0xFF 内，这些函数将返回一个非零值，指明字符满足测试条件。 使用 [_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) 来测试是否定义了多字节字符。  
  
 **END 特定于代码页 932**   
  
## <a name="see-also"></a>另请参阅  
 [字符分类](../c-runtime-library/character-classification.md)   
 [is、isw 例程](../c-runtime-library/is-isw-routines.md)   
 [_ismbb 例程](../c-runtime-library/ismbb-routines.md)