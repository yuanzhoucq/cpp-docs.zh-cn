---
title: "无法从委托“&lt;delagateName&gt;”推断出在“&lt;typeName&gt;”中定义的扩展方法“&lt;methodName&gt;”的类型参数 | Microsoft Docs"
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
  - "bc36581"
  - "vbc36581"
helpviewer_keywords: 
  - "BC36581"
ms.assetid: 2bb9ca8d-7293-40e9-9285-e20b8254b3af
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法从委托“&lt;delagateName&gt;”推断出在“&lt;typeName&gt;”中定义的扩展方法“&lt;methodName&gt;”的类型参数
赋值语句使用 `AddressOf` 将泛型扩展方法的地址分配给委托，但它不向该扩展方法提供任何类型参数。  
  
 在调用泛型方法时，通常会为该泛型方法所定义的每个类型形参提供类型实参。 如果未提供任何类型实参，编译器将尝试推断要传递给类型形参的类型。 如果上下文未提供充足的信息供编译器推断类型，则将生成错误。  
  
 **错误 ID：**BC36581  
  
### 更正此错误  
  
-   在 `AddressOf` 表达式中，为扩展方法指定类型实参。  
  
## 请参阅  
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [AddressOf 运算符](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型过程](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [扩展方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)