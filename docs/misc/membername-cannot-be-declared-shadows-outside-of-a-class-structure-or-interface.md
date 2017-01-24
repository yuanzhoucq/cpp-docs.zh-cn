---
title: "“&lt;membername&gt;”不能在类、结构或接口外声明为“Shadows”。 | Microsoft Docs"
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
  - "bc32200"
  - "vbc32200"
helpviewer_keywords: 
  - "BC32200"
ms.assetid: 23e28894-5854-46ef-924d-f1cb6e81bcb1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;membername&gt;”不能在类、结构或接口外声明为“Shadows”。
`Shadows` 关键字出现在命名空间、模块或文件级别的声明中。 隐藏仅在可从基元素继承的编程元素内有意义。  
  
 **错误 ID：**BC32200  
  
### 更正此错误  
  
-   删除 `Shadows` 关键字，或在类、结构或接口内部移动声明。  
  
## 请参阅  
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Visual Basic 中的隐藏](../Topic/Shadowing%20in%20Visual%20Basic.md)