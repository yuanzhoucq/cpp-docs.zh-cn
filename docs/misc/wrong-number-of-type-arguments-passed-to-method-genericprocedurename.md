---
title: "传递给方法“&lt;genericprocedurename&gt;”的类型实参的数目不正确 | Microsoft Docs"
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
  - "bc30951"
  - "vbc30951"
helpviewer_keywords: 
  - "BC30951"
ms.assetid: 84c2f0cb-5706-4b4e-967c-0ca35a20913c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 传递给方法“&lt;genericprocedurename&gt;”的类型实参的数目不正确
已调用泛型过程，其中类型实参的数量与定义它的类型形参的数量不匹配。  
  
 **错误 ID：**BC30951  
  
### 更正此错误  
  
-   向为泛型过程定义的各个类型形参均提供一个类型实参。  
  
     \- 或 \-  
  
-   调用不带任何类型实参的泛型过程，并让编译器尝试推断类型实参。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [AddressOf 运算符](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型过程](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)