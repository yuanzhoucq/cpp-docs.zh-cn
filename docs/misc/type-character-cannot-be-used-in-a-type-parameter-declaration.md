---
title: "在类型参数声明中不能使用类型字符。 | Microsoft Docs"
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
  - "vbc32041"
  - "bc32041"
helpviewer_keywords: 
  - "BC32041"
ms.assetid: 24f9a514-f3d4-46c3-805c-71225f6fec59
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在类型参数声明中不能使用类型字符。
类型参数声明包含至少一个标识符类型字符。  
  
 泛型类型的类型参数必须是有效的 Visual Basic 名称。 允许使用的字符不包括任何标识符类型字符（`%`、`&`、`@`、`!`、`#` 和 `$`）。 请参阅 [已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)。  
  
 **错误 ID：**BC32041  
  
### 更正此错误  
  
-   从类型参数声明中删除类型标识符字符。  
  
## 请参阅  
 [类型字符](../Topic/Type%20Characters%20\(Visual%20Basic\).md)   
 [已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)