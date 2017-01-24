---
title: "无法推断“&lt;typename&gt;”中定义的扩展方法“&lt;methodname&gt;”的类型参数“&lt;typeparametername&gt;” | Microsoft Docs"
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
  - "vbc36589"
  - "bc36589"
helpviewer_keywords: 
  - "BC36589"
ms.assetid: 4676a7a5-934b-4b74-b640-48065fc07e94
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法推断“&lt;typename&gt;”中定义的扩展方法“&lt;methodname&gt;”的类型参数“&lt;typeparametername&gt;”
在未提供类型参数列表的情况下调用泛型扩展方法，某一个类型参数的类型推理失败。  
  
 在调用泛型过程时，通常会为过程所定义的每个类型形参提供类型实参。 但是，还可以选择忽略整个类型实参列表。 执行此操作时，编译器将尝试推断调用上下文中每个类型实参的类型。 有关详细信息，请参见 [Visual Basic 中的泛型过程](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md) 中的“类型推理”。  
  
 **错误 ID：** BC36589  
  
### 更正此错误  
  
-   确保普通参数的类型是这样的：类型推理与为泛型过程声明的类型形参一致。  
  
     \- 或 \-  
  
-   调用具有完整类型实参列表的泛型过程，因此就不需要类型推理。  
  
## 请参阅  
 [扩展方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型过程](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)