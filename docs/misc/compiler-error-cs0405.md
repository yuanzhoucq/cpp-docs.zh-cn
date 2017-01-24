---
title: "编译器错误 CS0405 | Microsoft Docs"
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
  - "CS0405"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0405"
ms.assetid: 0bf51e24-dc6c-438f-a928-b5bfbf35f81a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0405
类型参数“type parameter”的重复约束“constraint”  
  
 泛型声明的两个约束完全相同。 若要消除此错误，请删除重复的约束。  
  
 下面的示例生成 CS0405：  
  
```  
// CS0405.cs interface I { } class C<T> where T : I, I  // CS0405.cs { }  
```