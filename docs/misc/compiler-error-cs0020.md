---
title: "编译器错误 CS0020 | Microsoft Docs"
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
  - "CS0020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0020"
ms.assetid: 7a54db39-6530-4e34-aa17-a90f85223d08
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0020
被常数零除  
  
 表达式在除法运算的分母中使用了文本（不是变量）值零。 未定义除数为零，因此无效。  
  
 下面的示例生成 CS0020:  
  
```  
// CS0020.cs namespace x { public class b { public static void Main() { 1 / 0;   // CS0020 } } }  
```  
  
## 请参阅  
 [运算符](../Topic/Operators%20\(C%23%20Programming%20Guide\).md)