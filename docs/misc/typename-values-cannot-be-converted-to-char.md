---
title: "“&lt;类型名称&gt;”值无法转换为“Char” | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32007"
  - "vbc32007"
helpviewer_keywords: 
  - "BC32007"
ms.assetid: b04212da-57ac-4493-9480-04c12b50f875
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;类型名称&gt;”值无法转换为“Char”
“\<类型名称\>”值无法转换为“Char”。 使用 Microsoft.VisualBasic.ChrW 将数值解释为 Unicode 字符，或者先将其转换为“String”以产生数字。  
  
 一个表达式尝试将 `String` 或 `Object` 之外的数据类型转换为 `Char`。  
  
 **错误 ID：**BC32007  
  
### 更正此错误  
  
-   使用 `ChrW` 函数将数值转换为 Unicode 字符，或将该值首先转换为 `String`，然后转换为 `Char`。  
  
## 请参阅  
 [不在生成中：Chr, ChrW 函数](http://msdn.microsoft.com/zh-cn/37f3c707-8a6f-4c51-9b02-9e634c4299ab)   
 [隐式转换和显式转换](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Char 数据类型](../Topic/Char%20Data%20Type%20\(Visual%20Basic\).md)