---
title: "类型形参不能与其定义函数同名 | Microsoft Docs"
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
  - "vbc32090"
  - "bc32090"
helpviewer_keywords: 
  - "BC32090"
ms.assetid: 02f4d82c-dcd7-44cc-b725-81e235f680f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类型形参不能与其定义函数同名
所声明的泛型类型的类型形参与泛型类型同名。  
  
 在泛型类型的类型形参列表中，每个类型形参的名称必须与以下所有名称均不同：  
  
-   相同类型形参列表中的每个其他类型形参，  
  
-   在任何包含泛型类型的类型形参列表中的每个类型形参，以及  
  
-   泛型类型本身的名称。  
  
 **错误 ID:** BC32090  
  
### 更正此错误  
  
-   重命名类型形参，使其有别于此帮助页上的列表中引用的每个名称。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)