---
title: "不能将类型形参“&lt;typeparametername&gt;”约束为其自身：“&lt;errormessage&gt;” | Microsoft Docs"
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
  - "bc32113"
  - "vbc32113"
helpviewer_keywords: 
  - "BC32113"
ms.assetid: a74128ae-11d0-46bf-8c0b-c7a2bf881d17
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能将类型形参“&lt;typeparametername&gt;”约束为其自身：“&lt;errormessage&gt;”
类型形参的约束列表包括该类型形参。  
  
 类型形参的约束列表可以指定任意数量的接口，但最多能指定一个类。 为该类型形参提供的类型实参必须实现每个指定的接口，并继承指定的类。 当编译器遇到约束列表时，它需要已定义的接口和类。 创建泛型类型的代码提供的适当类型实参替换类型形参之前，不将其视为已定义的类型。  
  
 **错误 ID：**BC32113  
  
### 更正此错误  
  
1.  检查约束列表中类型形参及其约束的拼写。  
  
2.  如果没有拼写错误，请从类型形参约束列表中删除其名称。 不能将其约束为其自身。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)