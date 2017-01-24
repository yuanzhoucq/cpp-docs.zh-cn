---
title: "只有转换运算符可以声明为“&lt;keyword&gt;”。 | Microsoft Docs"
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
  - "bc33019"
  - "vbc33019"
helpviewer_keywords: 
  - "BC33019"
ms.assetid: 946266fe-a909-41b1-aad4-f85dc8050b88
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 只有转换运算符可以声明为“&lt;keyword&gt;”。
当运算符不为转换运算符时，[Operator 语句](../Topic/Operator%20Statement.md) 指定 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md)。  
  
 每个运算符必须声明为 [Public](../Topic/Public%20\(Visual%20Basic\).md) 和 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)。 但是，仅可使用 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md)（而不可同时使用两者）声明转换运算符。  
  
 运算符定义可以选择性地包含 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 和 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) 关键字。 在 [Operator 语句](../Topic/Operator%20Statement.md) 中不允许有其他关键字。  
  
 **错误 ID：**BC33019  
  
### 更正此错误  
  
1.  将 `Widening` 或 `Narrowing` 关键字从运算符定义中删除。 这些不适用，因为未进行类型转换。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Visual Basic 中的类型转换](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)