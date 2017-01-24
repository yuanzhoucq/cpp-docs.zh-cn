---
title: "此转换运算符的参数类型或返回类型必须为包含类型。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33022"
  - "bc33022"
helpviewer_keywords: 
  - "BC33022"
ms.assetid: 55baff11-eb35-4c81-bc04-5006524ab450
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此转换运算符的参数类型或返回类型必须为包含类型。
转化运算符的定义使用在其中定义了此运算符的类或结构之外的类型来指定两个参数和返回类型。  
  
 在类或结构中定义转换运算符时，该运算符必须转换为\/自该类或结构的类型。  
  
 **错误 ID：**BC33022  
  
### 更正此错误  
  
-   将参数类型或返回类型更改为在其中定义了运算符的类或结构的类型。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)