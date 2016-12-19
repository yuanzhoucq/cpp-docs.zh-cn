---
title: "“&lt;logicaloperator&gt;”的返回和参数类型必须是“&lt;shortcircuitoperator&gt;”表达式中使用的“&lt;typename&gt;” | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33034"
  - "bc33034"
helpviewer_keywords: 
  - "BC33034"
ms.assetid: 94cd52dc-5d48-4673-b0b8-38a1954483c6
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;logicaloperator&gt;”的返回和参数类型必须是“&lt;shortcircuitoperator&gt;”表达式中使用的“&lt;typename&gt;”
使用不合适的参数或返回类型声明的用于 [AndAlso 运算符](../Topic/AndAlso%20Operator%20\(Visual%20Basic\).md) 或 [OrElse 运算符](../Topic/OrElse%20Operator%20\(Visual%20Basic\).md) 中的 `And` 运算符或 `Or` 运算符。  
  
 由于未直接定义短路运算符（`AndAlso` 或 `OrElse`），因此必须定义相应的逻辑和行列式运算符。 下表显示了所需的运算符。  
  
|短路运算符|逻辑运算符|行列式运算符|  
|-----------|-----------|------------|  
|`AndAlso`|[And 运算符](../Topic/And%20Operator%20\(Visual%20Basic\).md)|[IsFalse 运算符](../Topic/IsFalse%20Operator%20\(Visual%20Basic\).md)|  
|`OrElse`|[Or 运算符](../Topic/Or%20Operator%20\(Visual%20Basic\).md)|[IsTrue 运算符](../Topic/IsTrue%20Operator%20\(Visual%20Basic\).md)|  
  
 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 使用这些逻辑运算符和行列式运算符来构造用于 `AndAlso` 或 `OrElse` 的短路逻辑。 为使其正常工作，`And` 或 `Or` 定义的操作数和返回值必须为包含类型，也就是说，你可在其中定义 `And` 或 `Or` 的类或结构的类型。  
  
 **错误 ID：**BC33034  
  
### 更正此错误  
  
-   将操作数和返回值的类型更改为在其中定义了此运算符的类或结构的类型。  
  
     \- 或 \-  
  
-   请勿使用在其中定义了此 `And` 或 `Or` 运算符的类或结构的类型的操作数的相应短路运算符（`AndAlso` 或 `OrElse`）。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Visual Basic 中的逻辑运算符和位运算符](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)