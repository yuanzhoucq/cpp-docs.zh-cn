---
title: "计划程序策略 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计划程序策略"
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
caps.latest.revision: 12
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 计划程序策略
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍并发运行时中计划程序策略的角色。  *计划程序策略*控制计划程序在管理任务时使用的策略。  例如，考虑需要执行某些任务。`THREAD_PRIORITY_NORMAL` 和执行其他任务。`THREAD_PRIORITY_HIGHEST`的应用程序。您可以创建两个计划程序实例：指定 `ContextPriority` 策略为 `THREAD_PRIORITY_NORMAL` 指定同一策略是 `THREAD_PRIORITY_HIGHEST`另一个。  
  
 计划程序策略允许您划分可用处理资源，以及将一组固定的资源分配给每个计划程序。  例如，请考虑一个作用范围不超过四个处理器的并行算法。  您可以创建一个计划程序策略，该策略将其任务限制为同时使用最多四个处理器。  
  
> [!TIP]
>  并发运行时提供了默认计划程序。  因此，不必创建该应用程序。  由于任务计划程序可帮助您优化应用程序的性能，因此，如果您初次接触并发运行时，则建议您先使用 [并行模式库 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
 当您使用 [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md)、[concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) 或 [concurrency::Scheduler::SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md) 方法创建计划程序实例时，请提供包含指定计划程序行为的键值对集合的 [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) 对象。  `SchedulerPolicy` 构造函数采用数量不定的参数。  第一个参数是您要指定的策略元素数。  其余参数是每个策略元素的键值对。  下面的示例创建一个 `SchedulerPolicy` 对象，该对象指定三个策略元素。  运行时对未指定的策略键使用默认值。  
  
 [!CODE [concrt-scheduler-policy#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-scheduler-policy#2)]  
  
 [concurrency::PolicyElementKey](../Topic/PolicyElementKey%20Enumeration.md) 枚举定义了与任务计划程序关联的策略键。  下表描述策略键以及运行时对每个策略键使用的默认值。  
  
|策略键|说明|默认值|  
|---------|--------|---------|  
|`SchedulerKind`|[concurrency::SchedulerType](../Topic/SchedulerType%20Enumeration.md) 值，该值指定特定线程类型来计划任务。|`ThreadScheduler`（使用普通线程）。  这是此键的唯一有效值。|  
|`MaxConcurrency`|`unsigned int` 值，该值指定计划程序使用的并发资源的最大数量。|[concurrency::MaxExecutionResources](../Topic/MaxExecutionResources%20Constant.md)|  
|`MinConcurrency`|`unsigned int` 值，该值指定计划程序使用的并发资源的最小数量。|`1`|  
|`TargetOversubscriptionFactor`|`unsigned int` 值，该值指定为每个处理资源分配了多少线程。|`1`|  
|`LocalContextCacheSize`|`unsigned int` 值，该值指定可在每个虚拟处理器的本地队列中缓存的上下文的最大数目。|`8`|  
|`ContextStackSize`|`unsigned int` 值，该值指定为每个上下文保留的堆栈的大小（以千字节为单位）。|`0`（使用默认堆栈大小）|  
|`ContextPriority`|`int` 值，该值指定每个上下文的线程优先级别。  它可以是可传递给 [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) 或 `INHERIT_THREAD_PRIORITY` 的任何值。|`THREAD_PRIORITY_NORMAL`|  
|`SchedulingProtocol`|[concurrency::SchedulingProtocolType](../Topic/SchedulingProtocolType%20Enumeration.md) 值，该值指定要使用的计划算法。|`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`|[concurrency::DynamicProgressFeedbackType](../Topic/DynamicProgressFeedbackType%20Enumeration.md) 值，该值指定是否根据基于统计信息的进度信息来重新平衡资源。<br /><br /> **附注** 不要将此策略设置 `ProgressFeedbackDisabled` 因为它保留给运行时使用。|`ProgressFeedbackEnabled`|  
  
 每个计划程序在计划任务时使用其自己的策略。  与一个计划程序关联的策略不影响任何其他计划程序的行为。  另外，创建 `Scheduler` 对象后，则不能更改计划程序策略。  
  
> [!IMPORTANT]
>  仅使用计划程序策略控制运行时创建的线程的特性。  不要更改线程关联或运行时创建的线程的优先级因为会产生未定义的行为。  
  
 如果您未显式创建计划程序，则运行时会为您创建一个默认计划程序。  如果您想要在应用程序中使用默认计划程序，但要为该计划程序指定要使用的策略，请在计划并行工作之前调用 [concurrency::Scheduler::SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md) 方法。  如果您不调用 `Scheduler::SetDefaultSchedulerPolicy` 方法，则运行时将使用表中的默认策略值。  
  
 使用 [concurrency::CurrentScheduler::GetPolicy](../Topic/CurrentScheduler::GetPolicy%20Method.md) 和 [concurrency::Scheduler::GetPolicy](../Topic/Scheduler::GetPolicy%20Method.md) 方法可检索计划程序策略的副本。  从这些方法接收的策略值可能不同于您在创建计划程序时指定的策略值。  
  
## 示例  
 为了实验有关使用特定计划程序策略控制计划程序行为的示例，请参见[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)和[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。  
  
## 请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)