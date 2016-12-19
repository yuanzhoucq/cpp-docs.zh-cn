---
title: "关于异常的疑难解答：System.TypeInitializationException | Microsoft Docs"
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
  - "TypeInitializationException 异常"
  - "System.TypeInitializationException 异常"
ms.assetid: c77e81fd-1518-49a1-8213-3f169658f5f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.TypeInitializationException
作为类初始值设定项引发的异常的包装器而引发的异常。  
  
## 备注  
 当类初始值设定项初始化类型失败时，将创建一个 <xref:System.TypeInitializationException>，并向其传递对由该类型的类初始值设定项引发的异常的引用。<xref:System.Exception.InnerException%2A> 的 <xref:System.TypeInitializationException> 属性保存着基础异常。  
  
## 请参阅  
 <xref:System.TypeInitializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)