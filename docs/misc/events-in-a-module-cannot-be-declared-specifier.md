---
title: "“模块”中的事件不能声明为“&lt;specifier&gt;” | Microsoft Docs"
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
  - "bc30434"
  - "vbc30434"
helpviewer_keywords: 
  - "BC30434"
ms.assetid: ac6a63e3-89a6-4fbb-ade1-4fa033252379
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “模块”中的事件不能声明为“&lt;specifier&gt;”
你使用了在 `Module` 语句内的事件上无效的说明符。 模块永远不能实例化，不支持继承且不能实现接口。  
  
 **错误 ID：**BC30434  
  
### 更正此错误  
  
-   删除说明符。  
  
## 请参阅  
 [Module 语句](../Topic/Module%20Statement.md)