---
title: "编译器错误 CS0761 | Microsoft Docs"
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
  - "CS0761"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0761"
ms.assetid: b16ac1df-0ddc-44d2-89f1-8d9c32af87ad
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0761
“method\<T\>”的分部方法声明具有不一致的类型参数约束。  
  
 如果分部方法具有实现，则泛型类型约束必须与方法签名上定义的约束相同。  
  
### 更正此错误  
  
1.  确保分部方法各部分上的泛型类型约束保持一致。  
  
## 示例  
 以下代码生成 CS0761：  
  
```  
// cs0761.cs using System; public partial class C { partial void Part<T>() where T : class; partial void Part<T>() where T : struct // CS0761 { } public static int Main() { return 1; } }  
  
```  
  
## 请参阅  
 [分部类和方法](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [类型参数的约束](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)