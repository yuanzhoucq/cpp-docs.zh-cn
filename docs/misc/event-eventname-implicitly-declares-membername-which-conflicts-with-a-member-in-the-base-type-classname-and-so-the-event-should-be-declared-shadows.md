---
title: "事件“&lt;eventname&gt;”隐式声明的“&lt;membername&gt;”与基&lt;type&gt;“&lt;classname&gt;”中的某个成员冲突，因此应将该事件声明为“Shadows”。 | Microsoft Docs"
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
  - "bc40012"
  - "vbc40012"
helpviewer_keywords: 
  - "BC40012"
ms.assetid: 5f14e8bd-a227-4115-af99-cd2b6fe4dc0e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 事件“&lt;eventname&gt;”隐式声明的“&lt;membername&gt;”与基&lt;type&gt;“&lt;classname&gt;”中的某个成员冲突，因此应将该事件声明为“Shadows”。
事件由一个名称进行声明，该名称组合形成一个与基类成员具有相同名称的隐式成员。 例如，如果你声明一个名为 `Event1` 的事件，则编译器将生成隐式过程 `add_Event1` 和 `remove_Event1`。 如果基类中存在具有这些名称的成员，此类中的事件应隐藏基类成员。  
  
 此消息是一个警告。 默认假定 `Shadows`。 有关隐藏警告或将警告视为错误的详细信息，请参阅 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC40012  
  
### 更正此错误  
  
1.  若要隐藏基类成员，请将 `Shadows` 关键字添加到事件声明中。  
  
2.  如果不打算隐藏基类成员，请更改事件名称。  
  
## 请参阅  
 [Event 语句](../Topic/Event%20Statement.md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Visual Basic 中的隐藏](../Topic/Shadowing%20in%20Visual%20Basic.md)