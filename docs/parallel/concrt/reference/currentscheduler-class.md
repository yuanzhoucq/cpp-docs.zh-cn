---
title: "CurrentScheduler 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::CurrentScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CurrentScheduler 类"
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CurrentScheduler 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示与调用上下文相关联的当前计划程序的抽象。  
  
## 语法  
  
```  
class CurrentScheduler;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CurrentScheduler::Create 方法](../Topic/CurrentScheduler::Create%20Method.md)|创建行为由 `_Policy` 参数描述的新计划程序，并将其附加到调用上下文。  新创建的计划程序将成为调用上下文的当前计划程序。|  
|[CurrentScheduler::CreateScheduleGroup 方法](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md)|已重载。  在与调用上下文相关联的计划程序内创建新的计划组。  采用参数 `_Placement` 的版本在新创建的计划组中的生成任务。偏向在该参数指定的位置执行。|  
|[CurrentScheduler::Detach 方法](../Topic/CurrentScheduler::Detach%20Method.md)|将当前计划程序从调用上下文中分离并将先前附加的计划程序作为当前计划程序还原（如果有）。  此方法返回后，则由先前通过 `CurrentScheduler::Create` 或 `Scheduler::Attach` 方法附加到上下文的计划程序管理调用上下文。|  
|[CurrentScheduler::Get 方法](../Topic/CurrentScheduler::Get%20Method.md)|返回指向与调用上下文关联的计划程序（也称为当前计划程序）的指针。|  
|[CurrentScheduler::GetNumberOfVirtualProcessors 方法](../Topic/CurrentScheduler::GetNumberOfVirtualProcessors%20Method.md)|返回与调用上下文关联的计划程序的当前虚拟处理器数。|  
|[CurrentScheduler::GetPolicy 方法](../Topic/CurrentScheduler::GetPolicy%20Method.md)|返回要用其创建当前计划程序的策略副本。|  
|[CurrentScheduler::Id 方法](../Topic/CurrentScheduler::Id%20Method.md)|返回当前计划程序的唯一标识符。|  
|[CurrentScheduler::IsAvailableLocation 方法](../Topic/CurrentScheduler::IsAvailableLocation%20Method.md)|确定特定位置是否可用于当前计划程序。|  
|[CurrentScheduler::RegisterShutdownEvent 方法](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md)|在当前上下文的关联计划程序关闭和销毁本身时使在 `_ShutdownEvent` 参数中传递的 Windows 事件句柄发出信号。  在发出事件信号时，所有已计划至计划程序的工作已完成。  可通过该方法注册多个关闭事件。|  
|[CurrentScheduler::ScheduleTask 方法](../Topic/CurrentScheduler::ScheduleTask%20Method.md)|已重载。  在与调用上下文相关联的计划程序内安排轻量任务。  轻量任务将放置在运行时决定的计划组中。  带 `_Placement` 参数的版本导致任务偏向执行指定的位置。|  
  
## 备注  
 如果没有计划程序（请参见[计划程序](../../../parallel/concrt/reference/scheduler-class.md)）与调用上下文相关联，`CurrentScheduler` 类中的许多方法将导致附加进程的默认计划程序。  这也暗示在此调用的过程中创建了进程的默认计划程序。  
  
## 继承层次结构  
 `CurrentScheduler`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)