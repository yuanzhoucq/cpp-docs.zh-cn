---
title: "“&lt;declaration1&gt;”无法重写“&lt;declaration2&gt;”，因为它们具有不同的访问级别 | Microsoft Docs"
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
  - "bc30266"
  - "vbc30266"
helpviewer_keywords: 
  - "BC30266"
ms.assetid: c9c5c14e-876c-430d-ab98-5087c19efae7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;declaration1&gt;”无法重写“&lt;declaration2&gt;”，因为它们具有不同的访问级别
过程或属性声明试图重写一个同名的继承元素，但是它指定的可访问性与继承元素不同。 继承元素的可访问性（如 `Public` 或 `Private`）必须在重写时保留。  
  
 **错误 ID：**BC30266  
  
### 更正此错误  
  
-   更改重写元素的可访问性以便与继承元素的可访问性匹配。  
  
## 请参阅  
 [不在生成中：重写属性和方法](http://msdn.microsoft.com/zh-cn/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Visual Basic 中的访问级别](../Topic/Access%20Levels%20in%20Visual%20Basic.md)