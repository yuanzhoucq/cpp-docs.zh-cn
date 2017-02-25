---
title: "CNonStatelessWorker Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CNonStatelessWorker<Worker>"
  - "ATL::CNonStatelessWorker"
  - "ATL.CNonStatelessWorker"
  - "CNonStatelessWorker"
  - "ATL::CNonStatelessWorker<Worker>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNonStatelessWorker class"
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CNonStatelessWorker Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

接收来自线程池的请求并传递到在每个请求创建和销毁的辅助对象。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class Worker  
>  
class CNonStatelessWorker  
```  
  
#### 参数  
 *辅助*  
 匹配 [辅助原型](../../atl/reference/worker-archetype.md) 的辅助线程选件类应用于处理请求。[CThreadPool](../../atl/reference/cthreadpool-class.md)排入队列。  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CNonStatelessWorker::RequestType](../Topic/CNonStatelessWorker::RequestType.md)|[WorkerArchetype::RequestType](../Topic/WorkerArchetype::RequestType.md)的实现。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CNonStatelessWorker::Execute](../Topic/CNonStatelessWorker::Execute.md)|[WorkerArchetype::Execute](../Topic/WorkerArchetype::Execute.md)的实现。|  
|[CNonStatelessWorker::Initialize](../Topic/CNonStatelessWorker::Initialize.md)|[WorkerArchetype::Initialize](../Topic/WorkerArchetype::Initialize.md)的实现。|  
|[CNonStatelessWorker::Terminate](../Topic/CNonStatelessWorker::Terminate.md)|[WorkerArchetype::Terminate](../Topic/WorkerArchetype::Terminate.md)的实现。|  
  
## 备注  
 此选件类是简单辅助线程用于 [CThreadPool](../../atl/reference/cthreadpool-class.md)的使用。  此选件类不提供自己的任何请求处理的功能。  相反，它实例化 *辅助* 一个实例每个请求并将其方法的实现对该实例。  
  
 此选件类的优点是它提供了一种简便方式更改现有的辅助线程选件类的状态模型。  `CThreadPool` 将创建线程的生存期的单个辅助进程，因此，如果辅助选件类保留状态，它会保存到跨越多个请求。  通过包装在 `CNonStatelessWorker` 模板的选件该类在将它用于 `CThreadPool`，它保留辅助进入状态的生存期限于单个请求。  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [CThreadPool Class](../../atl/reference/cthreadpool-class.md)   
 [Worker Archetype](../../atl/reference/worker-archetype.md)   
 [类](../../atl/reference/atl-classes.md)