---
title: "无法将“&lt;propertyname&gt;”作为“Let”属性向 COM 公开 | Microsoft Docs"
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
  - "bc42102"
  - "vbc42102"
helpviewer_keywords: 
  - "BC42102"
ms.assetid: b77c5b7c-ac43-4b2d-b8bc-582e65e6f7e7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法将“&lt;propertyname&gt;”作为“Let”属性向 COM 公开
无法将“\<propertyname\>”作为“Let”属性向 COM 公开。 你将无法使用“Let”语句从 Visual Basic 6.0 向该属性分配非对象值（如数字或字符串）。  
  
 使用 `COMClassAttribute` 特性块的类声明了具有数据类型 `Object` 的 `Public` 属性。 Visual Basic 6.0 程序可以作为 `Variant` 访问此属性，但是只能使用 `Set` 语句为其分配一个对象引用。 它不能使用 `Let` 语句分配值类型。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的详细信息，请参见 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC42102  
  
### 解决此警告  
  
-   请考虑通知此类可能的 Visual Basic 6.0 用户：他们不能通过 `Let` 语句使用此属性。  
  
## 请参阅  
 [Default Property Changes in Visual Basic](http://msdn.microsoft.com/zh-cn/9b8cfad7-40ac-4b83-affb-1ff781755a4c)   
 [Property 语句](../Topic/Property%20Statement.md)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)   
 [Object 数据类型](../Topic/Object%20Data%20Type.md)   
 [不在生成中：Visual Basic 中使用的特性](http://msdn.microsoft.com/zh-cn/22231318-8a40-49af-9245-e0aab723563b)   
 [不在生成中：特性的应用程序](http://msdn.microsoft.com/zh-cn/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute 类](http://msdn.microsoft.com/zh-cn/5c2f0835-9210-47dc-bc59-5c1769953574)