---
title: "“For”必须以匹配的“Next”结束 | Microsoft Docs"
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
  - "vbc30084"
  - "bc30084"
helpviewer_keywords: 
  - "BC30084"
ms.assetid: 4c5e49c2-7343-4487-b5f8-a38c97ba895b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “For”必须以匹配的“Next”结束
出现 `For` 语句而没有相应的 `Next` 语句。 必须使用 `Next` 语句结束 `For` 循环。  
  
 **错误 ID：**BC30084  
  
### 更正此错误  
  
-   如果此 `For` 循环是一组嵌套循环的一部分，请确保每个循环正常终止。  
  
-   将 `Next` 语句添加到 `For` 循环末尾。  
  
## 请参阅  
 [For...Next 语句](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)