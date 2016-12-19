---
title: "编译器错误 CS0226 | Microsoft Docs"
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
  - "CS0226"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0226"
ms.assetid: 9f8c74c4-de21-41fb-84e1-ef32a4b23ced
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0226
\_\_arglist 表达式只能出现在调用或新的表达式内部。  
  
 不支持的关键字 `__arglist` 只能出现在方法调用或新的表达式中。  
  
## 示例  
 以下代码生成 CS0226：  
  
```  
// cs0226.cs using System; public class C { public static int Main () { __arglist(1,"This is a string"); // CS0226 return 0; } }  
```