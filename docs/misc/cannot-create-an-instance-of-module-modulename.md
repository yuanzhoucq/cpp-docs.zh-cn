---
title: "无法创建模块“&lt;modulename&gt;”的实例 | Microsoft Docs"
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
  - "bc30166"
  - "vbc30166"
helpviewer_keywords: 
  - "BC30166"
ms.assetid: 40b9dbd3-9b57-450f-a631-b0ab06ca19c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法创建模块“&lt;modulename&gt;”的实例
模块仅作为单个共享实例存在，不能创建其他实例。  
  
 **错误 ID：**BC30166  
  
### 更正此错误  
  
-   将模块更改为类，或在 `New` 子句中将其替换为类名。  
  
## 请参阅  
 [Module 语句](../Topic/Module%20Statement.md)   
 [不在生成中：Implements 关键字和 Implements 语句](http://msdn.microsoft.com/zh-cn/b96560f7-6413-480f-a1e2-f80253bab5be)