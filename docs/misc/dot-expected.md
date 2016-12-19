---
title: "应有“.” | Microsoft Docs"
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
  - "bc30287"
  - "vbc30287"
helpviewer_keywords: 
  - "BC30287"
ms.assetid: 7d7b4934-b521-4ed3-b054-aeb71f8daacf
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应有“.”
代码具有包含感叹号 \(`!`\) 的 `Handles` 子句。  
  
 **错误 ID：**BC30287  
  
### 更正此错误  
  
1.  如果 `Handles` 子句引用对象内的事件，请使用句点 \(`.`\) 将对象与该事件分隔开。  
  
     此示例处理 `Button1` 对象的 `Click` 事件。  
  
     [!code-vb[VbVbalrEventError#21](../misc/codesnippet/VisualBasic/dot-expected_1.vb)]  
  
## 请参阅  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)