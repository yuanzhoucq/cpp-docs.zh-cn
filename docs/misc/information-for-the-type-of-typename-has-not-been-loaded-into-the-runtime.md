---
title: "类型“&lt;typename&gt;”的信息未加载到运行时中 | Microsoft Docs"
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
  - "vbc30750"
  - "bc30750"
helpviewer_keywords: 
  - "BC30750"
ms.assetid: b0f074f9-571d-48f8-b334-4fd34b61cd89
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类型“&lt;typename&gt;”的信息未加载到运行时中
引用了尚未被运行时加载的类型。  
  
 **错误 ID：**BC30750  
  
### 更正此错误  
  
1.  重构代码，使该类型定义在当前范围内。  
  
2.  验证是否定义了成员并且已正确拼写了成员名称。  
  
3.  尝试访问该模块中声明的其中一个成员。 在某些情况下，调试环境找不到成员，因为尚未加载在其中声明成员的模块。  
  
## 请参阅  
 [使用 Visual Studio 进行调试](../Topic/Debugging%20in%20Visual%20Studio.md)