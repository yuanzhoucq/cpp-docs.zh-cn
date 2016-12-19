---
title: "不能为分部类型“&lt;partialtypename&gt;”指定“MustInherit”，因为它不能与对其其他分部类型之一指定的“NotInheritable”进行组合 | Microsoft Docs"
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
  - "vbc30926"
  - "BC30926"
helpviewer_keywords: 
  - "BC30926"
ms.assetid: 59a0b5d9-f53c-4234-88f4-dfc66342f143
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能为分部类型“&lt;partialtypename&gt;”指定“MustInherit”，因为它不能与对其其他分部类型之一指定的“NotInheritable”进行组合
在多个分部声明中定义一个类，这些分部声明之一指定 `MustInherit`，另一个指定 `NotInheritable`。  
  
 在多个分部声明间划分类的定义时，编译器会将该类视为它的所有分部声明的联合。 这不仅适用于成员，还适用于实现、继承和访问级别。  
  
 类不能同时为*“抽象”*和*“密封”*，意味着它不能同时要求和禁止继承。 因此你不能为同一个类同时指定 `MustInherit` 和 `NotInheritable`。  
  
 **错误 ID：**BC30926  
  
### 更正此错误  
  
-   确定该类是否需要继承、禁止继承，还是两者皆非，然后删除不适合于你的决定的关键字。  
  
## 请参阅  
 [分部](../Topic/Partial%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md)   
 [继承的基础知识](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)