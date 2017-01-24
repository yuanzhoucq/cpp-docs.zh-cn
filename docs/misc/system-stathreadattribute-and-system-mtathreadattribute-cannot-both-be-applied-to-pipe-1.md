---
title: "“System.STAThreadAttribute”和“System.MTAThreadAttribute”不能同时应用于“|1” | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31513"
  - "vbc31513"
helpviewer_keywords: 
  - "BC31513"
ms.assetid: 7efb4c8e-d31c-4273-9d85-8cd2bef4d120
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “System.STAThreadAttribute”和“System.MTAThreadAttribute”不能同时应用于“|1”
`System.STAThreadAttribute` 和 `System.MTAThreadAttribute` 特性互相排斥。  
  
 **错误 ID：**BC31513  
  
### 更正此错误  
  
1.  应用 `System.MTAThreadAttribute` 或 `System.STAThreadAttribute` 两者之一，而非同时应用。  
  
## 请参阅  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [不在生成中：Visual Basic 中的特性](http://msdn.microsoft.com/zh-cn/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)