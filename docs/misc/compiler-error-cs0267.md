---
title: "编译器错误 CS0267 | Microsoft Docs"
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
  - "CS0267"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0267"
ms.assetid: 11aaab96-5838-4e36-9551-5b032a1089e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0267
partial 修饰符的后面只能紧跟“class”、“struct”或“interface”  
  
 **partial** 修饰符在 class、struct 或 interface 声明中的位置错误。 要修复错误，请重新排列修饰符。 有关更多信息，请参见[分部类和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0267：  
  
```  
// CS0267.cs public partial class MyClass { public MyClass() { } } partial public class MyClass  // CS0267 // Try this line instead: // public partial class MyClass { public void Foo() { } public static void Main() { } }  
```