---
title: "无法在“NotOverridable”属性中将属性访问器声明为“&lt;accessmodifier&gt;” | Microsoft Docs"
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
  - "vbc31106"
  - "bc31106"
helpviewer_keywords: 
  - "BC31106"
ms.assetid: 84bcb157-9c33-4e4f-89a9-c5e6cb73028b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法在“NotOverridable”属性中将属性访问器声明为“&lt;accessmodifier&gt;”
`NotOverridable` 属性中的 [Get 语句](../Topic/Get%20Statement.md) 或 [Set 语句](../Topic/Set%20Statement%20\(Visual%20Basic\).md) 包括 `Private` 关键字。  
  
 以下推理行解释了[Property 语句](../Topic/Property%20Statement.md)中不可同时包含 `NotOverridable` 和 `Private` 的原因：  
  
1.  不重写基类属性（或过程）的属性（或过程）具有 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md) 这一默认设置。  
  
2.  但是，对于派生类中重写基类属性（或过程）的属性（或过程），其默认设置为 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)。 若要终止重写层次结构，可将其声明为 `NotOverridable`。 这是唯一可使用 `NotOverridable` 的上下文。 也就是说，你只能将 `NotOverridable` 和 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md) 结合使用。  
  
3.  如果基类属性或过程声明为 [Private](../Topic/Private%20\(Visual%20Basic\).md)，则派生类无法访问此属性或过程，因而不能重写它。 因此，不能结合使用 `Private` 和 `Overridable`。  
  
4.  若要重写属性或过程，则重写的属性或过程必须具有相同签名及相同的访问级别。 这意味着，重写的属性或过程不能指定 `Private`，因为可重写的属性或过程不能指定 `Private`。  
  
5.  因为你只可在重写的属性或过程上指定 `NotOverridable`，因此不能将其与 `Private` 结合使用。  
  
 同理，重写属性的个别属性过程（`Get` 和 `Set`）不能为 `Private`。  
  
 **错误 ID：**BC31106  
  
### 更正此错误  
  
-   删除 `Get` 或 `Set` 语句中的 `Private` 关键字，或者删除 `Property` 语句中的 `Overrides` 和 `NotOverridable` 关键字。  
  
## 请参阅  
 [Property 过程](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [隐藏和重写之间的差异](../Topic/Differences%20Between%20Shadowing%20and%20Overriding%20\(Visual%20Basic\).md)   
 [如何：声明具有混合访问级别的属性](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)