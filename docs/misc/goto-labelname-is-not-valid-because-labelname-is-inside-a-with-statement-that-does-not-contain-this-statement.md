---
title: "“GoTo &lt;labelname&gt;”无效，因为“&lt;labelname&gt;”位于不包含此语句的“With”语句内 | Microsoft Docs"
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
  - "bc30756"
  - "vbc30756"
helpviewer_keywords: 
  - "BC30756"
ms.assetid: 9c39d4ad-0b9b-45e9-b6c2-d983144b5b23
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “GoTo &lt;labelname&gt;”无效，因为“&lt;labelname&gt;”位于不包含此语句的“With”语句内
`GoTo` 语句限制为在当前代码块中跳转。  
  
 **错误 ID：**BC30756  
  
### 更正此错误  
  
-   重构你的代码，以便 `GoTo` 语句和标签都位于 `With` 块中。  
  
## 请参阅  
 [GoTo 语句](../Topic/GoTo%20Statement.md)