---
title: "编译器错误 CS0027 | Microsoft Docs"
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
  - "CS0027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0027"
ms.assetid: 3a599876-9643-4c68-9457-3306858a73e9
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0027
关键字 "this" 在当前上下文中不可用  
  
 在属性、方法或构造函数的外部发现了 [this](../Topic/this%20\(C%23%20Reference\).md) 关键字。  
  
 若要修复此错误，请修改语句以消除 `this` 关键字，关键字的使用，并且\/或者将语句的一部分或全部移到属性、方法或构造函数的内部。  
  
 下面的示例生成 CS0027：  
  
```  
using System; using System.Collections.Generic; using System.Text; namespace ConsoleApplication3 { class MyClass { int err1 = this.Fun() + 1;  // CS0027 public int Fun() { return 10; } public void Test() { // valid use of this int err = this.Fun() + 1; Console.WriteLine(err); } public static void Main() { MyClass c = new MyClass(); c.Test(); } } }  
```