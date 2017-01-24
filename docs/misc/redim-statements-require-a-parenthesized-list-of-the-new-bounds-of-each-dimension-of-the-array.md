---
title: "“ReDim”语句需要一个带括号的列表，该列表列出此数组每个维度的新界限 | Microsoft Docs"
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
  - "bc30670"
  - "vbc30670"
helpviewer_keywords: 
  - "BC30670"
ms.assetid: b2c5fea3-e7db-4797-b917-d61a65befbd4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “ReDim”语句需要一个带括号的列表，该列表列出此数组每个维度的新界限
必须指定数组的新大小作为 `ReDim` 语句的一部分。  
  
 **错误 ID：**BC30670  
  
### 更正此错误  
  
-   提供该数组每级的大小；例如：  
  
    ```  
    ReDim arr(5, 6)  
    ```  
  
## 请参阅  
 [ReDim 语句](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)