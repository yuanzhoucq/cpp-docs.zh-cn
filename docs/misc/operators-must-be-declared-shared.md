---
title: "运算符必须声明为“Shared”。 | Microsoft Docs"
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
  - "vbc33012"
  - "bc33012"
helpviewer_keywords: 
  - "BC33012"
ms.assetid: 5ad97616-4032-46cd-aaf7-517db5d1195f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符必须声明为“Shared”。
[Operator 语句](../Topic/Operator%20Statement.md) 不包括 [Shared](../Topic/Shared%20\(Visual%20Basic\).md) 关键字。  
  
 `Operator` 过程要求 [Public](../Topic/Public%20\(Visual%20Basic\).md) 和 `Shared` 两个关键字，而转换运算符还要求 [Widening](../Topic/Widening%20\(Visual%20Basic\).md) 或 [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md) 关键字。  
  
 **错误 ID：**BC33012  
  
### 更正此错误  
  
-   将 `Shared` 关键字添加到 `Operator` 语句中。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)