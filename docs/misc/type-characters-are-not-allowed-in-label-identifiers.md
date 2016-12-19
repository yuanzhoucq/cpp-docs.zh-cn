---
title: "标签标识符中不允许使用类型字符 | Microsoft Docs"
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
  - "BC31395"
  - "vbc31395"
helpviewer_keywords: 
  - "BC31395"
ms.assetid: 6c65dd06-1ff1-49d3-b698-3afb21a39f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 标签标识符中不允许使用类型字符
语句标签包含至少一个标识符类型字符。  
  
 语句标签必须是有效的 Visual Basic 名称。 允许使用的字符不包括任何标识符类型字符（`%`、`&`、`@`、`!`、`#` 和 `$`）。 请参阅 [已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)。  
  
 **错误 ID：**BC31395  
  
### 更正此错误  
  
-   从语句标签中删除类型标识符字符。  
  
## 请参阅  
 [类型字符](../Topic/Type%20Characters%20\(Visual%20Basic\).md)   
 [已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [如何：标记语句](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)