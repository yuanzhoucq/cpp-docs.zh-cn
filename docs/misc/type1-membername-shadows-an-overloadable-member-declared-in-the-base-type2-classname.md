---
title: "&lt;类型1&gt;“&lt;成员名称&gt;”隐藏了在基&lt;类型2&gt;“&lt;类名称&gt;”中声明的可重载成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40003"
  - "vbc40003"
helpviewer_keywords: 
  - "BC40003"
ms.assetid: 1e0d2061-0ad9-4915-b946-d55cb5d5ee80
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;类型1&gt;“&lt;成员名称&gt;”隐藏了在基&lt;类型2&gt;“&lt;类名称&gt;”中声明的可重载成员
\<类型1\>“\<成员名称\>”隐藏了在基\<类型2\>“\<类名称\>”中声明的可重载成员。 若要重载基方法，必须将此方法声明为“Overloads”。  
  
 派生的类以基类中定义的过程或属性的相同名称来定义 `Function` 或 `Sub` 过程或 `Property`。 因为过程和属性都是可重载的成员，派生类可以重载或隐藏基类成员。 但是，派生的类代码未在声明中指定任何 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) 或 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)。 在没有关键字的情况下，编译器将假定 `Shadows`。  
  
 指定 `Overloads` 或 `Shadows` 是一个良好的编程做法。 这使得你的代码易于阅读和理解。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参阅 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC40003  
  
### 更正此错误  
  
-   如果想要重载基类方法或属性，请将 `Overloads` 关键字包括在声明中。  
  
-   如果想要重载基类方法或属性，请将 `Shadows` 关键字而非 `Overloads` 包括在声明中。  
  
-   如果不想重载或隐藏基类成员，则更改派生类成员的名称。  
  
## 请参阅  
 [过程重载](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Visual Basic 中的隐藏](../Topic/Shadowing%20in%20Visual%20Basic.md)   
 [Function 语句](../Topic/Function%20Statement%20\(Visual%20Basic\).md)   
 [Sub 语句](../Topic/Sub%20Statement%20\(Visual%20Basic\).md)   
 [Property 语句](../Topic/Property%20Statement.md)