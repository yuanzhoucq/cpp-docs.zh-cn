---
title: "应为“On” | Microsoft Docs"
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
  - "bc36618"
  - "vbc36618"
helpviewer_keywords: 
  - "BC36618"
ms.assetid: 7cb1b205-c4c3-4485-ae3f-8942425692ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应为“On”
已经指定 `Join` 或 `Group Join` 子句，但没有使用 `On` 运算符。 使用 `On` 运算符标识每个集合的范围变量的键字段。 键字段用于匹配每个集合中的项。  
  
 **错误 ID：**BC36618  
  
### 更正此错误  
  
1.  将 `On` 运算符和键字段添加到 `Join` 或 `Group Join` 子句。 下面是一个示例：  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _ Join pet In pets _ On pet.Owner Equals pers _ Select pers.FirstName, PetName = pet.Name  
    ```  
  
## 请参阅  
 [如何：使用联接合并数据](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join 子句](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join 子句](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Visual Basic 中的 LINQ 简介](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)