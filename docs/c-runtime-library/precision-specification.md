---
title: "精度规范 | Microsoft Docs"
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
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "c.math"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "printf 函数, 格式规范字段"
ms.assetid: dc59ea4e-d23a-4f1f-9881-2c919ebefb82
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 精度规范
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在格式规范，第三可选字段是精度规范。  它包含，根据转换类型，指定字符串的字符的数量，小数位数或将这些类型输出的有效位数的非负十进制整数 \(.\) 及后跟的过程。  
  
 与宽度指定精度规范，可以生成输出值的浮点值的截断或轮。  如果指定了 `precision`，因为 0 以及要转换的值是 0，如下例所示，结果是不存在字符输出，例如：  
  
 `printf( "%.0d", 0 );      /* No characters output */`  
  
 如果精度规范是一个星号 \(`int`\)，从参数列表参数支持的值。  `precision` 参数必须先于的被格式化的参数列表中的值，如以下示例所示：  
  
 `printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`  
  
 类型确定 `precision` 的说明或默认精度，则省略 `precision`。时，如下表所示。  
  
### 精度如何影响值类型  
  
|类型|含义|默认|  
|--------|--------|--------|  
|`a`, `A`|精度指定在点后数字的个数。|默认值精度为6。  如果精度为 0，小数点未输出，除非使用 `#` 标志。|  
|`c`, `C`|精度不起作用。|打印字符。|  
|`d`, `i`, `u`, `o`, `x`, `X`|精度指定要打印的最小位数。  如果在参数的数字的数目小于 `precision`，用零填充。中输出值在左边  当数字的数目超过 `precision`值时，不会被截断。|默认值精度为1。|  
|`e`, `E`|精度说明符指示小数点后要打印的位数。  打印最后的数值舍入。|默认值精度为6。  如果 `precision` 为 0 或句点 \(.\)，而不出现在它后面的数字，小数点未输出。|  
|`f`|精度说明符指示小数点后所需的位数。  如果出现小数点，在它之前至少出现一个数字。  值舍入到数字的数据。|默认值精度为6。  如果 `precision` 为 0 或句点 \(.\)，而不出现在它后面的数字，小数点未输出。|  
|`g`, `G`|精度指定打印的有效位的最大数目。|六个有效位打印，因此，任何尾随零截断。|  
|`s`, `S`|精度指定要打印字符的最大数量。  超出 `precision` 的字符未打印。|打印字符，直到遇到 null 字符。|  
  
## 请参阅  
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [格式规范语法：printf 和 wprintf 函数](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [标志指令](../c-runtime-library/flag-directives.md)   
 [printf 宽度规范](../c-runtime-library/printf-width-specification.md)   
 [大小规范](../c-runtime-library/size-specification.md)   
 [printf 类型字段字符](../c-runtime-library/printf-type-field-characters.md)