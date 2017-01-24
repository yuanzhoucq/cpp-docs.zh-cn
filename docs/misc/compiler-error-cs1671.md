---
title: "编译器错误 CS1671 | Microsoft Docs"
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
  - "CS1671"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1671"
ms.assetid: 34255d2b-6ff6-4ac1-b617-3199e16726cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1671
命名空间声明不能有修饰符或特性  
  
 修饰符在应用于命名空间时没有意义，因此不允许使用修饰符。  
  
 下面的示例生成 CS1671：  
  
```  
// CS1671.cs public namespace NS // CS1671 { }  
```