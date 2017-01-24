---
title: "类型“&lt;typeparametername&gt;”是没有类约束的类型参数，因此类型“&lt;typeparametername&gt;”的 &quot;Is&quot; 操作数只能与 &quot;Nothing&quot; 比较 | Microsoft Docs"
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
  - "vbc32052"
  - "bc32052"
helpviewer_keywords: 
  - "BC32052"
ms.assetid: 0bbf2249-eb0d-4b74-a555-8868c7ebe91d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 类型“&lt;typeparametername&gt;”是没有类约束的类型参数，因此类型“&lt;typeparametername&gt;”的 &quot;Is&quot; 操作数只能与 &quot;Nothing&quot; 比较
如果定义的类型形参在其约束列表中没有 [Class \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) 关键字或特定类名，则该类型形参可以用作 [Is 运算符](../Topic/Is%20Operator%20\(Visual%20Basic\).md) 的操作数。  
  
 `Is` 比较两个引用类型以确定它们是否指向内存中的同一个对象实例。 它无法接受非引用类型的操作数，除非另一个操作数是 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)。  
  
 **错误 ID：**BC32052  
  
### 更正此错误  
  
-   如果你可以要求提供给此类型形参的类型实参始终是引用类型，请将 `Class` 关键字或特定的类名称添加到该类型形参的约束列表中。  
  
-   如果你不能要求提供给此类型形参的类型实参始终是引用类型，请将其从 `Is` 表达式中删除。 不能使用 `Is` 运算符将其与其他引用类型进行比较。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [值类型和引用类型](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [比较运算符 \(Visual Basic\)](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)