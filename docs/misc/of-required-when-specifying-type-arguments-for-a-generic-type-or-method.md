---
title: "在指定泛型类型或方法的类型实参时需要“Of” | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32093"
  - "vbc32093"
helpviewer_keywords: 
  - "BC32093"
ms.assetid: 9a1baf12-a4a4-442d-9baa-852ad30a956b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在指定泛型类型或方法的类型实参时需要“Of”
某个语句尝试通过泛型类型构造类型，或调用泛型方法，而未使用 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md) 子句。  
  
 泛型类型的 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 语法需要通过 `Of` 关键字引入类型形参和类型实参。 此外，类型形参列表或类型实参列表必须括在括号内。  
  
 **错误 ID：**BC32093  
  
### 更正此错误  
  
-   在类型实参列表开头包含 `Of` 关键字，并将整个列表括在括号内。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [如何：使用泛型类](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)