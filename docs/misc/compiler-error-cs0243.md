---
title: "编译器错误 CS0243 | Microsoft Docs"
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
  - "CS0243"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0243"
ms.assetid: 2506e4cb-dc26-46b4-a58c-ab6bf1601144
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0243
Conditional 特性在“method”上无效，因为它是重写方法  
  
 在标记有 [override](../Topic/override%20\(C%23%20Reference\).md) 关键字的方法上不允许使用 [Conditional](http://msdn.microsoft.com/zh-cn/e1c4913b-74d0-421a-8a6d-c14b3f0e68fb) 特性。 有关详细信息，请参阅[了解何时使用 Override 和 New 关键字](../Topic/Knowing%20When%20to%20Use%20Override%20and%20New%20Keywords%20\(C%23%20Programming%20Guide\).md)。  
  
 编译器从不绑定到重写方法；它只绑定到基方法，而且公共语言运行库在适当的时候调用重写。  
  
 下面的示例生成 CS0243：  
  
```  
// CS0243.cs // compile with: /target:library public class MyClass { public virtual void M() {} } public class MyClass2 : MyClass { [System.Diagnostics.ConditionalAttribute("MySymbol")]   // CS0243 // remove Conditional attribute or remove override keyword public override void M() {} }  
```