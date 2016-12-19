---
title: "&quot;Exit Property&quot; 在 Function 或 Sub 中无效 | Microsoft Docs"
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
  - "vbc30066"
  - "bc30066"
helpviewer_keywords: 
  - "BC30066"
ms.assetid: 09e7e766-e35d-4282-b949-d227f733f950
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Exit Property&quot; 在 Function 或 Sub 中无效
`Exit Property` 出现在 `Function` 过程或 `Sub` 过程中。`Exit` 语句必须与它所在的块匹配。  
  
 **错误 ID：**BC30066  
  
### 更正此错误  
  
-   根据需要，用 `Exit Function` 或 `Exit Sub` 语句替换 `Exit Property`。  
  
## 请参阅  
 [Sub 过程](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [Function 过程](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [Property 过程](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)