---
title: "计划程序实例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1688a2b689b3fc3391e617f3d65d3c681f05a84f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="scheduler-instances"></a>计划程序实例
本文档介绍中并发运行时以及如何使用计划程序实例的角色[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)和[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)类来创建和管理计划程序实例。 当你想要将显式计划策略与特定类型的工作负荷相关联，计划程序实例非常有用。 例如，你可以创建一个计划程序实例来以提升的线程优先级运行一些任务，并使用默认计划程序以普通线程优先级运行其他任务。  
  
> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序有助于细微调整你的应用程序的性能，我们建议你开始使用[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)如果你是新的并发运行。  
  
##  <a name="top"></a> 部分  
  
-   [计划程序和 CurrentScheduler 类](#classes)  
  
-   [创建计划程序实例](#creating)  
  
-   [管理计划程序实例的生存期](#managing)  
  
-   [方法和功能](#features)  
  
-   [示例](#example)  
  
##  <a name="classes"></a>计划程序和 CurrentScheduler 类  
 任务计划程序使应用程序可以使用一个或多*计划程序实例*来计划作业。 [Concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)类代表计划程序实例，并封装与计划任务相关的功能。  
  
 附加到计划程序线程被称为*执行上下文*，或仅仅称为*上下文*。 在任何时候，一个计划可以处于活动状态在当前上下文。 活动的计划程序也称为*当前计划程序*。 并发运行时使用[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)类以提供对当前计划程序的访问。 当前计划程序一个上下文可能与另一个上下文的当前计划程序不同。 运行时不提供当前计划程序的进程级表示。  
  
 通常情况下，`CurrentScheduler`类用于访问当前计划程序。 `Scheduler`需要管理的计划程序不是当前类很有用。  
  
 下列各节描述如何创建和管理计划程序实例。 有关完整示例，阐释了以下任务的说明，请参阅[如何： 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="creating"></a>创建计划程序实例  
 有以下三种方式创建`Scheduler`对象：  
  
-   如果没有计划程序存在，运行时创建默认计划程序运行时功能，例如，并行算法，用于执行工作。 默认计划程序将成为的当前计划程序启动的并行工作的上下文。  
  

-   [Concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)方法创建`Scheduler`对象，使用特定策略并将该计划程序与当前上下文相关联。  
  
-   [Concurrency::Scheduler::Create](reference/scheduler-class.md#create)方法创建`Scheduler`使用特定策略，但不将它与当前上下文关联的对象。  

  
 允许运行时创建默认计划程序使所有的并发任务能够共享同一个计划程序。 通常情况下，由提供的功能[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL) 或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)用于执行并行工作。 因此，无需直接使用计划程序来控制其策略或生存期。 当你使用 PPL 或代理库时，运行时将创建默认计划程序，如果它不存在，并使它为每个上下文的当前计划程序。 当你创建的计划，并将其设置为当前计划程序时，运行时将使用该计划程序来计划任务。 仅当你需要特定的计划策略时，请创建其他计划程序实例。 有关与计划程序关联的策略的详细信息，请参阅[计划程序策略](../../parallel/concrt/scheduler-policies.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="managing"></a>管理计划程序实例的生存期  
 运行时使用引用计数机制来控制的生存期`Scheduler`对象。  
  

 当你使用`CurrentScheduler::Create`方法或`Scheduler::Create`方法来创建`Scheduler`对象，运行时将该计划程序的初始引用计数设置为一。 运行时递增引用计数在调用时[concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)方法。 `Scheduler::Attach`方法将关联`Scheduler`对象与当前上下文。 这使得它当前计划程序。 当调用`CurrentScheduler::Create`方法时，运行时创建`Scheduler`对象并将其附加到当前上下文 （并将引用计数设置为一个）。 你还可以使用[concurrency::Scheduler::Reference](reference/scheduler-class.md#reference)方法以递增的引用计数`Scheduler`对象。  
  
 运行时递减引用计数在调用[concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach)方法以分离当前计划程序，或调用[concurrency::Scheduler::Release](reference/scheduler-class.md#release)方法。 当引用计数达到零时，运行时销毁`Scheduler`对象后所有计划任务完成。 正在运行的任务可以递增当前计划程序的引用计数。 因此，如果引用计数达到零时，并且任务递增引用计数，运行时不会销毁`Scheduler`对象的引用计数再次达到零和所有任务都完成之前。  

  
 运行时维护的内部堆栈`Scheduler`为每个上下文的对象。 当调用`Scheduler::Attach`或`CurrentScheduler::Create`方法时，运行时推送`Scheduler`对象拖放到当前上下文的堆栈。 这使得它当前计划程序。 当调用`CurrentScheduler::Detach`，运行时弹出从当前上下文的堆栈的当前计划程序并设置上的一个当前计划程序。  
  
 运行时提供多种方式来管理计划程序实例的生存期。 下表显示释放或分离从每个方法都创建或将计划程序附加到当前上下文的当前上下文的计划程序的适当方法。  
  
|创建或 attach 方法|释放或 detach 方法|  
|-----------------------------|------------------------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 调用不适当释放或分离方法生成未指定的行为运行时中。  
  
 当你使用的功能，例如，PPL 导致运行时创建默认计划程序，不释放或分离此计划程序。 运行时管理它会创建任何计划程序的生存期。  
  

 因为运行时不会销毁`Scheduler`对象在所有任务都完成之前，您可以使用[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法或[concurrency:: currentscheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法来接收通知时`Scheduler`对象被销毁。 这很有用时你必须等待所计划的每个任务`Scheduler`对象来完成。  
  
 [[返回页首](#top)]  
  
##  <a name="features"></a>方法和功能  
 此部分总结了的重要方法`CurrentScheduler`和`Scheduler`类。  
  
 想一想`CurrentScheduler`类作为用于在当前上下文中创建的计划程序使用的帮助。 `Scheduler`类可控制的计划程序属于另一个上下文。  
  
 下表显示由定义的重要方法`CurrentScheduler`类。  
  
|方法|描述|  
|------------|-----------------|  
|[创建](reference/currentscheduler-class.md#create)|创建`Scheduler`对象，使用指定的策略并将其与当前上下文关联起来。|  
|[Get](reference/currentscheduler-class.md#get)|检索指向的`Scheduler`与当前上下文关联的对象。 此方法引用不递增引用计数的`Scheduler`对象。|  
|[分离](reference/currentscheduler-class.md#detach)|分离当前计划程序，从当前上下文和设置当前计划程序上的一个。|  
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|注册的事件的运行时设置当前计划程序时销毁。|  
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|创建[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)当前计划程序中的对象。|  
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|将轻量级任务添加到当前计划程序计划队列中。|  
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|检索与当前计划程序关联的策略的副本。|  
  
 下表显示由定义的重要方法`Scheduler`类。  
  
|方法|描述|  
|------------|-----------------|  
|[创建](reference/scheduler-class.md#create)|创建`Scheduler`对象，它使用指定的策略。|  
|[附加](reference/scheduler-class.md#attach)|将相关联`Scheduler`对象与当前上下文。|  
|[参考](reference/scheduler-class.md#reference)|递增引用计数器的`Scheduler`对象。|  
|[发布](reference/scheduler-class.md#release)|递减的引用计数器`Scheduler`对象。|  
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|注册运行时设置时事件`Scheduler`对象被销毁。|  
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|创建[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)对象在`Scheduler`对象。|  
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|计划从轻量任务`Scheduler`对象。|  
|[GetPolicy](reference/scheduler-class.md#getpolicy)|检索与关联的策略副本`Scheduler`对象。|  
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|设置运行时，它会创建默认计划程序时要使用的策略。|  
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|将默认策略还原到之前调用处于活动状态的一个`SetDefaultSchedulerPolicy`。 如果此调用后创建默认计划程序，则运行时将使用默认策略设置来创建计划程序。|  

  
 [[返回页首](#top)]  
  
##  <a name="example"></a> 示例  
 有关如何创建和管理计划程序实例的基本示例，请参阅[如何： 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。  
  
## <a name="see-also"></a>请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何： 管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [计划程序策略](../../parallel/concrt/scheduler-policies.md)   
 [计划组](../../parallel/concrt/schedule-groups.md)

