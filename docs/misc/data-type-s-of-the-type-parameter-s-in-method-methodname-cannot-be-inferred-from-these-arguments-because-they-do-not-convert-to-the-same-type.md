---
title: "无法根据这些参数推断出方法“&lt;methodname&gt;”中类型形参的数据类型，因为它们没有转换为同一类型 | Microsoft Docs"
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
  - "vbc36660"
  - "bc36660"
  - "vbc36657"
  - "bc36657"
helpviewer_keywords: 
  - "BC36660"
  - "BC36657"
ms.assetid: e80c5afd-e16d-4f03-bdf1-c79c4286114b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 无法根据这些参数推断出方法“&lt;methodname&gt;”中类型形参的数据类型，因为它们没有转换为同一类型
无法根据这些参数推断出方法“\<methodname\>”中类型形参的数据类型，因为它们没有转换为同一类型。 显式指定数据类型可更正此错误。  
  
 在计算对泛型过程的调用时，试图使用类型推断功能来确定类型形参的数据类型。 编译器找不到符合所有实参约束的数据类型。 因此，编译器报告此错误。  
  
> [!NOTE]
>  当无法指定实参时（例如，对于查询表达式中的查询运算符），显示的错误消息不包括第二个句子。  
  
 下面的代码演示了此错误。  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. Integer and Date do not convert to the same type. 'targetMethod(19, #3/4/2007#) End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **错误 ID：**BC36660 和 BC36657  
  
### 更正此错误  
  
-   你或许能够将一个或多个实参显式转换为某个兼容类型，如以下代码所示：  
  
    ```  
    targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   你或许能够为实参转换到的类型形参指定数据类型，如以下代码所示：  
  
    ```  
    targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## 请参阅  
 [Visual Basic 中的泛型过程](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [类型转换函数](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)   
 [隐式转换和显式转换](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Visual Basic 中的类型转换](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)