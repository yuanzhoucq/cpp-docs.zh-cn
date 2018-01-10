---
title: "生成文件预处理运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59007bdabc81b5fe49aa4b5265dc0fc73ef4f0b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="makefile-preprocessing-operators"></a>生成文件预处理运算符
生成文件预处理表达式可以使用在常数值、命令的退出代码、字符串、宏和文件系统路径上使用的运算符。 若要计算该表达式，预处理器应先展开宏、执行命令，然后再执行运算。 运算先按括号中的显式分组进行计算，然后再按运算符优先级进行计算。 该结果是一个常数值。  
  
 `DEFINED` 运算符是宏名称上使用的逻辑运算符。 表达式`DEFINED(` *macroname* `)`适用如果*macroname*定义，即使它没有分配的值。 与 `DEFINED` 或 `!IF` 一起使用的 `!ELSE IF` 等效于 `!IFDEF` 或 `!ELSE IFDEF`。 但是，与这些指令不同，`DEFINED` 可用在复杂表达式中。  
  
 `EXIST` 运算符是文件系统路径上使用的逻辑运算符。 `EXIST(`*路径*`)`适用如果*路径*存在。 `EXIST` 的结果可用在二进制表达式中。 如果*路径*包含空格，请将其括在双引号内。  
  
 若要比较两个字符串，请使用相等 (`==`) 运算符或不相等 (`!=`) 运算符。 用双引号将字符串引起来。  
  
 整数常量可以将一元运算符用于数字求反 (`-`)、1 的补数 (`~`) 和逻辑求反 (`!`)。  
  
 表达式可使用以下运算符。 将相同优先级的运算符分组在一起，分组将按优先级递减的顺序列出。 一元运算符向右关联操作数。 相同优先级的二元运算符按照从左到右的顺序关联操作数。  
  
|运算符|描述|  
|--------------|-----------------|  
|`DEFINED(`*macroname*`)`|产生一个逻辑值的当前定义状态*macroname*。|  
|`EXIST(`*路径*`)`|产生的文件是否存在一个逻辑值*路径*。|  
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
>  按位“异或”运算符 (`^`) 与转义符相同，当在表达式中使用该运算符时，必须对其进行转义（如 `^^`）。  
  
## <a name="see-also"></a>请参阅  
 [生成文件预处理中的表达式](../build/expressions-in-makefile-preprocessing.md)