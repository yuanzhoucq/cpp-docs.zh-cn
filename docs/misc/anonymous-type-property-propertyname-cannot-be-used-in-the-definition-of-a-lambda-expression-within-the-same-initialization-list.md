---
title: "不能在同一个初始化列表中的 lambda 表达式定义中使用匿名类型属性“&lt;propertyname&gt;”。 | Microsoft Docs"
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
  - "vbc36549"
  - "bc36549"
helpviewer_keywords: 
  - "BC36549"
ms.assetid: 6d04692a-957a-41ce-a19c-fcb06a186d1a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不能在同一个初始化列表中的 lambda 表达式定义中使用匿名类型属性“&lt;propertyname&gt;”。
匿名类型的初始化列表中定义的属性不能是相同列表中的 lambda 表达式定义的一部分。 例如，在下面的代码中，属性 `Num` 不能包含在 `LambdaFun` 的定义中。  
  
```vb#  
' Not valid.  
'Dim anon = New With {.Num = 4, .LambdaFun = Function() .Num > 0}  
```  
  
 **错误 ID：**BC36549  
  
### 更正此错误  
  
1.  考虑将匿名类型拆分为两个部分：  
  
    ```vb#  
    Dim anon1 = New With {.Num = 4}  
    Dim anon2 = New With {.LambdaFun = Function() anon1.Num > 0}  
    ' - or -  
    Dim anon3 = New With {.lambdaFun = Function(n As Integer) n > 0}  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    anon1.Num = -5  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    ```  
  
     请注意，如果将 `anon1.Num` 声明为 `Key` 属性，则无法更改其值。  
  
2.  一种替代方法是使用常规函数语句访问匿名类型属性：  
  
    ```vb#  
    Function testNum(ByVal n As Integer) As Boolean  
        Return n > 0  
    End Function  
    Console.WriteLine(testNum(anon1.Num))  
    ```  
  
3.  同样，可以使用在匿名类型外部定义的 lambda 函数：  
  
    ```vb#  
    Dim lambdaFun1 = Function() anon1.Num > 0  
    Dim lambdaFun2 = Function(n As Integer) n > 0  
    ```  
  
## 请参阅  
 [lambda 表达式](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [匿名类型](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)