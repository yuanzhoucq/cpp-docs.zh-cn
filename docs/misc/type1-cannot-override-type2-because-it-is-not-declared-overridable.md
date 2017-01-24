---
title: "&lt;type2&gt; 未声明为 &quot;Overridable&quot;，因此“&lt;type1&gt;”无法对它进行重写 | Microsoft Docs"
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
  - "bc31086"
  - "vbc31086"
helpviewer_keywords: 
  - "BC31086"
ms.assetid: ce071994-2e32-4460-a65d-f48f914386c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type2&gt; 未声明为 &quot;Overridable&quot;，因此“&lt;type1&gt;”无法对它进行重写
派生类中的成员重写了没有用 `Overridable` 修饰符标记的基类成员。  
  
 **错误 ID：**BC31086  
  
### 更正此错误  
  
1.  为重写的基类成员添加 `Overridable` 修饰符。  
  
2.  使用 `Shadows` 关键字将基类中的项隐藏。  
  
## 请参阅  
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)