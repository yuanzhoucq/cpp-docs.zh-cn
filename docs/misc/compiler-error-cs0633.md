---
title: "编译器错误 CS0633 | Microsoft Docs"
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
  - "CS0633"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0633"
ms.assetid: a24d310b-151a-45eb-b150-3407940ec24c
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0633
“attribute”特性的参数必须是有效的标识符  
  
 传递到 <xref:System.Diagnostics.ConditionalAttribute> 或 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 特性的参数必须是有效的标识符。 这意味着它不能包含“\+”这样的字符，它们出现在标识符中则为非法。  
  
## 示例  
 此示例使用 <xref:System.Diagnostics.ConditionalAttribute> 演示 CS0633。 以下示例生成 CS0633。  
  
```  
// CS0633a.cs #define DEBUG using System.Diagnostics; public class Test { [Conditional("DEB+UG")]   // CS0633 // try the following line instead // [Conditional("DEBUG")] public static void Main() { } }  
```  
  
## 示例  
 此示例使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 演示 CS0633。  
  
```  
// CS0633b.cs // compile with: /target:module #define DEBUG using System.Runtime.CompilerServices; public class Test { [IndexerName("Invalid+Identifier")]   // CS0633 // try the following line instead // [IndexerName("DEBUG")] public int this[int i] { get { return i; } } }  
  
```