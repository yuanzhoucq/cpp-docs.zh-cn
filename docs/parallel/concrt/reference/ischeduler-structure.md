---
title: "IScheduler 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IScheduler 结构"
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# IScheduler 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

工作计划程序抽象的接口。  并发运行时的资源管理器使用该接口与工作计划程序进行通信。  
  
## 语法  
  
```  
struct IScheduler;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IScheduler::AddVirtualProcessors 方法](../Topic/IScheduler::AddVirtualProcessors%20Method.md)|为计划程序提供一组虚拟处理器根供其使用。  每个 `IVirtualProcessorRoot` 接口表示执行可以代表计划程序执行作业的单个线程的权限。|  
|[IScheduler::GetId 方法](../Topic/IScheduler::GetId%20Method.md)|返回计划程序的唯一标识符。|  
|[IScheduler::GetPolicy 方法](../Topic/IScheduler::GetPolicy%20Method.md)|返回计划程序的策略副本。  有关计划程序策略的更多信息，请参见 [SchedulerPolicy](../../../parallel/concrt/reference/schedulerpolicy-class.md)。|  
|[IScheduler::NotifyResourcesExternallyBusy 方法](../Topic/IScheduler::NotifyResourcesExternallyBusy%20Method.md)|通知此计划程序由数组 `ppVirtualProcessorRoots` 中的虚拟处理器根的集合表示的硬件线程正被其他计划程序使用。|  
|[IScheduler::NotifyResourcesExternallyIdle 方法](../Topic/IScheduler::NotifyResourcesExternallyIdle%20Method.md)|通知此计划程序由数组 `ppVirtualProcessorRoots` 中的虚拟处理器根的集合表示的硬件线程未被其他计划程序使用。|  
|[IScheduler::RemoveVirtualProcessors 方法](../Topic/IScheduler::RemoveVirtualProcessors%20Method.md)|启动移除之前分配给此计划程序的虚拟处理器根。|  
|[IScheduler::Statistics 方法](../Topic/IScheduler::Statistics%20Method.md)|提供有关任务到达和完成率以及计划程序的队列长度更改的信息。|  
  
## 备注  
 如果要实现与资源管理器进行通信的自定义计划程序，您应提供 `IScheduler` 接口的实现。  该接口是计划程序和资源管理器之间的通信的双向通道的一端。  `IResourceManager` 和 `ISchedulerProxy` 接口表示的另一端，由资源管理器实施。  
  
## 继承层次结构  
 `IScheduler`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy 类](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [IExecutionContext 结构](../../../parallel/concrt/reference/iexecutioncontext-structure.md)   
 [IThreadProxy 结构](../../../parallel/concrt/reference/ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 结构](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [IResourceManager 结构](../../../parallel/concrt/reference/iresourcemanager-structure.md)