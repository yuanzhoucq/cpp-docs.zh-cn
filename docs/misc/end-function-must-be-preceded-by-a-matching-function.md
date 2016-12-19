---
title: "“End Function”前面必须是匹配的“Function” | Microsoft Docs"
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
  - "bc30430"
  - "vbc30430"
helpviewer_keywords: 
  - "BC30430"
ms.assetid: de66a6b4-0321-45c2-aca0-87d2b4244b31
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “End Function”前面必须是匹配的“Function”
代码中的 `End Function` 语句前面没有与其匹配的 `Function` 过程定义。  
  
 **错误 ID：**BC30430  
  
### 更正此错误  
  
1.  删除多余的 `End Function` 语句。  
  
2.  提供缺少的 `Function` 过程（如果有）。  
  
3.  将 `End Function` 移到代码中的适当位置。  
  
## 请参阅  
 [Function 过程](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [End \<关键字\> 语句](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)