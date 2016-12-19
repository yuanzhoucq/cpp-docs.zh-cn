---
title: "编译器错误 CS1023 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1023"
ms.assetid: 27d70f2c-9ae1-459c-a6be-01ed5a3eea07
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1023
嵌入的语句不能是声明或标记语句  
  
 嵌入语句（如跟在 **if** 语句后面的语句）不能包含声明，也不能包含标记语句。  
  
 下面的示例生成 CS1023 两次：  
  
```  
// CS1023.cs public class a { public static void Main() { if (1) int i;      // CS1023, declaration is not valid here if (1) xx : i++;   // CS1023, labeled statement is not valid here } }  
```