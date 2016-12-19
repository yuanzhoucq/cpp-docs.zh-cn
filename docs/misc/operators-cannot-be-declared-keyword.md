---
title: "运算符不能声明为“&lt;keyword&gt;”。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33013"
  - "bc33013"
helpviewer_keywords: 
  - "BC33013"
ms.assetid: bfd805f4-e30e-4553-9cb7-2690595f0480
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符不能声明为“&lt;keyword&gt;”。
使用对于运算符定义无效的关键字声明运算符。  
  
 每个运算符必须声明为 [Public](../Topic/Public%20\(Visual%20Basic\).md) 和 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)。 此外，可使用任一 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md) 声明转换运算符，但不可同时使用两者。 运算符定义可以选择性地包含 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 或 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 关键字。 在 [Operator 语句](../Topic/Operator%20Statement.md) 中不允许有其他关键字。  
  
 **错误 ID：**BC33013  
  
### 更正此错误  
  
-   从运算符定义中删除无效关键字。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)