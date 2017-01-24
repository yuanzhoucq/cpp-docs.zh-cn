---
title: "编译器错误 CS0729 | Microsoft Docs"
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
  - "CS0729"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0729"
ms.assetid: e0421d06-e818-404f-af97-d101272f4d07
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0729
类型“type”是在此程序集中定义的，但又为它指定了一个类型转发器  
  
 类型转发器不能用于在同一程序集中定义的类型。  
  
## 示例  
 下面的示例生成 CS0729。  
  
```  
// CS0729.cs // compile with: /target:library using System.Runtime.CompilerServices; [assembly:TypeForwardedTo(typeof(TestClass))]   // CS0729 class TestClass {}  
```