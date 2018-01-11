---
title: "计划组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a61566878adc539af21e1645844eff27c5a8aec0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="schedule-groups"></a>计划组
本文档介绍并发运行时中的计划组的角色。 A*计划组*关联，或，相关的任务组合到一起。 每个计划程序具有一个或多个计划组。 当你需要在任务之间处于较高位置时（例如，当一组相关的任务受益于在相同的处理器节点上执行操作时），可使用计划组。 如果应用程序特定的质量要求，例如，当你想要限制分配给一组任务的处理资源量，相反，使用计划程序实例。 有关计划程序实例的详细信息，请参阅[计划程序实例](../../parallel/concrt/scheduler-instances.md)。  
  
> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序有助于细微调整你的应用程序的性能，我们建议你开始使用[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)如果你是新的并发运行。  
  
 每个`Scheduler`对象具有计划的每个节点的默认计划组。 A*计划节点*映射到基础系统拓扑。 运行时创建一个计划节点对于每个处理器包或非统一内存体系结构 (NUMA) 节点，数字较大者。 如果你未将任务的计划组与显式关联，计划程序会选择要添加到任务的组。  
  
 `SchedulingProtocol`计划程序策略会影响计划程序在其中执行每个计划组中的任务的顺序。 当`SchedulingProtocol`设置为`EnhanceScheduleGroupLocality`（这是默认值），任务计划程序可从它正在当前任务完成，或以协作方式生成时的计划组中选择下一个任务。 任务计划程序搜索工作的当前计划组之前它将移到下一个可用的组。 相反，当`SchedulingProtocol`设置为`EnhanceForwardProgress`，每个任务完成，或生成后，计划程序将移到下一步的计划组。 将这些策略进行比较的示例，请参阅[如何： 使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  

 运行时使用[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)类来表示计划组。 若要创建`ScheduleGroup`对象，请调用[concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)或[concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)方法。 运行时使用引用计数机制来控制的生存期`ScheduleGroup`对象，就像它与`Scheduler`对象。 当你创建`ScheduleGroup`对象时，运行时将引用设置到其中一个计数器。 [Concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference)方法递增引用计数器 1。 [Concurrency::ScheduleGroup::Release](reference/schedulegroup-class.md#release)方法递减一个引用计数器。  
  
 并发运行时中的许多类型，可以将对象与计划组相关联。 例如， [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)类和消息块类，如[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)， [concurrency:: join](../../parallel/concrt/reference/join-class.md)，和并发::[计时器](reference/timer-class.md)，提供的构造函数的重载的版本，较`ScheduleGroup`对象。 运行时使用`Scheduler`与此关联的对象`ScheduleGroup`对象来计划任务。  
  
 你还可以使用[concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask)方法来计划轻量级任务。 轻量级任务有关的详细信息，请参阅[轻量级任务](../../parallel/concrt/lightweight-tasks.md)。  

  
## <a name="example"></a>示例  
 使用计划组来控制任务执行的顺序示例，请参阅[如何： 使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
## <a name="see-also"></a>请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [计划程序实例](../../parallel/concrt/scheduler-instances.md)   
 [如何：使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

