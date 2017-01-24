---
title: "在 Imports 别名上不允许使用类型字符 | Microsoft Docs"
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
  - "vbc31398"
  - "BC31398"
helpviewer_keywords: 
  - "BC31398"
ms.assetid: 0620669d-b529-49f3-9deb-aeda4dacc58a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在 Imports 别名上不允许使用类型字符
`Imports` 语句中的导入别名包含至少一个标识符类型字符。  
  
 导入别名必须是有效的 Visual Basic 名称。 允许使用的字符不包括任何标识符类型字符（`%`、`&`、`@`、`!`、`#` 和 `$`）。 请参阅 [已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)。  
  
 **错误 ID：**BC31398  
  
### 更正此错误  
  
-   从导入别名中删除类型标识符字符。  
  
## 请参阅  
 [类型字符](../Topic/Type%20Characters%20\(Visual%20Basic\).md)   
 [已声明的元素名称](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Imports 语句（.NET 命名空间和类型）](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)   
 [NOTINBUILD：当多个变量具有相同名称时解析引用](http://msdn.microsoft.com/zh-cn/9601e39f-1911-44e1-ace5-3f6e090408b9)