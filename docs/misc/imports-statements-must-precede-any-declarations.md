---
title: "“Imports”语句必须位于任何声明之前 | Microsoft Docs"
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
  - "vbc30465"
  - "bc30465"
helpviewer_keywords: 
  - "BC30465"
ms.assetid: 726365f6-d6fc-454a-a43b-afa41bfea82a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “Imports”语句必须位于任何声明之前
`Imports` 语句位于源文件中的声明语句之后。  
  
 `Imports` 语句从被引用项目和程序集导入命名空间名称，以及在它所出现的项目中定义的命名空间名称。`Imports` 语句必须置于源代码文件中的任何标识符引用之前。  
  
 **错误 ID：**BC30465  
  
### 更正此错误  
  
-   将 `Imports` 语句移动到源文件顶部任何声明语句之前。  
  
## 请参阅  
 [Imports 语句（.NET 命名空间和类型）](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)