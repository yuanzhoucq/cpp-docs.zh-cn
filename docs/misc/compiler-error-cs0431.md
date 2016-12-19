---
title: "编译器错误 CS0431 | Microsoft Docs"
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
  - "CS0431"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0431"
ms.assetid: 05da7ea7-f33d-48d4-948e-d64be56f91ba
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0431
无法将别名“identifier”与“::”一起使用，因为该别名引用了类型。 请改用“.”。  
  
 同时使用了“::”与引用类型的别名。 若要解决此错误，请使用“.”运算符。  
  
 下面的示例生成 CS0431:  
  
```  
// CS0431.cs using A = Outer; public class Outer { public class Inner { public static void Meth() {} } } public class MyClass { public static void Main() { A::Inner.Meth();   // CS0431 A.Inner.Meth();   // OK } }  
```