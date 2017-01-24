---
title: "编译器错误 CS0155 | Microsoft Docs"
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
  - "CS0155"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0155"
ms.assetid: 6c92984a-2b10-453e-9cb7-e6a1d1b98aa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0155
捕获或抛弃的类型必须从 System.Exception 派生  
  
 尝试将不是派生自 **System.Exception** 的数据类型传递到 [catch](../Topic/try-catch%20\(C%23%20Reference\).md) 块中。 只有派生自 **System.Exception** 的数据类型才能传递到 **catch** 块中。 有关详细信息，请参阅[异常处理语句](../Topic/Exception%20Handling%20Statements%20\(C%23%20Reference\).md)和[异常和异常处理](../Topic/Exceptions%20and%20Exception%20Handling%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0155：  
  
```  
// CS0155.cs using System; namespace MyNamespace { public class MyClass2 // try the following line instead // public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } catch (MyClass2)   // CS0155, resolves if you derive MyClass2 from Exception { } } } }  
```