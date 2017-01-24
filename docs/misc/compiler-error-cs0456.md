---
title: "编译器错误 CS0456 | Microsoft Docs"
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
  - "CS0456"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0456"
ms.assetid: d714ec06-a7f4-405e-bf32-423696848319
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0456
类型参数“Type Parameter Name 1”具有“struct”约束，因此“Type Parameter Name 1”不能用作“Type Parameter Name 2”的约束  
  
 值类型约束是隐式密封的，因此这些约束不能用作第二个类型参数的约束。 这是因为值类型不可重写。 若要解决此错误，直接将一个值类型约束用于第二个类型参数，而不是通过第一个类型参数间接进行。  
  
## 示例  
 下面的示例生成 CS0456。  
  
```  
// CS0456.cs // compile with: /target:library public class GenericsErrors { public class G5<T> where T : struct { public class N<U> where U : T {}   // CS0456 public class N2<U> where U : struct {}   // OK } }  
```