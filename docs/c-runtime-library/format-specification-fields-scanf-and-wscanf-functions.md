---
title: "格式规范字段：scanf 和 wscanf 函数 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- wscanf
- scanf
dev_langs:
- C++
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 77ef83eccc158cb9fff1a9161b5694a4caf62777
ms.lasthandoff: 04/01/2017

---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>格式规范字段：scanf 和 wscanf 函数
此处的信息适用于整个 `scanf` 函数系列（包括安全版本），并描述了用于告诉 `scanf` 函数如何将输入流（如 `stdin` 的输入流 `scanf`）分析为插入到程序变量中的值。  
  
 格式规范具有以下形式：  
  
 `%`[`*`] [[width](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][type](../c-runtime-library/scanf-type-field-characters.md)  
  
 `format` 参数指定输入的解释，并且可以包含以下一项或多项：  
  
-   空白字符：空白 (' ')；制表符 ('\t')；或换行符 ('\n')。 空白字符将使得 `scanf` 读取（但不存储）输入中所有连续的空白字符，直至下一个非空白字符。 格式中的一个空白字符与输入中的任何数字（包括 0）和空白字符的组合相匹配。  
  
-   百分号 (`%`) 除外的非空白字符。 非空白字符将使得 `scanf` 读取（但不存储）匹配的非空白字符。 如果输入流中的下一个字符不匹配，则 `scanf` 将会终止。  
  
-   由百分号 (`%`) 引入的格式规范。 格式规范将使得 `scanf` 读取输入中的字符并将其转换为指定类型的值。 该值将分配给参数列表中的一个参数。  
  
 格式为从左向右读取。 不符合格式规范的字符应匹配输入流中的字符序列；将扫描但不存储输入流中的匹配字符。 如果输入流中的字符与格式规范冲突，则 `scanf` 将终止，并且将该字符留在输入流中，就像没有读取过它一样。  
  
 遇到第一个格式规范时，第一个输入字段的值将根据此规范进行转换并储存在第一个 `argument` 指定的位置中。 第二个格式规范将使得第二个输入字段进行转换并储存在第二个 `argument` 中，依此类推，直至格式字符串的末尾。  
  
 将输入字段定义为第一个空白字符（空格、制表符或换行符）之前的所有字符，或第一个无法根据格式规范转换的字符之前的所有字符，或在达到最大字段宽度（如果已指定）之前的所有字符。 如果给定的规范有太多参数，则将计算但忽略多余的参数。 如果格式规范没有足够参数，则结果不可预知。  
  
 格式规范的每个字段是一个用于指定特定格式选项的字符或数字。 位于最后一个可选格式字段之后的 `type` 字符决定将输入字段解释为字符、字符串还是数字。  
  
 最简单的格式规范仅包含百分号和一个 `type` 字符（例如，`%s`）。 如果百分号 (`%`) 后跟一个没有意义的字符作为格式控制字符，则该字符及其后面的字符（直至下一个百分号）将被视为普通字符序列，即必须与输入匹配的字符序列。 例如，若要指定要输入的百分号字符，请使用 `%%`。  
  
 百分号后面的星号 (`*`) 将取消下一个输入字段的分配（将被解释为指定类型的字段）。 将扫描但不储存该字段。  
  
 `_s` 函数系列的安全版本（具有 `scanf` 后缀的版本）需要在每个 `c`、`C`、`s`、`S` 或 `[` 类型的参数之后立即传入一个缓冲区大小参数。 有关 `scanf` 系列函数的安全版本的更多信息，请参阅 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)。  
  
## <a name="see-also"></a>另请参阅  
 [scanf 宽度规范](../c-runtime-library/scanf-width-specification.md)   
 [scanf 类型字段字符](../c-runtime-library/scanf-type-field-characters.md)   
 [scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
