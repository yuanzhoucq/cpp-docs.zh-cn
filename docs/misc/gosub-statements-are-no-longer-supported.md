---
title: "不再支持“GoSub”语句 | Microsoft Docs"
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
  - "vbc30814"
  - "bc30814"
helpviewer_keywords: 
  - "BC30814"
ms.assetid: fef2d78f-39ba-4aad-93b3-c7a08df9f805
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不再支持“GoSub”语句
`GoSub` 不能用于调用过程。  
  
 **错误 ID：**BC30814  
  
### 更正此错误  
  
-   直接调用过程而不使用 `GoSub`；例如：  
  
    ```  
    CalculateInterest(Amount, Rate, Time)  
    ```  
  
## 请参阅  
 [过程](../Topic/Procedures%20in%20Visual%20Basic.md)