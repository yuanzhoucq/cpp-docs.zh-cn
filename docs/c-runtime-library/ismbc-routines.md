---
title: "_ismbc 例程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ismbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ismbc 例程"
  - "ismbc 例程"
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _ismbc 例程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个**\_ismbc**实例都针对给定的条件测试给定的多字节字符`c`。  
  
|||  
|-|-|  
|[\_ismbcalnum、\_ismbcalnum\_l、\_ismbcalpha、\_ismbcalpha\_l、\_ismbcdigit、\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[\_ismbcl0、\_ismbcl0\_l、\_ismbcl1、\_ismbcl1\_l、\_ismbcl2、\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|  
|[\_ismbcgraph、\_ismbcgraph\_l、\_ismbcprint、\_ismbcprint\_l、\_ismbcpunct、\_ismbcpunct\_l、\_ismbcblank、\_ismbcblank\_l、\_ismbcspace、\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[\_ismbclegal、\_ismbclegal\_l、\_ismbcsymbol、\_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|  
|[\_ismbchira、\_ismbchira\_l、\_ismbckata、\_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|  
  
## 备注  
 每个 **\_ismbc** 实例的测试结果都依赖于实际的多字节代码页。  多字节代码页具有单字节字母字符。  默认情况下，多字节代码页设置为在程序启动时从操作系统获得的系统默认的 ANSI 代码页。  在使用[\_getmbcp](../c-runtime-library/reference/getmbcp.md) 或 [\_setmbcp](../c-runtime-library/reference/setmbcp.md)时，您可以分别查询或更改多字节代码页。  
  
 输出值受 `LC_CTYPE` 区域设置的类设置的影响；有关更多信息，请参见 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 **\_l** 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 **\_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
|例程|测试条件|代码页 932 示例|  
|--------|----------|----------------|  
|[\_ismbcalnum，\_ismbcalnum\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|字母数字|返回非零，则因此只有当 `c` 是 ASCII 字母英语的单字节表示：为 `_ismbcdigit` 和 `_ismbcalpha` 参见示例。|  
|[\_ismbcalpha，\_ismbcalpha\_](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphabetic|只有当 `c` 是 ASCII 英语字母的单字节表示时，返回非零：请参见实例`_ismbcupper`和`_ismbclower`; 或片假名字母:0xA6\<\=`c`\<\=0xDF。|  
|[\_ismbcdigit，\_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Digit|返回非零，且只有 `c` 是 ASCII 数字的单字节表示：0x30\=\<`c`\<\=0x39。|  
|[\_ismbcgraph，\_ismbcgraph\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|图形|当且仅当 `c` 是任何 ASCII 或片假名可打印字符（除空格（）外）的单字节表示时，返回非零。  请参见 `_ismbcdigit`、`_ismbcalpha` 和 `_ismbcpunct`有关示例。|  
|[\_ismbclegal，\_ismbclegal\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|有效的多字节字符|返回非零，当且只有当第一个字节 `c` 在范围 0x81– 0x9F 或 0xE0 –0xFC，那么，当第二个字节在范围内 0x40 \- 0x7E 或 0x80 \- 0xFC。|  
|[\_ismbclower，\_ismbclower\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小写字母|返回非零，且只有`c` 是 ASCII 字母小写英语的单字节表示：0x61\=\<`c`\<\=0x7A。|  
|[\_ismbcprint，\_ismbcprint\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|可打印|当且仅当 `c` 是任何 ASCII 或片假名可打印字符的单字节表示（包含一个空白 \( \)）:请参阅 `_ismbcspace`、`_ismbcdigit`、`_ismbcalpha`和 `_ismbcpunct`示例。|  
|[\_ismbcpunct，\_ismbcpunct\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|标点|当且仅当 `c` 是任何 ASCII 或片假名标点符号的单字节表示形式时，返回非零。|  
|[\_ismbcblank，\_ismbcblank\_l，](../c-runtime-library/reference/ismbcgraph-functions.md)|空格或水平制表符|当且仅当 `c` 是空格或水平制表符字符的单字节表示：`c`\=0x20 或 `c`\=0x09，返回非零，。|  
|[\_ismbcspace，\_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|当且仅当 `c` 是空格时，返回非零值：`c`\=0x20 或 0x09\<\=`c`\<\=0x0D。|  
|[\_ismbcsymbol，\_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|多字节字符|返回非零，当且仅当 0x8141\=\<`c`\<\=0x81AC。|  
|[\_ismbcupper，\_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大写字母|返回非零，且只有`c` 是 ASCII 字母大写英语的单字节表示：0x41\=\<`c`\<\=0x5A。|  
  
 **代码页 932 特定**  
  
 下面的实例特定给代码页 932。  
  
|例程|测试条件 \(代码页 932 只\)|  
|--------|------------------------|  
|[\_ismbchira，\_ismbchira\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|双字节平假名：0x829F\=\<`c`\<\=0x82F1。|  
|[\_ismbckata，\_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|双字节片假名：0x8340\=\<`c`\<\=0x8396。|  
|[\_ismbcl0，\_ismbcl0\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 非日本汉字：0x8140\=\<`c`\<\=0x889E。|  
|[\_ismbcl1，\_ismbcl1\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 级别 1:0x889F\=\<`c`\<\=0x9872。|  
|[\_ismbcl2，\_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS 级别 2:0x989F\=\<`c`\<\=0xEA9E。|  
  
 `_ismbcl0`, `_ismbcl1`, and `_ismbcl2` 检查前面表格描述的满足测试条件的指定值`c`，但是，不检查`c`是有效的多字节字符。  如果低字节在范围 0x00 – 0x3F、0x7F 或 0xFD – 0xFF，这些函数返回一个非零值，指示满足测试条件的字符。  使用 [\_ismbbtrail、\_ismbbtrail\_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) 测试多字节字符是否已定义。  
  
 **END代码页 932 特定**  
  
## 请参阅  
 [字符分类](../c-runtime-library/character-classification.md)   
 [is、isw 例程](../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 例程](../c-runtime-library/ismbb-routines.md)