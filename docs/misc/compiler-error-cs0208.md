---
title: "编译器错误 CS0208 | Microsoft Docs"
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
  - "CS0208"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0208"
ms.assetid: 03534893-1522-4dab-9822-8b9ed97b3bd0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0208
无法获取托管类型（“类型”）的地址和大小，也无法声明指向它的指针  
  
 即使使用 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md) 关键字，也不允许获取托管对象的地址和大小或声明指向托管类型的指针。 托管类型是：  
  
-   任何引用类型  
  
-   包含作为字段或属性的引用类型的任何结构  
  
 有关详细信息，请参见 [不安全代码和指针](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md) 和 [sizeof](../Topic/sizeof%20\(C%23%20Reference\).md)。  
  
## 示例  
 下面的示例生成 CS0208:  
  
```  
// CS0208.cs // compile with: /unsafe class myClass { public int a = 98; } struct myProblemStruct { string s; float f; } struct myGoodStruct { int i; float f; } public class MyClass { unsafe public static void Main() { // myClass is a class, a managed type. myClass s = new myClass(); myClass* s2 = &s;    // CS0208 // The struct contains a string, a managed type. int i = sizeof(myProblemStruct); //CS0208 // The struct contains only value types. i = sizeof(myGoodStruct); //OK } }  
  
```  
  
## 请参阅  
 [sizeof](../Topic/sizeof%20\(C%23%20Reference\).md)