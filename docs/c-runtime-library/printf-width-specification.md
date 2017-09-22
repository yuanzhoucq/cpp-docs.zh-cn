---
title: "printf 宽度规范 | Microsoft Docs"
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
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "printf 函数, 格式规范字段"
  - "printf 函数, 宽度规范"
ms.assetid: 8b4a1b1e-bf6e-414f-a1b6-a9b6f1b6ce92
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# printf 宽度规范
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在格式规范里，第二个可选字段是宽规范。  `width` 参数控制字符的最小数量输出的非负十进制整数。  如果输出的字符数值小于指定的宽度，添加空格到值的左侧或右侧依赖于是否左对齐标志 \(`-`\) 被指定，除非到达最小宽度位置。  如果 `width` 由 0 前缀，前导零被添加到整数或浮点数的转换，直至达到最小宽度，除了当转换到无穷大或NaN。  
  
 宽度规格永远不会导致一个值被截断。  如果输出的字符数值大于指定的宽度，或者如果未给定 `width`，输出所有字符的值，以及 [精度](../c-runtime-library/precision-specification.md) 规范。  
  
 如果宽度规范是一个星号 \(`*`\)，从参数列表的 `int` 参数支持的值。  `width` 参数必须先于的被格式化的参数列表中的值，如以下示例所示：  
  
 `printf("%0*f", 5, 3);  /* 00003 is output */`  
  
 丢失或小的 `width` 值的格式规范并不导致输出值的截断。  如果转换的结果比 `width` 值字段宽，展开包含强制转换结果。  
  
## 请参阅  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [标志指令](../c-runtime-library/flag-directives.md)   
 [精度规范](../c-runtime-library/precision-specification.md)   
 [大小规范](../c-runtime-library/size-specification.md)   
 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)