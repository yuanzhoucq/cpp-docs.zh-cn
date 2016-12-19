---
title: "编译器错误 CS1021 | Microsoft Docs"
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
  - "CS1021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1021"
ms.assetid: 0346ba58-d7cd-40bd-bcad-b90117fdc9b5
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1021
整数常量太大  
  
 分配为[整型](../Topic/Integral%20Types%20Table%20\(C%23%20Reference\).md)的值超出了可能的最大无符号整数值。  
  
 下面的示例生成 CS1021:  
  
```  
// CS1021.cs enum F : int { a=(int)2590000000000000000000   // CS1021 } public class clx { public static void Main() { } }  
```