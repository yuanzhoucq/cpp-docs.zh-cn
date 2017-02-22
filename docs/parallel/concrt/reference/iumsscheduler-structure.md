---
title: "IUMSScheduler 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IUMSScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSScheduler 结构"
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# IUMSScheduler 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

希望并发运行时资源管理器向其传递用户模式计划 \(UMS\) 线程的工作计划程序抽象的接口。  资源管理器使用该接口与 UMS 线程计划程序通信。  `IUMSScheduler` 接口从 `IScheduler` 接口继承。  
  
## 语法  
  
```  
struct IUMSScheduler : public IScheduler;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IUMSScheduler::SetCompletionList 方法](../Topic/IUMSScheduler::SetCompletionList%20Method.md)|将 `IUMSCompletionList` 接口分配给 UMS 线程计划程序。|  
  
## 备注  
 如果要实现与资源管理器进行通信的自定义计划程序，并希望将 UMS 线程而不是普通的 Win32 线程传递给您的计划程序，则应提供 `IUMSScheduler` 接口的实现。  此外，您应将计划程序策略键 `SchedulerKind` 的策略值设置为 `UmsThreadDefault`。  如果策略指定 UMS 线程，作为参数传递给 [IResourceManager::RegisterScheduler](../Topic/IResourceManager::RegisterScheduler%20Method.md) 方法的 `IScheduler` 接口必须为 `IUMSScheduler` 接口。  
  
 资源管理器只能够在具有 UMS 功能的操作系统上处理 UMS 线程。具有 Windows 7 和更高版本的 64 位操作系统支持 UMS 线程。  如果您创建一个 `SchedulerKind` 键设置为值 `UmsThreadDefault` 的计划程序策略，且基础平台不支持 UMS，该策略上的 `SchedulerKind` 键的值将被更改为值 `ThreadScheduler`。  在希望接收 UMS 线程之前，应该始终读回该策略值。  
  
 `IUMSScheduler` 接口是计划程序和资源管理器之间的通信的双向通道的一端。  `IResourceManager` 和 `ISchedulerProxy` 接口表示的另一端，由资源管理器实施。  
  
## 继承层次结构  
 [IScheduler](../../../parallel/concrt/reference/ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [IScheduler 结构](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IUMSCompletionList 结构](../../../parallel/concrt/reference/iumscompletionlist-structure.md)   
 [IResourceManager 结构](../../../parallel/concrt/reference/iresourcemanager-structure.md)