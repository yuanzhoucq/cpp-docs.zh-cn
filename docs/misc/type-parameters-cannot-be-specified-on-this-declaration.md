---
title: "在此声明上不能指定类型参数 | Microsoft Docs"
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
  - "vbc32065"
  - "bc32065"
helpviewer_keywords: 
  - "BC32065"
ms.assetid: 94cfe3de-74fd-4a2c-9246-ec4a05b73d55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在此声明上不能指定类型参数
编程元素可以使用类型参数列表进行声明，但是编程元素不可作为泛型类型。  
  
 不可作为泛型的编程元素包括属性、运算符、事件和构造函数。 使用类型参数列表声明的任何这些元素会导致此错误。  
  
 **错误 ID：**BC32065  
  
### 更正此错误  
  
-   从声明中删除 `Of` 关键字和类型参数。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)