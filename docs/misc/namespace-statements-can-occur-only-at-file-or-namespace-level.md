---
title: "“Namespace”语句只能出现在文件级或命名空间级 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30618"
  - "vbc30618"
helpviewer_keywords: 
  - "BC30618"
ms.assetid: bcd365a4-5d84-4c3c-83dc-40cb4c47f73b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Namespace”语句只能出现在文件级或命名空间级
`Namespace` 语句必须显示在 `Option` 语句、`Imports` 语句和全局特性之后，但在源文件中的所有其他声明之前。  
  
 **错误 ID：**BC30618  
  
### 更正此错误  
  
-   将 `Namespace` 语句移动到命名空间声明或源文件的顶部。  
  
## 请参阅  
 [Namespace 语句](../Topic/Namespace%20Statement.md)   
 [Visual Basic 中的命名空间](../Topic/Namespaces%20in%20Visual%20Basic.md)