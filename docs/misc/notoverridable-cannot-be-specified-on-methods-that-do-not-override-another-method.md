---
title: "不能为不会重写另一个方法的方法指定“NotOverridable” | Microsoft Docs"
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
  - "vbc31088"
  - "bc31088"
helpviewer_keywords: 
  - "BC31088"
ms.assetid: 0241197c-51fa-48b8-9a2a-4205d25641d3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能为不会重写另一个方法的方法指定“NotOverridable”
默认情况下，属性和方法 `NotOverridable`。`NotOverridable` 修饰符仅可用于重写另一属性或方法的方法。  
  
 **错误 ID:** BC31088  
  
### 更正此错误  
  
-   从不重写另一成员的属性和方法中删除 `NotOverridable` 修饰符。  
  
## 请参阅  
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md)   
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)