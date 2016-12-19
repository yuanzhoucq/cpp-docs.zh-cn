---
title: "关于异常的疑难解答：System.Reflection.AmbiguousMatchException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Reflection.AmbiguousMatchException 异常"
  - "AmbiguousMatchException 异常"
ms.assetid: f92b5c51-42b6-4c2e-83df-0d598b3b41c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Reflection.AmbiguousMatchException
当绑定到方法导致多个方法匹配绑定条件时引发的异常。  
  
## 备注  
 如果应用程序调用类，但是无法确定要使用哪个类或重载类时，将引发 <xref:System.Reflection.AmbiguousMatchException>。 绑定尝试定位要使用的适当的类，这是由参数的数目和参数的类型决定的。 如果找到了多个可接受的类，将引发此异常。  
  
## 请参阅  
 <xref:System.Reflection.AmbiguousMatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)