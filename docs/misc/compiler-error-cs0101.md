---
title: "编译器错误 CS0101 | Microsoft Docs"
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
  - "CS0101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0101"
ms.assetid: edb5246b-c16b-4845-bb2d-0ef769d014c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0101
命名空间“namespace”已经包含“type”的定义  
  
 [namespace](../Topic/namespace%20\(C%23%20Reference\).md) 具有重复的标识符。 重命名或删除其中一个重复的标识符。 有关详细信息，请参阅[命名空间](../Topic/Namespaces%20\(C%23%20Programming%20Guide\).md)。  
  
 以下示例生成 CS0101：  
  
```  
// CS0101.cs namespace MyNamespace { public class MyClass { static public void Main() { } } public class MyClass   // CS0101 { } }  
```