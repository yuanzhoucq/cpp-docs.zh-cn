---
title: "接口“&lt;interfacename&gt;”的实现类“&lt;underlyingclassname&gt;”在此上下文中不可访问，因为它是“&lt;accesslevel&gt;” | Microsoft Docs"
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
  - "BC31109"
  - "vbc31109"
helpviewer_keywords: 
  - "BC31109"
ms.assetid: ab2a3bc3-b875-476f-b601-3e736ad2677e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 接口“&lt;interfacename&gt;”的实现类“&lt;underlyingclassname&gt;”在此上下文中不可访问，因为它是“&lt;accesslevel&gt;”
使用 <xref:System.Runtime.InteropServices.CoClassAttribute> 指定基础类从而声明了接口，但该类的访问级别阻止使用方代码访问它。  
  
 向接口应用 <xref:System.Runtime.InteropServices.CoClassAttribute> 将使基础类与该接口关联。 这允许代码使用 `New` 子句从接口直接创建对象。  
  
 如果使用 `New` 子句的代码不能访问该基础类（例如，如果此类是 `Private`），则编译器将产生此错误。  
  
 **错误 ID：**BC31109  
  
### 更正此错误  
  
1.  如果你可以对基础类进行源代码管理，可调整其访问级别，让使用方代码能够访问它。  
  
2.  如果你由于任何原因不能更改基础类的访问级别，请删除 `New` 子句。 不能从此接口直接创建对象。  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.CoClassAttribute>   
 [New 运算符](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [Visual Basic 中的访问级别](../Topic/Access%20Levels%20in%20Visual%20Basic.md)