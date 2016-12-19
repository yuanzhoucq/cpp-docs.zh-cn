---
title: "缺少事件“&lt;eventname&gt;”的“RemoveHandler”定义 | Microsoft Docs"
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
  - "bc31131"
  - "vbc31131"
helpviewer_keywords: 
  - "BC31131"
ms.assetid: 0ef68daf-b66e-4ecf-bf2c-dcacabd8aa3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 缺少事件“&lt;eventname&gt;”的“RemoveHandler”定义
如果一个事件被声明为 `Custom`，它必须提供用于删除事件处理程序的过程。  
  
 **错误 ID：**BC31131  
  
### 更正此错误  
  
1.  在 `Custom Event` 语句和 `End Event` 语句之间包括 `RemoveHandler` 声明。  
  
2.  验证事件声明中的其他过程是否正确终止。  
  
## 请参阅  
 [RemoveHandler 语句](../Topic/RemoveHandler%20Statement.md)   
 [Event 语句](../Topic/Event%20Statement.md)