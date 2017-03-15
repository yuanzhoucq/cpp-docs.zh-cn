---
title: "字符串到数值函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcstoui64"
  - "_tcstoi64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "分析, 数值字符串"
  - "字符串转换, 到数值"
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 字符串到数值函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

-   [strtod、\_strtod\_l、wcstod、\_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)  
  
-   [strtol、wcstol、\_strtol\_l、\_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)  
  
-   [strtoul、\_strtoul\_l、wcstoul、\_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)  
  
-   [\_strtoi64、\_wcstoi64、\_strtoi64\_l、\_wcstoi64\_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)  
  
-   [\_strtoui64、\_wcstoui64、\_strtoui64\_l、\_wcstoui64\_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)  
  
## 备注  
 在**strtod** 系列中的每个函数转换null终止字符串到数值。  下表列出了可用函数。  
  
|功能|说明|  
|--------|--------|  
|`strtod`|转换字符串到双精度浮点值。|  
|`strtol`|转换字符串到长整形。|  
|`strtoul`|转换字符串到无符号长整型。|  
|`_strtoi64`|转换字符串到64位`__int64`整数。|  
|`_strtoui64`|转换字符串到无符号64位`__int64`整数。|  
  
 `wcstod`, `wcstol`, `wcstoul`, 和 `_wcstoi64` 是 `strtod`, `strtol`, `strtoul`, 和 `_strtoi64`各自的宽字符版本。  这些函数中宽字符的每一个字符串参数是字符串；否则每个函数具有相同的行为与其单一字节字符副本。  
  
 `strtod` 函数带有两个参数：第一是输入字符串，第二个指向结束转换过程的字符的指针。  `strtol`、`strtoul`、**\_strtoi64** 和 **\_strtoui64** 在转换过程采用第三个参数作为数基。  
  
 输入字符串是可被解释为指定类型的数值的字符序列。  每一个函数在发现第一个不能将其识别为数字的字符时，将停止读入字符串。  这可能是终止 null 字符。  对于 `strtol`、`strtoul`、`_strtoi64`和 `_strtoui64`，则此终止字符也可能是第一个用户提供的字符数大于或等于数基。  
  
 如果对的字符转换的主题提供的指针没有设置为在调用时间的 **NULL** ，为停止扫描字符的指针将存储在其中。  如果没有转换可以执行（未找到有效数字或指定了无效基础）， 字符串指针的值存储在地址中。  
  
 `strtod` 需要以下格式的字符串：  
  
 \[*空白*\] \[*符号*\] \[`digits`\] \[**.**`digits`\]\[ {**d** &#124; **D** &#124; **e** &#124; **E**}*符号*\] \[`digits`\]  
  
 *空白*可能包含已忽略的空格或制表符；;*符号* 是加号 \(**\+**\) 或减号 \(**–**\)；而 `digits`是一个或多个十进制数字。  如果在基数字符前面没有出现数字，则至少基数字符后面应有一个数字。  十进制数字后跟指数，包括一个介绍性字母（**d**、**D**、 **e**, 或 **E** ）和一个可选带符号的整数。  如果指数部分和基数字符均未出现，则基数字符假定后跟该字符串的最后一位数。  不符合此窗体的首个字符将终止扫描。  
  
 `strtol`、`strtoul`、`_strtoi64`和 `_strtoui64` 函数需要以下格式的字符串：  
  
 \[*空白*\] \[{**\+** &#124; **–**}\] \[**0** \[{ **x** &#124; **X** }\]\] \[`digits`\]  
  
 如果 基础自变量在 2 和 36 之间，则将它用作数字的基础。  如果是 0，初始字符引用由结束转换指针来确定基本。  如果第一个字符是 0，第二个字符不是“x”或“X”，字符串解释为八进制整数；否则，它将被解释为十进制数字。  如果首个字符为“0”，而第二个字符为“X”或“Y”，该字符串则被解读为十六进制整数。  如果第一个字符为“1”到“9”，该字符串被解读为十进制整数。  字母“a”到“z”（或“A”到“Z”）赋值 10 到 35；只允许使用赋值小于*base* 的字母。   `strtoul` 和 `_strtoui64` 允许加 \(**\+**\) 或减 \(**–**\)前缀；前导减号表示返回值为负。  
  
 输出值受区域设置的 `LC_NUMERIC` 类设置影响；有关更多信息，请参见 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 **\_l** 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 **\_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
 这些函数返回的值将导致溢出或下溢时，或者，在转换不可能，特定情况返回值所示：  
  
|功能|条件|返回值|  
|--------|--------|---------|  
|`strtod`|溢出|\+\/\- `HUGE_VAL`|  
|`strtod`|不转换或下溢|0|  
|`strtol`|\+溢出。|**LONG\_MAX**|  
|`strtol`|\-溢出。|**LONG\_MIN**|  
|`strtol`|不转换或下溢|0|  
|`_strtoi64`|\+溢出。|**\_I64\_MAX**|  
|`_strtoi64`|\-溢出。|**\_I64\_MIN**|  
|`_strtoi64`|无转换。|0|  
|`_strtoui64`|溢出|**\_UI64\_MAX**|  
|`_strtoui64`|无转换。|0|  
  
 **\_I64\_MAX**，\_**I64\_MIN**和 **\_UI64\_MAX** 位于 LIMITS.H. 定义。  
  
 `wcstod`、`wcstol`、`wcstoul`、`_wcstoi64`和 `_wcstoui64` 分别是 `strtod`、`strtol`、`strtoul`、`_strtoi64`和 `_strtoui64`;宽字符版本，到结束转换参数的指针。这些函数中的每个计算机将是宽字符字符串。  否则，这些函数每个宽字符而言其方式与单字节字符副本。  
  
## 请参阅  
 [数据转换](../c-runtime-library/data-conversion.md)   
 [区域设置](../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [浮点支持](../c-runtime-library/floating-point-support.md)   
 [atof、\_atof\_l、\_wtof、\_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)