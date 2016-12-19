---
title: "生成文件预处理运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINED 运算符"
  - "EXIST运算符"
  - "生成文件, 预处理运算符"
  - "NMAKE 程序, 运算符"
  - "运算符 [C++], 生成文件预处理"
  - "预处理 NMAKE 生成文件运算符"
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成文件预处理运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成文件预处理表达式可以使用在常数值、命令的退出代码、字符串、宏和文件系统路径上使用的运算符。  若要计算该表达式，预处理器应先展开宏、执行命令，然后再执行运算。  运算先按括号中的显式分组进行计算，然后再按运算符优先级进行计算。  该结果是一个常数值。  
  
 `DEFINED` 运算符是宏名称上使用的逻辑运算符。  如果已定义 *macroname*，则即使没有为它赋值，表达式 `DEFINED(`*macroname*`)` 仍为真。  与 `!IF` 或 `!ELSE IF` 一起使用的 `DEFINED` 等效于 `!IFDEF` 或 `!ELSE IFDEF`。  但是，与这些指令不同，`DEFINED` 可用在复杂表达式中。  
  
 `EXIST` 运算符是文件系统路径上使用的逻辑运算符。  如果 *path* 存在，则 `EXIST(`*path*`)` 为真。  `EXIST` 的结果可用在二进制表达式中。  如果 *path* 包含空格，则用双引号将它引起来。  
  
 若要比较两个字符串，请使用相等 \(`==`\) 运算符或不相等 \(`!=`\) 运算符。  用双引号将字符串引起来。  
  
 整数常量可以将一元运算符用于数字求反 \(`–`\)、1 的补数 \(`~`\) 和逻辑求反 \(`!`\)。  
  
 表达式可使用以下运算符。  将相同优先级的运算符分组在一起，分组将按优先级递减的顺序列出。  一元运算符向右关联操作数。  相同优先级的二元运算符按照从左到右的顺序关联操作数。  
  
|运算符|描述|  
|---------|--------|  
|`DEFINED(` *macroname* `)`|为 *macroname* 的当前定义状态产生一个逻辑值。|  
|`EXIST(` *path* `)`|为在 *path* 上存在的文件产生一个逻辑值。|  
|||  
|`!`|一元逻辑“非”。|  
|`~`|一元 1 的补数。|  
|`-`|一元求反。|  
|||  
|`*`|乘法。|  
|`/`|除法。|  
|`%`|取模（余数）。|  
|||  
|`+`|加法。|  
|`-`|减法。|  
|||  
|`<<`|按位左移。|  
|`>>`|按位右移。|  
|||  
|`<=`|小于或等于。|  
|`>=`|大于或等于。|  
|`<`|小于。|  
|`>`|大于。|  
|||  
|`==`|相等。|  
|`!=`|不相等。|  
|||  
|`&`|按位“与”。|  
|`^`|按位“异或”。|  
|`&#124;`|按位“或”。|  
|||  
|`&&`|逻辑“与”。|  
|||  
|`&#124;&#124;`|逻辑“或”。|  
  
> [!NOTE]
>  按位“异或”运算符 \(`^`\) 与转义符相同，当在表达式中使用该运算符时，必须对其进行转义（如 `^^`）。  
  
## 请参阅  
 [生成文件预处理中的表达式](../build/expressions-in-makefile-preprocessing.md)