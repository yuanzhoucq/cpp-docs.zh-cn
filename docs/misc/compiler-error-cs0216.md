---
title: "编译器错误 CS0216 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0216"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0216"
ms.assetid: afb3dd29-3eff-4b62-8267-eb726c2bcee4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0216
运算符“operator”要求也要定义匹配的运算符“missing\_operator”  
  
 用户定义的 [true](../Topic/true%20\(C%23%20Reference\).md) 运算符要求用户定义 [false](../Topic/false%20\(C%23%20Reference\).md) 运算符，反之亦然。 有关详细信息，请参阅[运算符](../Topic/Operators%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0216：  
  
```  
// CS0216.cs class MyClass { public static bool operator true (MyClass MyInt)   // CS0216 { return true; } // to resolve, uncomment the following operator definition /* public static bool operator false (MyClass MyInt) { return true; } */ public static void Main() { } }  
```