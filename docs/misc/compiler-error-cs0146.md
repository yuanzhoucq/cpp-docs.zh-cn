---
title: "编译器错误 CS0146 | Microsoft Docs"
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
  - "CS0146"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0146"
ms.assetid: 2be796e5-da2c-4939-af12-3145cd1828c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0146
涉及“class1”和“class2”的循环基类依赖项  
  
 类的继承列表包括对其自身的直接或间接引用。 类不能从其自身继承。 有关详细信息，请参阅[继承](../Topic/Inheritance%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0146：  
  
```  
// CS0146.cs namespace MyNamespace { public interface InterfaceA { } public class MyClass : InterfaceA, MyClass2 { public void Main() { } } public class MyClass2 : MyClass   // CS0146 { } }  
```