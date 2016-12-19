---
title: "格式规范字段：scanf 和 wscanf 函数 | Microsoft Docs"
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
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wscanf"
  - "scanf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "宽度, scanf 函数中的规范"
  - "scanf 格式规范"
  - "scanf 宽度规范"
  - "scanf 类型字段字符"
  - "类型字段, scanf 函数"
  - "scanf 函数的格式规范字段"
  - "类型字段"
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 格式规范字段：scanf 和 wscanf 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此处的信息应用于整个 `scanf` 函数族，包括安全版本并且描述符号用于调用 `scanf` 函数如何解析输入流，如 `scanf`的输入流 `stdin` ，插入程序变量的值。  
  
 格式规范都有以下形式。  
  
 `%`\[`*`\] \[\] \[{[h&#124;l&#124;ll&#124;I64&#124;L](../c-runtime-library/scanf-width-specification.md)}\][类型](../c-runtime-library/scanf-type-field-characters.md)[宽度](../c-runtime-library/scanf-width-specification.md)  
  
 `format` 参数指定输入的解释，并且可以包含以下一项或多项：  
  
-   空白字符：空 \("\);选项卡 \(“\\ t”\);或者换行符 \(\\ n "\) 。  空格导致 `scanf` 读取，但不存储，在输入中所有连续的空格直到下一个非空格。  在格式中一个空格与输入中任何数字 \(包括 0 \)和空格组合匹配  
  
-   非空格，除了百分比符号 \(`%`\)。  非空格会引起 `scanf` 读取，但是不存储，匹配的非空格。  如果输入流中下一个字符不匹配， `scanf` 终止。  
  
-   格式规范，引入百分比符号 \(`%`\)。  格式规范导致 `scanf` 读取并将输入字符转换成指定类型的值。  赋值给参数列表中的参数。  
  
 格式从左到右读取。  不符合格式规范的字符应该匹配输入流中的字符序列；输入流中的匹配字符被扫描但不被存储。  如果输入流中的字符与格式规范冲突，`scanf` 终止，并且这个字符会留在输入流中仿佛它没有被读取过一样。  
  
 当遇到第一格式规范时，第一个输入字段中的值根据此规范转换并且储存在第一个 `argument` 指定的位置中。  第二种格式规范导致第二个输入字段被转换并储存在第二个 `argument`中，诸如此类直至格式字符串的末尾。  
  
 输入字段定义为任何字符到第一个空白字符 \(空格、制表符、或者换行符\)，或者到无法根据格式规范转换的第一个字符，或直到字段宽度 \(如果指定\) 为止。  如果有太多给定规范的参数，多余的参数会被评估，但忽略。  如果所有的格式规范都没有足够的参数，则结果为未定义。  
  
 每个格式规范的字段是单个字符或者是一个数字代表一个特定的格式选项。  `type` 字符，在最后选项格式字段后出现，以确定输入域是否被解释为字符串、字符或数字。  
  
 最简单格式规范只包含百分号和一个 `type` 字符 \(例如， `%s`\)。  如果百分号 \(`%`\) 后跟一个没有意义作为一个格式控件字符的字符，这个字符和它后面的字符 \(到下个百分号\) 被视为普通字符的序列，即，必须与输入匹配的字符序列。  例如，指定输入百分比符号字符，请使用 `%%`。  
  
 百分号后面的星号 \(`*`\) 压制下一个输入字段的分配，被解释为指定类型的字段。  字段被扫描但未存储。  
  
 `scanf` 函数系列的安全版本 \(具有 `_s` 后缀\) 需要缓冲区大小参数在 `c`，`C`，`s`，`S` 或 `[` 类型的每个参数后立即被传递。  有关 `scanf` 系列函数的安全版本的更多信息，请参见 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)。  
  
## 请参阅  
 [scanf 宽度规范](../c-runtime-library/scanf-width-specification.md)   
 [scanf 类型字段字符](../c-runtime-library/scanf-type-field-characters.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)