---
title: "“Using”必须以匹配的“End Using”结束 | Microsoft Docs"
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
  - "vbc36008"
  - "bc36008"
helpviewer_keywords: 
  - "BC36008"
ms.assetid: 83269108-b169-40a6-bbcc-af1ac8fcfd67
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Using”必须以匹配的“End Using”结束
出现 `Using` 语句而没有相应的 `End Using` 语句。  
  
 必须使用 `End Using` 语句结束 `Using` 块。  
  
 **错误 ID：**BC36008  
  
### 更正此错误  
  
1.  如果此 `Using` 块属于一组嵌套的 `Using` 块，请确保每个块均已正确终止。  
  
2.  将 `End Using` 语句添加到 `Using` 块末尾。  
  
## 请参阅  
 [Using 语句](../Topic/Using%20Statement%20\(Visual%20Basic\).md)   
 [如何：释放系统资源](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)