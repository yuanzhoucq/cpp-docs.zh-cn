---
title: "模块中的“Handles”必须指定用单个标识符限定的“WithEvents”变量 | Microsoft Docs"
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
  - "bc31418"
  - "vbc31418"
helpviewer_keywords: 
  - "BC31418"
ms.assetid: 7d866577-1e42-43f1-85d1-5d7eeba881b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模块中的“Handles”必须指定用单个标识符限定的“WithEvents”变量
若要指定事件处理程序，`Handles` 语句必须指定用 `WithEvents` 关键字声明的对象变量。  
  
 **错误 ID：**BC31418  
  
### 更正此错误  
  
-   使用 `WithEvents` 修饰符声明将用在 `Handles` 语句中的变量。  
  
## 请参阅  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)   
 [WithEvents](../Topic/WithEvents%20\(Visual%20Basic\).md)   
 [事件](../Topic/Events%20\(Visual%20Basic\).md)