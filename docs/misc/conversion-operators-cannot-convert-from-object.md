---
title: "转换运算符不能从 Object 转换 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33032"
  - "vbc33032"
helpviewer_keywords: 
  - "BC33032"
ms.assetid: 877f626f-7aa1-41d8-b7ca-eb4337d012d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 转换运算符不能从 Object 转换
转换运算符是使用 [Object 数据类型](../Topic/Object%20Data%20Type.md) 的参数声明的。  
  
 编译时，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 会认为在其继承层次结构中存在从任何引用类型到任何类型的预定义转换，即，派生该类型的任何类型或该类型所派生的任何类型。`Object` 是 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 中的通用数据类型，因此每个类型均从 `Object` 派生而来。  
  
 由于编译器认为已定义此转换，因此它不允许你对其重新定义。  
  
 **错误 ID：**BC33032  
  
### 更正此错误  
  
-   完全删除此运算符定义。 已对其进行预定义。  
  
## 请参阅  
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [作为通用数据类型的对象 \(Visual Basic\)](http://msdn.microsoft.com/zh-cn/5315bf21-2b22-45ab-98cd-5631dffbcb2f)