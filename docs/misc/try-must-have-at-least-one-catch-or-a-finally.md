---
title: "Try 必须至少有一个“Catch”或“Finally” | Microsoft Docs"
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
  - "bc30030"
  - "vbc30030"
helpviewer_keywords: 
  - "BC30030"
ms.assetid: d6eadd58-3788-42ae-8cc0-59aba86c7c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Try 必须至少有一个“Catch”或“Finally”
一个 `Try` 块必须包括一个 `Finally` 块或至少在 `End Try` 语句之前包括一个 `Catch` 块。  
  
 **错误 ID：**BC30030  
  
### 更正此错误  
  
-   在 `Try` 块中添加 `Catch` 或 `Finally` 块。  
  
## 请参阅  
 [Try...Catch...Finally 语句](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)