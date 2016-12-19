---
title: "范围变量名无法与“Object”类的成员名匹配 | Microsoft Docs"
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
  - "bc36606"
  - "vbc36606"
helpviewer_keywords: 
  - "BC36606"
ms.assetid: 964245e6-2601-4de6-8a51-25c0d9633418
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 范围变量名无法与“Object”类的成员名匹配
LINQ 查询中的范围变量与 <xref:System.Object> 类的成员名匹配。 这会导致与 Visual Basic 为 LINQ 查询创建的对象冲突。  
  
 **错误 ID：**BC36606  
  
### 更正此错误  
  
1.  为不与 <xref:System.Object> 类的任何成员名匹配的范围变量选择新名称。  
  
## 请参阅  
 <xref:System.Object>   
 [Visual Basic 中的 LINQ 简介](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [From 子句](../Topic/From%20Clause%20\(Visual%20Basic\).md)   
 [Aggregate 子句](../Topic/Aggregate%20Clause%20\(Visual%20Basic\).md)   
 [Select 子句](../Topic/Select%20Clause%20\(Visual%20Basic\).md)