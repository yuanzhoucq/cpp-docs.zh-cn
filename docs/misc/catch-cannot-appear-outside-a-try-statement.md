---
title: "“Catch”不能出现在“Try”语句之外 | Microsoft Docs"
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
  - "bc30380"
  - "vbc30380"
helpviewer_keywords: 
  - "BC30380"
ms.assetid: 73ce950d-881f-4532-8024-40a4930abd32
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Catch”不能出现在“Try”语句之外
`Catch` 必须出现在 `Try...Catch...Finally` 语句块之内。 或是 `Try` 块中具有不必要的 `Catch`，或是 `Catch` 语句出现在其对应 `Try` 块的边界之外。  
  
 **错误 ID：**BC30380  
  
### 更正此错误  
  
1.  如果 `Catch` 语句不必要，请删除它，或者请将其置于 `Try...Catch...Finally` 语句块之内。  
  
## 请参阅  
 [Try...Catch...Finally 语句](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的结构化异常处理概述](http://msdn.microsoft.com/zh-cn/bb81af80-a735-4873-9711-6151a48e418a)