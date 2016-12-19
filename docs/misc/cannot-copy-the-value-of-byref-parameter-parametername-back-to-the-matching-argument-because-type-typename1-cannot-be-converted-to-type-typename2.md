---
title: "由于类型“&lt;typename1&gt;”不能转换为类型“&lt;typename2&gt;”，因此无法将“ByRef”形参“&lt;parametername&gt;”的值复制回匹配的实参 | Microsoft Docs"
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
  - "vbc33037"
  - "BC33037"
helpviewer_keywords: 
  - "BC33037"
ms.assetid: 3ff137e2-e062-4e54-abf5-e902e2d18968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 由于类型“&lt;typename1&gt;”不能转换为类型“&lt;typename2&gt;”，因此无法将“ByRef”形参“&lt;parametername&gt;”的值复制回匹配的实参
一个过程，声明该过程时使用的形参类型无法转换回调用实参类型。  
  
 在定义类或结构时，可以定义一个或多个转换运算符来将该类或结构类型转换为其他类型。 也可以定义反向转换运算符来将这些其他类型转换回类或结构类型。 当在过程调用中使用你的类或结构类型时，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 可以使用这些转换运算符将参数的类型转换为其对应的参数的类型。  
  
 传递参数 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md) 时，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 有时会将参数值复制到过程的局部变量中，而不是传递一个引用。 在这种情况下，当过程返回时，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 必须随后将局部变量值复制回调用代码中的参数。  
  
 如果将 `ByRef` 实参值复制到过程中，并且实参与形参为同一类型，则不必进行转换。 但是，如果类型不同，则必须对 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 进行双向转换。 如果其中一个类型是你的类或结构类型，则 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 就必须在该类型与其他类型之间进行双向转换。 这意味着你必须定义两个方向的转换运算符。  
  
 **错误 ID：**BC33037  
  
### 更正此错误  
  
-   如果可能，请使用与过程参数同类型的调用参数，这样 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 就不需要进行任何转换。  
  
-   如果需要调用实参类型与形参类型不同的过程，但不需要将值返回到调用实参中，请将形参定义为 [ByVal](../Topic/ByVal%20\(Visual%20Basic\).md) 而不是 `ByRef`。  
  
-   如果需要将值返回到调用参数中，则可定义反向转换运算符，以便 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 可以转换回调用参数类型。  
  
## 请参阅  
 [过程](../Topic/Procedures%20in%20Visual%20Basic.md)   
 [过程参数和自变量](../Topic/Procedure%20Parameters%20and%20Arguments%20\(Visual%20Basic\).md)   
 [通过值和通过引用传递参数](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [运算符过程](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator 语句](../Topic/Operator%20Statement.md)   
 [如何：定义运算符](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [如何：定义转换运算符](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)