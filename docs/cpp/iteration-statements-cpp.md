---
title: "迭代语句 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "迭代语句"
  - "循环结构, 迭代语句"
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 迭代语句 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根据一些循环终止条件，迭代语句会导致语句（或复合语句）被执行零次或多次。  当这些语句是复合语句时，除非遇到 [break](../cpp/break-statement-cpp.md) 语句或 [continue](../cpp/continue-statement-cpp.md) 语句，否则将按顺序执行它们。  
  
 C\+\+ 提供四个迭代语句 \- [while](../cpp/while-statement-cpp.md)、[do](../cpp/do-while-statement-cpp.md)、[for](../cpp/for-statement-cpp.md) 和 [range\-based for](../cpp/range-based-for-statement-cpp.md)。  它们都将进行迭代环，直到其终止表达式的计算结果为零 \(false\)，或直到使用 **break** 语句强制执行循环终止。  下表汇总了这些语句及其操作；后面各节详细讨论了它们。  
  
### 迭代语句  
  
|语句|计算位置|初始化|递增|  
|--------|----------|---------|--------|  
|`while`|循环的顶部|否|否|  
|**do**|循环的底部|否|否|  
|**for**|循环的顶部|是|是|  
|**range\-based for**|循环的顶部|是|是|  
  
 迭代语句的语句部分不能为声明。  但是，它可以是包含声明的复合语句。  
  
## 请参阅  
 [C\+\+ 语句概述](../cpp/overview-of-cpp-statements.md)