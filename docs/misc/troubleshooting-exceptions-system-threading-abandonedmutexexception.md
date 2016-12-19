---
title: "关于异常的疑难解答：System.Threading.AbandonedMutexException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Threading.AbandonedMutexException 异常"
  - "AbandonedMutexException 异常"
ms.assetid: 11157066-32ed-492c-83af-29983f915eec
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Threading.AbandonedMutexException
当一个线程在等待 Mutex 对象，而另一个线程通过退出（而不释放）Mutex 来放弃它时，引发的异常。  
  
## 备注  
 放弃的 Mutex 通常表明代码中存在严重错误。 当线程在不释放 Mutex 退出时，由 Mutex 保护的数据结构可能不再处于一致的状态。 如果可以验证这些数据结构的完整性，那么下一个请求 Mutex 所有权的线程就可以处理此异常并继续运行。  
  
## 请参阅  
 <xref:System.Threading.AbandonedMutexException>   
 <xref:System.Threading.Mutex>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [线程](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)