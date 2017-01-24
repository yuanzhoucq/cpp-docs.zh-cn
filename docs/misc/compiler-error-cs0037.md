---
title: "编译器错误 CS0037 | Microsoft Docs"
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
  - "CS0037"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0037"
ms.assetid: 1d34a71e-10a0-4fa8-9b94-343e69428c61
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0037
无法将 null 转换成“type”，因为它是不可以为 null 的值类型  
  
 编译器无法将 null 分配到值类型；仅可将 null 分配到[引用类型](../Topic/Reference%20Types%20\(C%23%20Reference\).md)或可以为 null 的类型。[struct](../Topic/struct%20\(C%23%20Reference\).md) 是一个值类型。 有关详细信息，请参阅[可以为 null 的类型](../Topic/Nullable%20Types%20\(C%23%20Programming%20Guide\).md)。  
  
 下面的示例生成 CS0037：  
  
```  
// CS0037.cs public struct s { } class a { public static void Main() { int i = null;   // CS0037 s ss = null;    // CS0037 } }  
```