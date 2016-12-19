---
title: "编译器错误 CS0706 | Microsoft Docs"
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
  - "CS0706"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0706"
ms.assetid: bc3ac5c0-8c96-43c8-b10a-69bd31b38e4a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0706
约束类型无效。 作为约束使用的类型必须是接口、非密封类或类型形参。  
  
 当在约束子句中使用无效的构造时，将出现此错误。 若要避免此错误，请使用接口或非密封类取代导致此错误的构造。  
  
## 示例  
 下面的示例生成 CS0706。  
  
```  
// CS0706.cs // compile with: /target:library class A {} class C<T> where T : int[] {}  // CS0706 class D<T> where T : A {}  // OK  
```