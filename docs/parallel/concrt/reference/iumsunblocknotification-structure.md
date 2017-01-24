---
title: "IUMSUnblockNotification 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IUMSUnblockNotification"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSUnblockNotification 结构"
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUMSUnblockNotification 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示来自资源管理器的通知，说明阻塞并触发返回到计划程序的指定计划上下文的线程代理已解除阻塞，并已准备好进行计划。  一旦返回自 `GetContext` 方法的线程代理相关的执行上下文被重新计划，则该接口无效。  
  
## 语法  
  
```  
struct IUMSUnblockNotification;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IUMSUnblockNotification::GetContext 方法](../Topic/IUMSUnblockNotification::GetContext%20Method.md)|返回与已解除阻塞的线程代理关联的执行上下文的 `IExecutionContext` 接口。  此方法返回并通过调用 `IThreadProxy::SwitchTo` 方法重新计划基础执行上下文后，此接口不再有效。|  
|[IUMSUnblockNotification::GetNextUnblockNotification 方法](../Topic/IUMSUnblockNotification::GetNextUnblockNotification%20Method.md)|返回链中从 `IUMSCompletionList::GetUnblockNotifications` 方法返回的下个 `IUMSUnblockNotification` 接口。|  
  
## 继承层次结构  
 `IUMSUnblockNotification`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler 结构](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [IUMSCompletionList 结构](../../../parallel/concrt/reference/iumscompletionlist-structure.md)