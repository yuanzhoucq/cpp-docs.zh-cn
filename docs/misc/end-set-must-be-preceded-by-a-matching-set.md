---
title: "&quot;End Set&quot; 前面必须是匹配的 &quot;Set&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30632"
  - "vbc30632"
helpviewer_keywords: 
  - "BC30632"
ms.assetid: 0c3dd065-566b-485c-9996-6177eb0fde39
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End Set&quot; 前面必须是匹配的 &quot;Set&quot;
`End Set` 用于终止 `Set` 属性过程。`End Set` 构造出现在 `Set` 属性过程外。  
  
 **错误 ID：**BC30632  
  
### 更正此错误  
  
1.  请确保在 `Property` 关键字之后，`End Property` 构造之前声明 `Set` 属性过程。  
  
2.  确保 `Set` 属性过程以 `Set` 关键字开始，以 `End Set` 构造结束。  
  
## 请参阅  
 [Property 语句](../Topic/Property%20Statement.md)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/zh-cn/1c138efa-9bc2-44d7-80a0-f3a7c2510264)