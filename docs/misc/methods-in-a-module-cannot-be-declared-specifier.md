---
title: "模块中的方法不能声明为“&lt;specifier&gt;” | Microsoft Docs"
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
  - "bc30433"
  - "vbc30433"
helpviewer_keywords: 
  - "BC30433"
ms.assetid: e9fa204c-a40f-439e-95bb-048a89a19159
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模块中的方法不能声明为“&lt;specifier&gt;”
你使用了在 `Module` 语句内的方法上无效的说明符。 模块永远不能实例化，不支持继承且不能实现接口。  
  
 **错误 ID：**BC30433  
  
### 更正此错误  
  
-   删除说明符。  
  
## 请参阅  
 [Module 语句](../Topic/Module%20Statement.md)