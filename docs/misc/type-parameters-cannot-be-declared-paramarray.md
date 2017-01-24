---
title: "&lt;type&gt; 参数不能声明为“ParamArray” | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type&gt; 参数不能声明为“ParamArray”
委托、事件或运算符的定义声明了 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md) 参数。  
  
 仅在 `Declare`、`Function`、`Property` 和 `Sub` 参数上允许 `ParamArray` 参数。  
  
 **错误 ID：**BC33009  
  
### 更正此错误  
  
-   从参数列表中删除 `ParamArray` 关键字。  
  
-   如果你正在定义一个运算符，则可能能够利用一系列重载实现 `ParamArray` 功能。  
  
-   如果你正在定义委托或事件，则必须修改应用程序的这一部分的总逻辑。 不能对委托或事件参数使用 [Optional](../Topic/Optional%20\(Visual%20Basic\).md) 或 `ParamArray` 参数或重载版本。  
  
## 请参阅  
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)