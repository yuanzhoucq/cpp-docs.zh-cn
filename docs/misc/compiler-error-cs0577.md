---
title: "编译器错误 CS0577 | Microsoft Docs"
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
  - "CS0577"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0577"
ms.assetid: 34f8f453-f016-4f2c-981a-0d61449cd74b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0577
Conditional 特性对“function”无效，因为它是构造函数、析构函数、运算符或显式接口实现  
  
 `Conditional` 无法应用于指定的方法。  
  
 例如，你无法对显式接口定义使用某些特性。 下面的示例生成 CS0577：  
  
```  
// CS0577.cs // compile with: /target:library interface I { void m(); } public class MyClass : I { [System.Diagnostics.Conditional("a")]   // CS0577 void I.m() {} }  
```