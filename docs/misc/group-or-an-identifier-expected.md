---
title: "应为“Group”或标识符。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36707"
  - "bc36707"
helpviewer_keywords: 
  - "BC36707"
ms.assetid: 214e4aa3-d20f-41b3-902c-f1076d31b832
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应为“Group”或标识符。
`Group By` 或 `Group Join` 子句的 `Into` 部分不包括 `Group` 关键字。 必须在 `Group By` 或 `Group Join` 子句的 `Into` 子句中包括 `Group` 关键字，以标识要用于分组结果的变量名称。 这可以是你指定的名称或关键字 `Group`。  
  
 **错误 ID：**BC36707  
  
### 更正此错误  
  
1.  确保 `Group By` 或 `Group Join` 子句的 `Into` 部分包括 `Group` 关键字，如下面的示例中所示。  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## 请参阅  
 [Visual Basic 中的 LINQ 简介](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [Group By 子句](../Topic/Group%20By%20Clause%20\(Visual%20Basic\).md)   
 [Group Join 子句](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)