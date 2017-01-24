---
title: "运算符“&lt;operator&gt;”必须具有 Boolean 返回类型 | Microsoft Docs"
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
  - "vbc33023"
  - "bc33023"
helpviewer_keywords: 
  - "BC33023"
ms.assetid: 18e066f4-d71e-4e38-b0bc-8af9145f6015
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符“&lt;operator&gt;”必须具有 Boolean 返回类型
使用 [Boolean 数据类型](../Topic/Boolean%20Data%20Type%20\(Visual%20Basic\).md) 以外的返回类型声明比较运算符或逻辑运算符。  
  
 比较运算符的结果（`=`、`<>`、`<`、`<=`、`>`、`>=`、`Is`、`IsNot`、`IsFalse`、`IsTrue`、`Like`、`TypeOf`）只能是 `True` 或 `False`。 有关详细信息，请参阅[比较运算符 \(Visual Basic\)](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)。  
  
 逻辑运算符（`And`、`AndAlso`、`Not`、`Or`、`OrElse`、`Xor`）完全在布尔值的域中工作。 有关详细信息，请参阅[Visual Basic 中的逻辑运算符和位运算符](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC33023  
  
### 更正此错误  
  
-   将此比较运算符或逻辑运算符的返回类型替换为 `Boolean`。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)