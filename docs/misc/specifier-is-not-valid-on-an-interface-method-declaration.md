---
title: "“&lt;specifier&gt;”在接口方法声明中无效 | Microsoft Docs"
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
  - "bc30270"
  - "vbc30270"
helpviewer_keywords: 
  - "BC30270"
ms.assetid: 598f2944-3e5d-4686-b6f7-2b4bcaf5c211
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;specifier&gt;”在接口方法声明中无效
接口内的 `Function` 或 `Sub` 语句包含无效的关键字，如 `Implements`。 接口只能定义成员，而不能实现它们。  
  
 **错误 ID：**BC30270  
  
### 更正此错误  
  
1.  从声明语句中删除无效的关键字。  
  
2.  将接口成员的实现移动到实现该接口的类。  
  
## 请参阅  
 [Interface 语句](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements 语句](../Topic/Implements%20Statement.md)