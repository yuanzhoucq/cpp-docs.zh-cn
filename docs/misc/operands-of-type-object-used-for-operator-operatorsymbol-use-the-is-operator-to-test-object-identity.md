---
title: "对运算符“&lt;operatorsymbol&gt;”使用了 Object 类型的操作数；应使用“Is”运算符来测试对象标识 | Microsoft Docs"
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
  - "vbc42018"
  - "BC42018"
helpviewer_keywords: 
  - "BC42018"
ms.assetid: 3fc640a7-7dab-4c14-b25d-a5794dbba59d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 对运算符“&lt;operatorsymbol&gt;”使用了 Object 类型的操作数；应使用“Is”运算符来测试对象标识
表达式将 [Object 数据类型](../Topic/Object%20Data%20Type.md) 与 `=` 的一个或两个操作数一起使用。  
  
 应使用 `Is` 或 `IsNot` 运算符来确定是否两个对象引用都指向同一对象实例。 请参阅 [比较运算符 \(Visual Basic\)](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md) 中的“比较对象”。  
  
 当变量或表达式的计算结果为 `Object` 时，编译器必须执行*后期绑定*，这将导致在运行时产生额外的操作。 它还使应用程序易于发生潜在的运行时错误。 例如，如果你将 <xref:System.Windows.Forms.Form> 分配到 `Object` 变量，然后尝试将其与 `=` 运算符一起使用，那么运行时会引发 <xref:System.InvalidCastException>，因为 Visual Basic 不能将 <xref:System.Windows.Forms.Form> 对象转换为适用于值比较的数据类型。 即使两个操作数的计算结果都为类型 <xref:System.Windows.Forms.Form>，操作也将因没有为 <xref:System.Windows.Forms.Form> 操作数定义 `=` 而失败。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [在 Visual Basic 中配置警告](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md)。  
  
 **错误 ID：**BC42018  
  
### 更正此错误  
  
-   如果你希望确定两个对象引用是否引用相同的对象实例，请使用 `Is` 或 `IsNot` 运算符。  
  
## 请参阅  
 [比较运算符 \(Visual Basic\)](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)   
 [Is 运算符](../Topic/Is%20Operator%20\(Visual%20Basic\).md)   
 [如何：确定两个对象是否相关](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Related%20\(Visual%20Basic\).md)   
 [如何：确定两个对象是否相同](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Identical%20\(Visual%20Basic\).md)