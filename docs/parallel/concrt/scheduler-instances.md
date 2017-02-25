---
title: "计划程序实例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "计划程序实例"
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 计划程序实例
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍并发运行时中计划程序实例的作用，以及如何使用 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 和 [Concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) 类创建和管理计划程序实例。  当您想要将显式计划策略与特定类型的工作负载关联时，计划程序实例非常有用。  例如，您可以创建一个计划程序实例以提升的线程优先级运行部分任务，并使用默认计划程序以普通的线程优先级运行其他任务。  
  
> [!TIP]
>  并发运行时提供默认的计划程序，因此您不需要在应用程序中再创建一个计划程序。  由于任务计划程序可帮助您优化应用程序的性能，因此，如果您初次接触并发运行时，则建议您先使用 [并行模式库 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
##  <a name="top"></a> 各节内容  
  
-   [Scheduler 和 CurrentScheduler 类](#classes)  
  
-   [创建计划程序实例](#creating)  
  
-   [管理计划程序实例的生存期](#managing)  
  
-   [方法和功能](#features)  
  
-   [示例](#example)  
  
##  <a name="classes"></a> Scheduler 和 CurrentScheduler 类  
 任务计划程序使应用程序能够使用一个或多个计划程序实例来计划工作。  [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 类代表计划程序实例，并封装与计划任务相关的功能。  
  
 附加到计划程序的线程称为“执行上下文”或简称为“上下文”。  在任意时间，当前上下文中只能有一个计划程序处于活动状态。  活动的计划程序也称为“当前计划程序”。  并发运行时使用 [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) 类提供对当前计划程序的访问。  一个上下文的当前计划程序可以不同于另一个上下文的当前计划程序。  运行时不提供当前计划程序的进程级别表示形式。  
  
 通常，`CurrentScheduler` 类用于访问当前计划程序。  当您需要管理非当前的计划程序时，`Scheduler` 类很有用。  
  
 以下各节描述如何创建和管理计划程序实例。  有关演示这些任务的完整示例，请参见[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="creating"></a> 创建计划程序实例  
 可以使用下列三种方法创建 `Scheduler` 对象：  
  
-   如果不存在计划程序，在您使用运行时功能（如并行算法）执行工作时，运行时将为您创建默认计划程序。  默认计划程序将成为启动并行工作的上下文的当前计划程序。  
  
-   [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md) 方法可创建一个使用特定策略的 `Scheduler` 对象，并将该计划程序与当前上下文相关联。  
  
-   [concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) 方法可创建一个使用特定策略的 `Scheduler` 对象，但不将其与当前上下文相关联。  
  
 通过允许运行时创建默认计划程序，所有并发任务可以共享相同的计划程序。  通常，[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\) 或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)提供的功能用于执行并行工作。  因此，您不必直接使用计划程序来控制其策略或生存期。  当您使用 PPL 或代理库时，运行时将创建默认计划程序（如果它不存在），并使其成为每个上下文的当前计划程序。  如果您创建一个计划程序并将其设置为当前计划程序，则运行时使用该计划程序安排任务。  仅当需要特定的计划策略时，才创建额外的计划程序实例。  有关与计划程序关联的策略的更多信息，请参见[计划程序策略](../../parallel/concrt/scheduler-policies.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="managing"></a> 管理计划程序实例的生存期  
 运行时使用引用计数机制来控制 `Scheduler` 对象的生存期。  
  
 当您使用 `CurrentScheduler::Create` 方法或 `Scheduler::Create` 方法创建 `Scheduler` 对象时，运行时将该计划程序的初始引用计数设置为一。  当您调用 [concurrency::Scheduler::Attach](../Topic/Scheduler::Attach%20Method.md) 方法时，运行时会递增引用计数。  `Scheduler::Attach` 方法可将 `Scheduler` 对象与当前上下文相关联。  这使它成为当前计划程序。  当您调用 `CurrentScheduler::Create` 方法时，运行时创建 `Scheduler` 对象并将其附加到当前上下文（且将引用计数设置为一）。  您还可以使用 [concurrency::Scheduler::Reference](../Topic/Scheduler::Reference%20Method.md) 方法递增 `Scheduler` 对象的引用计数。  
  
 当您调用 [concurrency::CurrentScheduler::Detach](../Topic/CurrentScheduler::Detach%20Method.md) 方法以分离当前计划程序或调用 [Concurrency::Scheduler::Release](../Topic/Scheduler::Release%20Method.md) 方法时，运行时会递减引用计数。  当引用计数达到零时，运行时将在所有计划任务完成后销毁 `Scheduler` 对象。  允许正在运行的任务递增当前计划程序的引用计数。  因此，如果引用计数达到零而任务递增引用计数，在引用计数再次达到零和所有任务完成之前，运行时不会销毁 `Scheduler` 对象。  
  
 运行时为每个上下文维护一个内部 `Scheduler` 对象堆栈。  当您调用 `Scheduler::Attach` 或 `CurrentScheduler::Create` 方法时，运行时将该 `Scheduler` 对象推送到当前上下文的堆栈上。  这使它成为当前计划程序。  当您调用 `CurrentScheduler::Detach` 时，运行时从当前上下文的堆栈弹出当前计划程序，并将上一个计划程序设置为当前计划程序。  
  
 运行时提供了几种方法来管理计划程序实例的生存期。  下表针对在当前上下文中创建或附加计划程序的每个方法，显示了从当前上下文释放或分离计划程序的相应方法。  
  
|创建或附加方法|释放或分离方法|  
|-------------|-------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 调用不适当的释放或分离方法会在运行时产生未指定的行为。  
  
 当使用导致运行时为您创建默认计划程序的功能（如 PPL）时，不要释放或分离此计划程序。  运行时管理它创建的任何计划程序的生存期。  
  
 因为在所有任务完成之前运行时不会销毁 `Scheduler` 对象，所以您可以使用 [concurrency::Scheduler::RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md) 方法或 [concurrency::CurrentScheduler::RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md) 方法在 `Scheduler` 对象被销毁时接收通知。  当您必须等待 `Scheduler` 对象所计划的每个任务完成时，这非常有用。  
  
 \[[Top](#top)\]  
  
##  <a name="features"></a> 方法和功能  
 本节概述了 `CurrentScheduler` 和 `Scheduler` 类的重要方法。  
  
 将 `CurrentScheduler` 类视为一个帮助器，该帮助器用于创建在当前上下文中使用的计划程序。  通过 `Scheduler` 类，可以控制属于另一个上下文的计划程序。  
  
 下表显示了 `CurrentScheduler` 类所定义的重要方法。  
  
|方法|说明|  
|--------|--------|  
|[Create](../Topic/CurrentScheduler::Create%20Method.md)|创建一个使用指定策略的 `Scheduler` 对象，并将其与当前上下文相关联。|  
|[Get](../Topic/CurrentScheduler::Get%20Method.md)|检索指向与当前上下文关联的 `Scheduler` 对象的指针。  此方法不递增 `Scheduler` 对象的引用计数。|  
|[分离](../Topic/CurrentScheduler::Detach%20Method.md)|从当前上下文分离当前计划程序，并将上一个计划程序设置为当前计划程序。|  
|[RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md)|注册销毁当前计划程序时运行时设置的事件。|  
|[CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md)|在当前计划程序中，创建一个 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 对象。|  
|[ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md)|向当前计划程序的计划队列添加一个轻量级任务。|  
|[GetPolicy](../Topic/CurrentScheduler::GetPolicy%20Method.md)|检索与当前计划程序关联的策略的副本。|  
  
 下表显示了 `Scheduler` 类所定义的重要方法。  
  
|方法|说明|  
|--------|--------|  
|[Create](../Topic/Scheduler::Create%20Method.md)|创建使用指定策略的 `Scheduler` 对象。|  
|[附加](../Topic/Scheduler::Attach%20Method.md)|将 `Scheduler` 对象与当前上下文相关联。|  
|[引用](../Topic/Scheduler::Reference%20Method.md)|递增 `Scheduler` 对象的引用计数器。|  
|[Release](../Topic/Scheduler::Release%20Method.md)|递减 `Scheduler` 对象的引用计数器。|  
|[RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md)|注册销毁 `Scheduler` 对象时运行时设置的事件。|  
|[CreateScheduleGroup](../Topic/Scheduler::CreateScheduleGroup%20Method.md)|在 `Scheduler` 对象中创建 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 对象。|  
|[ScheduleTask](../Topic/Scheduler::ScheduleTask%20Method.md)|通过 `Scheduler` 对象计划轻量级任务。|  
|[GetPolicy](../Topic/Scheduler::GetPolicy%20Method.md)|检索与 `Scheduler` 对象关联的策略的副本。|  
|[SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)|设置当运行时创建默认计划程序时要使用的策略。|  
|[ResetDefaultSchedulerPolicy](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md)|将默认策略还原为在调用 `SetDefaultSchedulerPolicy` 之前处于活动状态的策略。  如果默认计划程序是在此调用后创建的，运行时将使用默认策略设置来创建该计划程序。|  
  
 \[[Top](#top)\]  
  
##  <a name="example"></a> 示例  
 有关如何创建和管理计划程序实例的基本示例，请参见[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。  
  
## 请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [计划程序策略](../../parallel/concrt/scheduler-policies.md)   
 [计划组](../../parallel/concrt/schedule-groups.md)