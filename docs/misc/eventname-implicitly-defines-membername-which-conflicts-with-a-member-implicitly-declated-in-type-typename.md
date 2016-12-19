---
title: "“&lt;eventname&gt;”隐式定义了“&lt;membername&gt;”，这与在&lt;type&gt;“&lt;typename&gt;”中隐式声明的某个成员冲突 | Microsoft Docs"
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
  - "bc31059"
  - "vbc31059"
helpviewer_keywords: 
  - "BC31059"
ms.assetid: 60ddb2f4-a204-41eb-b13b-b2bb13ddb69c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;eventname&gt;”隐式定义了“&lt;membername&gt;”，这与在&lt;type&gt;“&lt;typename&gt;”中隐式声明的某个成员冲突
类型成员名称与为事件隐式创建的成员名称冲突。 事件隐式创建了多个变量。 例如，声明 `Event X` 隐式声明了名称 `XEventHandler`、`XEvent`、`add_X` 和 `remove_X`。  
  
 **错误 ID：**BC31059  
  
### 更正此错误  
  
-   重命名显式声明的成员，以消除命名冲突。  
  
## 请参阅  
 [NotInBuild：Visual Basic 中的声明语句](http://msdn.microsoft.com/zh-cn/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [事件](../Topic/Events%20\(Visual%20Basic\).md)