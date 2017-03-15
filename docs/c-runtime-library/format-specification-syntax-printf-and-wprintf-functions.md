---
title: "格式规范语法：printf 和 wprintf 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wprintf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "标志指令 printf 函数"
  - "printf 函数的格式规范字段"
  - "精度字段"
  - "打印标志指令"
  - "printf 函数, 格式规范字段"
  - "printf 函数, 精度"
  - "类型字段"
  - "类型字段, printf 函数"
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 格式规范语法：printf 和 wprintf 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

介绍 `printf`、`wprintf` 和相关函数的格式化字符串参数的语法。  这些函数有更安全的版本；有关详细信息，请参阅 [CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。  有关各个函数的信息，请参阅这些特定函数对应的文档。  有关这些函数的列表，请参阅[流 I\/O](../c-runtime-library/stream-i-o.md)。  
  
 格式规范包含可选字段和必选字段，并采用以下形式：  
  
 `%`\[[flags](../c-runtime-library/flag-directives.md)\] \[[width](../c-runtime-library/printf-width-specification.md)\] \[**.**[precision](../c-runtime-library/precision-specification.md)\] \[{`h` &#124; `l` &#124; `ll` &#124; `w` &#124; `I` &#124; `I32` &#124; `I64`}\] [type](../c-runtime-library/printf-type-field-characters.md)  
  
 格式规范的每个字段是一个用于指示特定的格式选项或转换说明符的字符或数字。  必选的 `type` 字符指定要应用于参数的转换类型。  可选的 `flags`、`width` 和 `precision` 字段控制格式的其他方面。  基本的格式规范仅包含百分号和一个 `type` 字符，例如 `%s`，它指定字符串转换。  在函数的安全版本中，如果百分比符号后跟一个作为格式字段没有任何意义的字符，则将调用无效参数处理程序。  有关详细信息，请参阅[参数验证](../c-runtime-library/parameter-validation.md)。  在非安全版本中，字符将按原样复制到输出。  若要打印百分号字符，请使用 `%%`。  
  
 格式规范字段控制参数转换和格式设置的以下方面：  
  
 `type`  
 必选的转换说明符字符，用于确定将相关的 `argument` 解释为字符、字符串、整数还是浮点数。  有关详细信息，请参阅 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)。  
  
 `flags`  
 可选的一个或多个字符，用于控制输出对齐方式和符号、空白、前导零、小数点、八进制和十六进制前缀的输出。  有关详细信息，请参阅[标志指令](../c-runtime-library/flag-directives.md)。  格式规范中可出现多个标志，并且这些标志可以按任意顺序出现。  
  
 `width`  
 可选的十进制数字，用于指定要输出的最小字符数。  有关详细信息，请参阅 [printf 宽度规范](../c-runtime-library/printf-width-specification.md)。  
  
 `precision`  
 可选的十进制数字，用于指定要为字符串打印的最大字符数、有效数字的数量（即，浮点值的小数点字符之后的位数）、要为整数值打印的最小位数。  有关详细信息，请参阅[精度规范](../c-runtime-library/precision-specification.md)中的“精度值如何影响类型”。  
  
 `h` &#124; `l` &#124; `ll` &#124; `w` &#124; `I` &#124; `I32` &#124; `I64`  
 可选的 `type` 前缀，用于指定对应参数的大小。  有关详细信息，请参阅[大小规范](../c-runtime-library/size-specification.md)中的“大小前缀”。  
  
> [!IMPORTANT]
>  确保格式规范字符串不是用户定义的。  例如，考虑这样一个程序，它提示用户输入名称并将输入存储在一个名为 `name` 的字符串变量中。  若要打印 `name`，请勿执行下列操作：  
>   
>  `printf( name ); /* Danger!  If name contains "%s", program will crash */`  
>   
>  而应执行以下操作：  
>   
>  `printf( "%s", name );`  
  
## 请参阅  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [printf\_p 位置参数](../c-runtime-library/printf-p-positional-parameters.md)   
 [标志指令](../c-runtime-library/flag-directives.md)   
 [printf 宽度规范](../c-runtime-library/printf-width-specification.md)   
 [精度规范](../c-runtime-library/precision-specification.md)   
 [大小规范](../c-runtime-library/size-specification.md)   
 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)