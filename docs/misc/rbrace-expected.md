---
title: "应有“}” | Microsoft Docs"
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
  - "vbc30370"
  - "bc30370"
helpviewer_keywords: 
  - "BC30370"
ms.assetid: a4ce9be9-fc5d-46ec-a217-c3428bd0b97e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 应有“}”
数组初始值设定项或约束列表不以有效形式结束。  
  
 用来初始化数组的元素值必须括在大括号 \(`{}`\) 中。  
  
```  
Dim demoArray() As Integer = New Integer() {1, 2, 3}   
```  
  
 同样，泛型类型形参约束列表中的约束也必须括在大括号中。  
  
```  
Public Class dictionaryMaker(Of t As {IComparable, IDisposable, New})   
```  
  
 **错误 ID：**BC30370  
  
### 更正此错误  
  
-   使用“}”结束数组初始值设定项和约束列表。  
  
## 请参阅  
 [数组](../Topic/Arrays%20in%20Visual%20Basic.md)   
 [如何：在 Visual Basic 中初始化数组变量](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [类型列表](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型类型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)