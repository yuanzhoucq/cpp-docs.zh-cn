---
title: "C 序列点 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 85e9d8c04280b6f40081b1362a46bf27b62bcc28
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="c-sequence-points"></a>C 序列点
在连续的“序列点”之间，仅能通过表达式修改一次对象的值。 C 语言定义以下序列点：  
  
-   逻辑“与”运算符 (&&) 的左操作数。 完全计算逻辑“与”运算符的左操作数，并在继续之前完成所有副作用。 如果左操作数的计算结果为 false (0)，则不计算另一个操作数。  
  
-   逻辑“或”运算符 (`||`) 的左操作数。 完全计算逻辑“或”运算符的左操作数，并在继续之前完成所有副作用。 如果左操作数的计算结果为 true（非零），则不计算另一个操作数。  
  
-   逗号运算符的左操作数。 完全计算逗号运算符的左操作数，并在继续之前完成所有副作用。 始终计算逗号运算符的两个操作数。 请注意，函数调用中的逗号运算符不保证计算顺序。  
  
-   函数调用运算符。 计算函数的所有参数，并在输入函数前完成所有副作用。 未指定参数之间的计算顺序。  
  
-   条件运算符的第一个操作数。 完全计算条件运算符的第一个操作数，并在继续之前完成所有副作用。  
  
-   完全初始化表达式的末尾（即，不是一个表达式的一部分的另一个表达式，如声明语句中的初始化的末尾）。  
  
-   表达式语句中的表达式。 表达式语句由可选表达式后跟分号 (;) 组成。 为其副作用计算该表达式，并且此计算后面有一个序列点。  
  
-   选择（if 或 `switch`）语句中的控制表达式。 完全计算该表达式，并在执行依赖于选择的代码之前完成所有副作用。  
  
-   `while` 或 do 语句的控制表达式。 完全计算该表达式，并且在执行 `while` 或 do 循环的下一次迭代中的任何语句执行之前完成所有副作用。  
  
-    for 语句的所有三个表达式。 完全计算这些表达式，并在执行 for 循环的下一次迭代中的任何语句之前完成所有副作用。  
  
-   `return` 语句中的表达式。 完全计算该表达式，并在控制返回调用函数之前完成所有副作用。  
  
## <a name="see-also"></a>另请参阅  
 [表达式计算](../c-language/expression-evaluation-c.md)
