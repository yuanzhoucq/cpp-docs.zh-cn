---
title: "编译器错误 CS1902 | Microsoft Docs"
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
  - "CS1902"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1902"
ms.assetid: 120c5978-9ebc-4ec1-bcec-f840af6fdf5d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS1902
\/debug 的选项“option”无效；必须是 full 或 pdbonly  
  
 向 [\/debug](../Topic/-debug%20\(C%23%20Compiler%20Options\).md) 编译器选项传递了无效的选项。  
  
 下面的示例生成 CS1902：  
  
```  
// CS1902.cs // compile with: /debug:x // CS1902 expected class x { public static void Main() { } }  
```