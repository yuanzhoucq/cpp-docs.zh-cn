---
title: "参数匹配参数“&lt;parametername&gt;”从“&lt;type1&gt;”收缩到“&lt;type2&gt;” | Microsoft Docs"
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
  - "vbc30520"
  - "bc30520"
helpviewer_keywords: 
  - "BC30520"
ms.assetid: 652ff70b-156d-4d1c-af19-fa1c53e2d0b5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 参数匹配参数“&lt;parametername&gt;”从“&lt;type1&gt;”收缩到“&lt;type2&gt;”
你已调用重载方法，但编译器找不到无需收缩转换便可调用的方法。 收缩转换将值更改为可能无法精确保存某些可能值的数据类型。  
  
 **错误 ID：**BC30520  
  
### 更正此错误  
  
-   指定 `Option Strict Off`。  
  
## 请参阅  
 [重载属性和方法](../Topic/Overloaded%20Properties%20and%20Methods%20\(Visual%20Basic\).md)   
 [扩大转换和收缩转换](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [Option Strict 语句](../Topic/Option%20Strict%20Statement.md)