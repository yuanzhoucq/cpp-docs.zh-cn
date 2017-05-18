---
title: "字符串到数值函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _tcstoui64
- _tcstoi64
dev_langs:
- C++
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
caps.latest.revision: 8
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: f3e38062baccecbe3b3cf5bbc9e059c1f1acae56
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="string-to-numeric-value-functions"></a>字符串到数值函数
-   [strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)  
  
-   [strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)  
  
-   [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)  
  
-   [_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)  
  
-   [_strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)  
  
## <a name="remarks"></a>备注  
 **strtod** 系列中的每个函数都可将以空值终止的字符串转换为数值。 下表中列出了可用函数。  
  
|函数|说明|  
|--------------|-----------------|  
|`strtod`|将字符串转换为双精度浮点值|  
|`strtol`|将字符串转换为长整型|  
|`strtoul`|将字符串转换为无符号长整型|  
|`_strtoi64`|将字符串转换为 64 位 `__int64` 整数|  
|`_strtoui64`|将字符串转换为 64 位无符号 `__int64` 整数|  
  
 `wcstod`、`wcstol`、`wcstoul` 和 `_wcstoi64` 分别是 `strtod`、`strtol`、`strtoul` 和 `_strtoi64` 的宽字符版本。 每个宽字符函数的字符串参数都是一个宽字符串；每个函数的行为与其对应的单字节字符相同。  
  
 `strtod` 函数有两个参数：第一个是输入字符串，第二个是结束转换过程的字符的指针。 `strtol`、`strtoul`、**_strtoi64** 和 **_strtoui64** 将第三个参数作为在转换过程中使用的数基。  
  
 输入字符串是一系列字符，可以解释为指定类型的数值。 每个函数在首个无法识别为数字一部分的字符处停止读取字符串。 这可能是终止 null 字符。 对于 `strtol`、`strtoul`、`_strtoi64` 和 `_strtoui64`，该终止字符也可以是大于或等于用户提供的数基的第一个数字字符。  
  
 如果用户提供的指向转换结束字符的指针在调用时未设置为 **NULL**，则会在该位置存储指向停止扫描的字符的指针。 如果无法执行任何转换（未找到任何有效的数字或指定了无效的基数），则将在该位置存储字符串指针的值。  
  
 `strtod` 应为以下形式的字符串：  
  
 [*whitespace*] [*sign*] [`digits`] [**.**`digits`] [ {**d** &#124; **D** &#124; **e** &#124; **E**}[*sign*]`digits`]  
  
 *whitespace* 可能包含被忽略的空格或制表符；*sign* 是加号 (**+**) 或减号 (**-**)；`digits` 是一个或多个十进制数字。 如果基数字符前没有任何数字，则基数字符后必须至少有一个数字。 十进制数字可以后跟一个指数，其中包含介绍性字母（**d**、**D**、**e** 或 **E**）和可选的带符号整数。 如果指数部分和基数字符都没有出现，则假定基数字符跟随字符串中的最后一个数字。 不符合此形式的第一个字符停止扫描。  
  
 `strtol`、`strtoul`、`_strtoi64` 和 `_strtoui64` 函数应为以下形式的字符串：  
  
 [*whitespace*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [`digits`]  
  
 如果 base 参数在 2 和 36 之间，则将其用作数字的基数。 如果为 0，则转换结束指针引用的初始字符将用于确定基数。 如果第一个字符为 0，且第二个字符不为“x”或“X”，则将该字符串视为八进制整数；否则将其视为十进制数。 如果第一个字符为“0”，且第二个字符为“x”或“X”，则将该字符串视为十六进制整数。 如果第一个字符是“1”至“9”，则将该字符串视为十进制整数。 为字母“a”到“z”（或“A”到“Z”）分配了 10 到 35 的值；仅允许分配的值小于 *base* 的字母。 `strtoul` 和 `_strtoui64` 允许加号 (**+**) 或减号 (**-**) 前缀；前导减号表示返回值不起作用。  
  
 输出值受区域设置的 `LC_NUMERIC` 类别设置影响；有关详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
 当这些函数返回的值会导致溢出或下溢，或不能转换时，将返回如下特殊情况值：  
  
|函数|条件|值|  
|--------------|---------------|--------------------|  
|`strtod`|溢出|+/- `HUGE_VAL`|  
|`strtod`|下溢或不进行转换|0|  
|`strtol`|+ 溢出|**LONG_MAX**|  
|`strtol`|- 溢出|**LONG_MIN**|  
|`strtol`|下溢或不进行转换|0|  
|`_strtoi64`|+ 溢出|**_I64_MAX**|  
|`_strtoi64`|- 溢出|**_I64_MIN**|  
|`_strtoi64`|不进行转换|0|  
|`_strtoui64`|溢出|**_UI64_MAX**|  
|`_strtoui64`|不进行转换|0|  
  
 **_I64_MAX**、_**I64_MIN** 和 **_UI64_MAX** 在 LIMITS.H 中进行定义。  
  
 `wcstod`、`wcstol`、`wcstoul`、`_wcstoi64` 和 `_wcstoui64` 分别是 `strtod`、`strtol`、`strtoul`、`_strtoi64` 和 `_strtoui64` 的宽字符版本。指向每个宽字符函数的转换结束参数的指针都是一个宽字符串。 否则，每个宽字符函数将与其对应的单字节字符的行为相同。  
  
## <a name="see-also"></a>另请参阅  
 [数据转换](../c-runtime-library/data-conversion.md)   
 [区域设置](../c-runtime-library/locale.md)   
 [多字节字符序列的解释](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [浮点支持](../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
