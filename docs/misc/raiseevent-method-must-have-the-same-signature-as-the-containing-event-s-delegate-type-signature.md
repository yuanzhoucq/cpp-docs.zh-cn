---
title: "“RaiseEvent”方法和包含事件的委托类型“&lt;signature&gt;”必须有相同的签名 | Microsoft Docs"
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
  - "bc31137"
  - "vbc31137"
helpviewer_keywords: 
  - "BC31137"
ms.assetid: 9db77546-9205-4fd2-baf6-6eb1b46b1f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “RaiseEvent”方法和包含事件的委托类型“&lt;signature&gt;”必须有相同的签名
`Custom Event` 声明必须具有 `RaiseEvent` 声明，此声明具有和自定义事件的 `As` 子句指定的委托类型相同的签名。  
  
 对于要匹配的签名，`RaiseEvent` 声明和委托必须具有参数数量，并且参数类型必须匹配。  
  
 **错误 ID：**BC31137  
  
### 更正此错误  
  
-   更改 `RaiseEvent` 声明的参数以匹配委托类型的参数。  
  
## 示例  
 此示例演示具有 `RaiseEvent` 声明的正确参数类型的自定义事件。  
  
 [!code-vb[VbVbalrEventError#2](../misc/codesnippet/VisualBasic/raiseevent-method-must-have-the-same-signature-as-the-containing-event-s-delegate-type-signature_1.vb)]  
  
## 请参阅  
 [Event 语句](../Topic/Event%20Statement.md)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/zh-cn/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Delegate 语句](../Topic/Delegate%20Statement.md)   
 [事件](../Topic/Events%20\(Visual%20Basic\).md)