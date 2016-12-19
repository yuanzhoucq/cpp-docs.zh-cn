---
title: "Scheduler 类 | Microsoft Docs"
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
  - "concrt/concurrency::Scheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Scheduler 类"
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
caps.latest.revision: 19
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Scheduler 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示并发运行时计划程序的抽象。  
  
## 语法  
  
```  
class Scheduler;  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[Scheduler::Scheduler 构造函数](../Topic/Scheduler::Scheduler%20Constructor.md)|`Scheduler` 类的对象只能使用工厂方法创建或隐式创建。|  
|[Scheduler::~Scheduler 析构函数](../Topic/Scheduler::~Scheduler%20Destructor.md)|当对 `Scheduler` 类的对象的所有外部引用不存在时，该对象会隐式销毁。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)|将计划程序附加到调用上下文中。  此方法返回后，则由计划程序管理调用上下文，并且该计划程序将成为当前计划程序。|  
|[Scheduler::Create 方法](../Topic/Scheduler::Create%20Method.md)|创建行为由 `_Policy` 参数描述的新计划程序，将初始引用放置到该计划程序并返回一个指向它的指针。|  
|[Scheduler::CreateScheduleGroup 方法](../Topic/Scheduler::CreateScheduleGroup%20Method.md)|已重载。  在计划程序内创建新的计划组。  采用参数 `_Placement` 的版本在新创建的计划组中的生成任务。偏向在该参数指定的位置执行。|  
|[Scheduler::GetNumberOfVirtualProcessors 方法](../Topic/Scheduler::GetNumberOfVirtualProcessors%20Method.md)|返回计划程序的当前虚拟处理器数。|  
|[Scheduler::GetPolicy 方法](../Topic/Scheduler::GetPolicy%20Method.md)|返回要用其创建计划程序的策略副本。|  
|[Scheduler::Id 方法](../Topic/Scheduler::Id%20Method.md)|返回计划程序的唯一标识符。|  
|[Scheduler::IsAvailableLocation 方法](../Topic/Scheduler::IsAvailableLocation%20Method.md)|确定特定位置是否可用于计划程序。|  
|[Scheduler::Reference 方法](../Topic/Scheduler::Reference%20Method.md)|递增计划的引用数。|  
|[Scheduler::RegisterShutdownEvent 方法](../Topic/Scheduler::RegisterShutdownEvent%20Method.md)|在计划程序关闭和销毁本身时使在 `_Event` 参数中传递的 Windows 事件句柄发出信号。  在发出事件信号时，所有已计划至计划程序的工作已完成。  可通过该方法注册多个关闭事件。|  
|[Scheduler::Release 方法](../Topic/Scheduler::Release%20Method.md)|递减计划的引用数。|  
|[Scheduler::ResetDefaultSchedulerPolicy 方法](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md)|将默认计划程序策略重置为运行时的默认策略。  下次在创建一个默认计划程序时，它将使用运行时的默认策略设置。|  
|[Scheduler::ScheduleTask 方法](../Topic/Scheduler::ScheduleTask%20Method.md)|已重载。  在计划程序内安排轻量任务。  轻量任务将放置在运行时决定的计划组中。  带 `_Placement` 参数的版本导致任务偏向执行指定的位置。|  
|[Scheduler::SetDefaultSchedulerPolicy 方法](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)|允许使用户定义的策略来创建默认计划程序。  在进程中存在一个默认计划程序时，才可调用此方法。  在设置了默认策略后，在对 `SetDefaultSchedulerPolicy` 或 [ResetDefaultSchedulerPolicy](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md) 方法进行下一个有效的调用之前它将一直有效。|  
  
## 备注  
 并发运行时计划程序使用映射到操作系统执行上下文的执行上下文（如线程）来执行由您的应用程序对其进行排队的工作。  在任何时候，计划程序的并发级别等于通过资源管理器向它授予的虚拟处理器数。  虚拟处理器是处理资源的抽象，可映射到基础系统中的硬件线程。  在指定时间只有一个计划程序上下文可能会在虚拟处理器上执行。  
  
 并发运行时将为每个进程创建默认计划程序来执行并行工作。  此外，您可以使用此类创建您自己的计划程序实例和对它进行操作。  
  
## 继承层次结构  
 `Scheduler`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler Class](../../../parallel/concrt/reference/scheduler-class.md)   
 [PolicyElementKey 枚举](../Topic/PolicyElementKey%20Enumeration.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)