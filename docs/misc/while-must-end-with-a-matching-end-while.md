---
title: "“While”必须以匹配的“End While”结束 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30082"
  - "vbc30082"
helpviewer_keywords: 
  - "BC30082"
ms.assetid: 50b722b1-906f-4cb1-b5d4-fefab2ba3907
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “While”必须以匹配的“End While”结束
出现 `While` 语句而没有相应的 `End While` 语句。 必须使用 `End While` 语句结束 `While` 块。  
  
 **错误 ID：**BC30082  
  
### 更正此错误  
  
1.  如果此 `While` 块属于一组嵌套的 `While` 块，请确保每个块均已正确终止。  
  
2.  将 `End While` 语句添加到 `While` 块末尾。  
  
## 请参阅  
 [While...End While 语句](../Topic/While...End%20While%20Statement%20\(Visual%20Basic\).md)