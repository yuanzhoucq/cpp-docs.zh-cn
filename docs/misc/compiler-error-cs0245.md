---
title: "编译器错误 CS0245 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0245"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0245"
ms.assetid: 3f2beb2f-a510-4568-9d11-bb1f65066acd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0245
无法直接调用析构函数和 object.Finalize。 请考虑调用 IDisposable.Dispose（如果可用）。  
  
 有关详细信息，请参阅[垃圾回收的编程原理](../Topic/Garbage%20Collection.md)和 [析构函数](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0245：  
  
```  
// CS0245.cs using System; using System.Collections; class MyClass // : IDisposable { /* public void Dispose() { // cleanup code goes here } */ void m() { this.Finalize();   // CS0245 // this.Dispose(); } public static void Main() { } }  
```