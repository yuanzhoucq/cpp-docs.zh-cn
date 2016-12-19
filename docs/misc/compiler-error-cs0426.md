---
title: "编译器错误 CS0426 | Microsoft Docs"
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
  - "CS0426"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0426"
ms.assetid: 62df0deb-3624-436e-9691-ebe3ee1fc31f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0426
类型“type”中不存在类型名称“identifier”  
  
 引用嵌套在另一类型中的类型而这一嵌套类型不存在时，会出现此错误。 键错嵌套类型的名称时可能出现此错误。 检查所用名称的拼写，并验证外层类型具有所需成员。  
  
 下面的示例生成 CS0426，因为类 C 不具有嵌套类型 A：  
  
```  
// CS0426.cs class C { // No nested types are declared. } class D { public static void Main() { C c = new C(); // Attempt to reference a nested type A: C.A a; // CS0426 because no such type C.A } }  
```  
  
## 请参阅  
 [类和结构](../Topic/Classes%20and%20Structs%20\(C%23%20Programming%20Guide\).md)