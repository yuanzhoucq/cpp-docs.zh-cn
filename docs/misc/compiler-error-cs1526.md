---
title: "编译器错误 CS1526 | Microsoft Docs"
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
  - "CS1526"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1526"
ms.assetid: 92feeb9f-e577-4c08-b12b-c19822857200
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1526
new 表达式要求在类型后有 \(\)、\[\] 或 {}  
  
 未正确指定用于为对象动态分配内存的 [new](../Topic/new%20\(C%23%20Reference\).md) 运算符。  
  
## 示例  
 下面的示例演示如何使用 `new` 为数组和对象分配空间。  
  
```  
// CS1526.cs public class y { public static int i = 0; public int myi = 0; } public class z { public static void Main() { y py = new y;   // CS1526 y[] aoys = new y[10];   // Array of Ys for (int i = 0; i < aoys.Length; i++) aoys[i] = new y();   // an object of type y } }  
```