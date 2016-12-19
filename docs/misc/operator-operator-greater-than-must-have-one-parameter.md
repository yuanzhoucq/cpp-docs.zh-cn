---
title: "运算符“&lt;operator&gt;”必须有一个参数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33014"
  - "vbc33014"
helpviewer_keywords: 
  - "BC33014"
ms.assetid: 512a5724-a6c5-4437-a608-7d6b10e68d49
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 运算符“&lt;operator&gt;”必须有一个参数
使用无参数或多个参数定义的一元运算符。  
  
 一元运算符必须只具有一个参数。  
  
 **错误 ID：**BC33014  
  
### 更正此错误  
  
-   调整定义以只指定一个参数。  
  
-   如果需要两个参数，则必须定义一个二元运算符。  
  
-   如果不需要参数或需要两个以上的参数，则必须使用 [Function 语句](../Topic/Function%20Statement%20\(Visual%20Basic\).md) 来定义 `Function` 过程（而不是运算符）。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)