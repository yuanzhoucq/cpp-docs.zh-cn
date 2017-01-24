---
title: "&quot;End Sub&quot; 前面必须是匹配的 &quot;Sub&quot; | Microsoft Docs"
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
  - "vbc30429"
  - "bc30429"
helpviewer_keywords: 
  - "BC30429"
ms.assetid: cf9d0cfe-5dfa-4f6d-9d10-69eb16e413e1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End Sub&quot; 前面必须是匹配的 &quot;Sub&quot;
代码中的 `End Sub` 语句前面没有与其匹配的 `Sub` 过程定义。  
  
 **错误 ID：**BC30429  
  
### 更正此错误  
  
-   删除多余的 `End Sub` 语句。  
  
-   提供缺少的 `Sub` 过程（如果有）。  
  
-   将 `End Sub` 移到代码中的适当位置。  
  
## 请参阅  
 [Sub 过程](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [End \<关键字\> 语句](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)