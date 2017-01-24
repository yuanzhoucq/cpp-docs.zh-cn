---
title: "编译器错误 CS0713 | Microsoft Docs"
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
  - "CS0713"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0713"
ms.assetid: 27a46765-d982-43ba-909f-9278e26b80d2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0713
静态类“static type”不能从类型“type”派生。 静态类必须从对象派生。  
  
 如果允许这样做，静态类将从基类继承方法和非静态成员，因此它不会是静态的。 因此，不允许这样做。  
  
 下面的示例生成 CS0713：  
  
```  
// CS0713.cs public class Base { } public static class Derived : Base  // CS0713 { } public class CMain { public static void Main() { } }  
```