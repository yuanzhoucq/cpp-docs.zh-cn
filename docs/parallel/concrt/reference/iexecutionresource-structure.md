---
title: "IExecutionResource 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IExecutionResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IExecutionResource 结构"
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# IExecutionResource 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

硬件线程的抽象。  
  
## 语法  
  
```  
struct IExecutionResource;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IExecutionResource::CurrentSubscriptionLevel 方法](../Topic/IExecutionResource::CurrentSubscriptionLevel%20Method.md)|返回激活的虚拟处理器根数以及当前与此执行资源表示的基础硬件线程关联的订阅的外部线程数。|  
|[IExecutionResource::GetExecutionResourceId 方法](../Topic/IExecutionResource::GetExecutionResourceId%20Method.md)|返回此执行资源表示的硬件线程的唯一标识符。|  
|[IExecutionResource::GetNodeId 方法](../Topic/IExecutionResource::GetNodeId%20Method.md)|返回此执行资源所属的处理器节点的唯一标识符。|  
|[IExecutionResource::Remove 方法](../Topic/IExecutionResource::Remove%20Method.md)|将此执行资源返回到资源管理器。|  
  
## 备注  
 执行资源可以是独立的，也可以与虚拟处理器根相关联。  独立执行资源在应用程序中的线程创建线程订阅时创建。  方法 [ISchedulerProxy::SubscribeThread](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md) 和 [ISchedulerProxy::RequestInitialVirtualProcessors](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md) 创建线程订阅，并返回表示订阅的 `IExecutionResource` 接口。  创建线程订阅是一种方法，用于通知资源管理器一个给定线程将参与作业排队到计划程序，同时将虚拟处理器根资源管理器分配给该计划程序。  资源管理器使用该信息以避免过度订阅硬件线程（在它可以这样的地方）。  
  
## 继承层次结构  
 `IExecutionResource`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IVirtualProcessorRoot 结构](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [ISchedulerProxy::SubscribeCurrentThread 方法](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md)   
 [ISchedulerProxy::RequestInitialVirtualProcessors 方法](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md)