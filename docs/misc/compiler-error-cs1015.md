---
title: "编译器错误 CS1015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1015"
ms.assetid: 53179feb-e8be-41e0-bb0b-f7879e9fa613
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1015
应是对象、字符串或类类型  
  
 尝试将预定义的数据类型传入 [catch](../Topic/try-catch%20\(C%23%20Reference\).md) 块。 仅派生自 <xref:System.Exception?displayProperty=fullName> 的数据类型可传入 `catch` 块。 有关异常的详细信息，请参阅[异常处理语句](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)。  
  
## 示例  
 下面的示例生成 CS1015：  
  
```  
// CS1015.cs class Sample { static void Main() { try { } catch(int)   // CS1015, int is not derived from System.Exception { } } }  
```