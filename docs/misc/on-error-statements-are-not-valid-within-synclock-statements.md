---
title: "“On Error”语句在“SyncLock”语句内无效 | Microsoft Docs"
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
  - "bc30752"
  - "vbc30752"
helpviewer_keywords: 
  - "BC30752"
ms.assetid: 5c726627-b0fc-4edf-bd29-a83a0009f44d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “On Error”语句在“SyncLock”语句内无效
`On Error` 语句不可用于 `SyncLock` 块中，因为它们可能会中断线程同步。  
  
 **错误 ID：**BC30752  
  
### 更正此错误  
  
1.  将 `On Error` 置于 `SyncLock` 块外。  
  
## 请参阅  
 [On Error 语句](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)