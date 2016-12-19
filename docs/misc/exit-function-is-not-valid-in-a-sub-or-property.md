---
title: "“Exit Functio”在 Sub 或属性中无效 | Microsoft Docs"
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
  - "vbc30067"
  - "bc30067"
helpviewer_keywords: 
  - "BC30067"
ms.assetid: 207fef65-4383-4120-9e5a-e0e14d168a72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Exit Functio”在 Sub 或属性中无效
`Exit Function` 出现在 `Sub` 过程或 `Property` 过程中。`Exit` 语句必须与它所在的块匹配。  
  
 **错误 ID：**BC30067  
  
### 更正此错误  
  
-   根据需要，用 `Exit Sub` 或 `Exit Property` 语句替换 `Exit Function`。  
  
## 请参阅  
 [Sub 过程](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [Function 过程](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [Property 过程](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)