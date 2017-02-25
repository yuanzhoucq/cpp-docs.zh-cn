---
title: "ISchedulerProxy 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::ISchedulerProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISchedulerProxy 结构"
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# ISchedulerProxy 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

计划程序用来与并发运行时的资源管理器进行通信以协商资源分配的接口。  
  
## 语法  
  
```  
struct ISchedulerProxy;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ISchedulerProxy::BindContext 方法](../Topic/ISchedulerProxy::BindContext%20Method.md)|如果尚未与一个线程代理相关联，则可以将执行上下文与线程代理关联。|  
|[ISchedulerProxy::CreateOversubscriber 方法](../Topic/ISchedulerProxy::CreateOversubscriber%20Method.md)|在与现有执行资源相关联的硬件线程上创建新的虚拟处理器根。|  
|[ISchedulerProxy::RequestInitialVirtualProcessors 方法](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md)|请求虚拟处理器根的初始分配。  每个虚拟处理器根表示执行一个可以执行计划程序作业的线程的能力。|  
|[ISchedulerProxy::Shutdown 方法](../Topic/ISchedulerProxy::Shutdown%20Method.md)|通知资源管理器计划程序正在关闭。  这将导致资源管理器以立即回收授予计划程序的所有资源。|  
|[ISchedulerProxy::SubscribeCurrentThread 方法](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md)|向资源管理器注册当前线程，将其与此计划程序相关联。|  
|[ISchedulerProxy::UnbindContext 方法](../Topic/ISchedulerProxy::UnbindContext%20Method.md)|将线程代理与由 `pContext` 参数指定的执行上下文取消关联，并将其返回到线程代理工厂的自由池。  该方法只能在通过 [ISchedulerProxy::BindContext](../Topic/ISchedulerProxy::BindContext%20Method.md) 方法绑定并且尚未通过以 [IThreadProxy::SwitchTo](../Topic/IThreadProxy::SwitchTo%20Method.md) 方法调用的 `pContext` 参数开始的执行上下文上调用。|  
  
## 备注  
 资源管理器使用 [IResourceManager::RegisterScheduler](../Topic/IResourceManager::RegisterScheduler%20Method.md) 方法将 `ISchedulerProxy` 接口给予用它注册的每个计划程序。  
  
## 继承层次结构  
 `ISchedulerProxy`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IScheduler 结构](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IThreadProxy 结构](../../../parallel/concrt/reference/ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 结构](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [IResourceManager 结构](../../../parallel/concrt/reference/iresourcemanager-structure.md)