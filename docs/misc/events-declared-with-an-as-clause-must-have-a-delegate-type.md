---
title: "用 &quot;As&quot; 子句声明的事件必须有委托类型 | Microsoft Docs"
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
  - "vbc31044"
  - "bc31044"
helpviewer_keywords: 
  - "BC31044"
ms.assetid: d0e86fcc-c638-4945-aa6f-9826aa38b23d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 用 &quot;As&quot; 子句声明的事件必须有委托类型
指定了非委托的类型。  
  
 **错误 ID：**BC31044  
  
### 更正此错误  
  
1.  删除 `As` 子句。  
  
2.  使用 `As` 子句指定委托。  
  
## 请参阅  
 [事件](../Topic/Events%20\(Visual%20Basic\).md)   
 [委托](../Topic/Delegates%20\(Visual%20Basic\).md)   
 [Event 语句](../Topic/Event%20Statement.md)   
 [Delegate 语句](../Topic/Delegate%20Statement.md)