---
title: "“Finally”只能在“Try”语句中出现一次 | Microsoft Docs"
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
  - "vbc30381"
  - "bc30381"
helpviewer_keywords: 
  - "BC30381"
ms.assetid: 4fa1d5fa-c54a-4f8c-9d66-9dbcc38c53bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Finally”只能在“Try”语句中出现一次
`Finally` 用于完成 `Try...Catch...Finally` 块；因此它只能在块的末尾出现一次。  
  
 **错误 ID：**BC30381  
  
### 更正此错误  
  
1.  找到并删除冗余 `Finally`。  
  
## 请参阅  
 [Try...Catch...Finally 语句](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的结构化异常处理概述](http://msdn.microsoft.com/zh-cn/bb81af80-a735-4873-9711-6151a48e418a)