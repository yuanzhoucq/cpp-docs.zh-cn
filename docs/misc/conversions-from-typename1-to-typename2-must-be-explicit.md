---
title: "从“&lt;typename1&gt;”到“&lt;typename2&gt;”的转换必须为显式转换 | Microsoft Docs"
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
  - "bc30664"
  - "vbc30664"
helpviewer_keywords: 
  - "BC30664"
ms.assetid: 84c0ece9-d5be-46de-b985-3ea010f3a181
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 从“&lt;typename1&gt;”到“&lt;typename2&gt;”的转换必须为显式转换
无法隐式实现此转换。  
  
 **错误 ID：**BC30664  
  
### 更正此错误  
  
-   使用 `CType` 或某个特定转换函数，如 `CInt` 或 `CDec`。  
  
## 请参阅  
 [类型转换函数](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)