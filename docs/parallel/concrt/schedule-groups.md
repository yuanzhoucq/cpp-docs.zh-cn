---
title: "计划组 | Microsoft Docs"
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
  - "计划组"
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 计划组
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍并发运行时中计划组的角色。 一个 *计划组* 将，或，相关的任务组合到一起。 每个计划程序有一个或多个计划组。 当你需要在任务之间处于较高位置时（例如，当一组相关的任务受益于在相同的处理器节点上执行操作时），可使用计划组。 如果应用程序特定质量要求，例如，当你想要限制分配给一组任务的处理资源量，相反，使用计划程序实例。 有关计划程序实例的详细信息，请参阅 [计划程序实例](../../parallel/concrt/scheduler-instances.md)。  
  
> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序可帮助您优化您的应用程序的性能，我们建议您从开始 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md) 如果您不熟悉并发运行时。  
  
 每个 `Scheduler` 对象都有计划的每个节点的默认计划组。 一个 *计划节点* 映射到基础系统拓扑。 运行时创建一个计划节点对于每个处理器包或非统一内存体系结构 (NUMA) 节点，数字较大者。 如果您没有将任务与计划组显式关联，计划程序会选择要添加到任务的组。  
  
  `SchedulingProtocol` 计划程序策略会影响计划程序执行每个计划组中的任务的顺序。 当 `SchedulingProtocol` 设置为 `EnhanceScheduleGroupLocality` （这是默认值），任务计划程序可从它还致力于在当前任务完成或通过协作时的计划组中选择下一个任务。 它将移到下一个可用组之前，任务计划程序将搜索工作的当前计划组。 相反，当 `SchedulingProtocol` 设置为 `EnhanceForwardProgress`, ，每个任务完成或生成后，计划程序将移到下一步的计划组。 将这些策略进行比较的示例，请参阅 [如何︰ 使用计划组影响执行顺序为](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
 运行时使用 [concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md) 类来表示计划组。 若要创建 `ScheduleGroup` 对象，请调用 [concurrency::CurrentScheduler::CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md) 或 [concurrency::Scheduler::CreateScheduleGroup](../Topic/Scheduler::CreateScheduleGroup%20Method.md) 方法。 运行时使用引用计数机制来控制的生存期 `ScheduleGroup` 对象时，就像它对待 `Scheduler` 对象。 当您创建 `ScheduleGroup` 对象时，运行时将该引用设置到其中一个计数器。  [Concurrency::ScheduleGroup::Reference](../Topic/ScheduleGroup::Reference%20Method.md) 方法逐个递增引用计数器。  [Concurrency::ScheduleGroup::Release](../Topic/ScheduleGroup::Release%20Method.md) 方法递减一个引用计数器。  
  
 并发运行时中的许多类型，可以将对象的计划组以及相关联。 例如， [concurrency:: agent](../../parallel/concrt/reference/agent-class.md) 类和消息块类，如 [concurrency:: unbounded_buffer](../Topic/unbounded_buffer%20Class.md), ，[concurrency:: join](../../parallel/concrt/reference/join-class.md), ，和并发::[计时器](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d5d4c847-5ad6-4c7f-b35b-d0b6f446d8b4/locales/en-US), ，提供的构造函数的重载的版本，较 `ScheduleGroup` 对象。 运行时使用 `Scheduler` 对象，它是与此关联 `ScheduleGroup` 对象来计划任务。  
  
 您还可以使用 [concurrency::ScheduleGroup::ScheduleTask](../Topic/ScheduleGroup::ScheduleTask%20Method.md) 方法来计划轻量级任务。 轻量级任务的详细信息，请参阅 [轻量级任务](../../parallel/concrt/lightweight-tasks.md)。  
  
## <a name="example"></a>示例  
 使用计划组来控制对任务执行的顺序示例，请参阅 [如何︰ 使用计划组影响执行顺序为](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [计划程序实例](../../parallel/concrt/scheduler-instances.md)   
 [如何︰ 使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

