---
title: 计划程序策略
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: e2acfc199e7ad9edf3965dc8ccb4103eb615a66b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298123"
---
# <a name="scheduler-policies"></a>计划程序策略

本文档介绍并发运行时中的计划程序策略的角色。 一个*计划程序策略*控制计划程序使用它管理任务时的策略。 例如，假设一个应用程序需要某些任务在 `THREAD_PRIORITY_NORMAL` 上执行，而其他任务在 `THREAD_PRIORITY_HIGHEST` 上执行。  您可以创建两个计划程序实例：一个指定 `ContextPriority` 策略为 `THREAD_PRIORITY_NORMAL`，另一个指定同一策略为 `THREAD_PRIORITY_HIGHEST`。

通过使用计划程序策略，您可以划分可用处理资源并将一组固定的资源分配给每个计划程序。 例如，考虑作用范围不超过四个处理器的并行算法。 可以创建限制其任务，以同时使用不超过四个处理器的计划程序策略。

> [!TIP]
>  并发运行时提供默认计划程序。 因此，不必在应用程序中创建计划程序。 因为任务计划程序可帮助您优化您的应用程序的性能，我们建议您开始[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)你是否新并发运行时。

当你使用[concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)， [concurrency::Scheduler::Create](reference/scheduler-class.md#create)，或[concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)方法创建的计划程序实例，则提供[concurrency:: schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)对象，其中包含指定的计划程序行为的键 / 值对的集合。 `SchedulerPolicy`构造函数采用数目可变的参数。 第一个参数是要指定的策略元素的数目。 其余的参数是为每个策略元素的键 / 值对。 下面的示例创建`SchedulerPolicy`对象，它指定三个策略元素。 运行时对未指定的策略键使用默认值。

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

[Concurrency:: policyelementkey](reference/concurrency-namespace-enums.md#policyelementkey)枚举定义与任务计划程序关联的策略键。 下表描述的策略键并为每个运行时使用的默认值。

|策略密钥|描述|默认值|
|----------------|-----------------|-------------------|
|`SchedulerKind`|一个[concurrency:: schedulertype](reference/concurrency-namespace-enums.md#schedulertype)值，该值指定要用于计划任务的线程的类型。|`ThreadScheduler`（使用正常线程）。 这是此键的唯一有效值。|
|`MaxConcurrency`|`unsigned int`值，该值指定并发计划程序使用的资源的最大数目。|[concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|`unsigned int`值，该值指定并发计划程序使用的资源的最小数目。|`1`|
|`TargetOversubscriptionFactor`|`unsigned int`值，该值指定要分配给每个处理资源的线程数。|`1`|
|`LocalContextCacheSize`|`unsigned int`值，该值指定可以缓存的上下文的最大数目，每个虚拟处理器的本地队列中。|`8`|
|`ContextStackSize`|`unsigned int`值，该值指定在堆栈的大小，为每个上下文保留千字节为单位。|`0` （使用默认堆栈大小）|
|`ContextPriority`|`int`值，该值指定每个上下文的线程优先级别。 这可以是任何值，可以将传递到[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)或`INHERIT_THREAD_PRIORITY`。|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`|一个[concurrency:: schedulingprotocoltype](reference/concurrency-namespace-enums.md#schedulingprotocoltype)值，该值指定要使用的计划算法。 |`EnhanceScheduleGroupLocality`| |`DynamicProgressFeedback`|一个[concurrency:: dynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype)值，该值指定是否要重新平衡资源根据基于统计信息的进度信息。<br /><br /> **请注意**未设置此策略为`ProgressFeedbackDisabled`因为它保留供运行时。 |`ProgressFeedbackEnabled`|

每个计划程序安排的任务时使用自己的策略。 与一个计划程序关联的策略不影响任何其他计划程序的行为。 此外，不能更改的计划程序策略在创建后`Scheduler`对象。

> [!IMPORTANT]
>  使用仅计划程序策略来控制运行时创建的线程的属性。 不要更改线程关联或运行时创建的线程的优先级，因为这可能会导致未定义的行为。

运行时创建一个默认计划程序为你如果你未显式创建一个。 如果你想要在应用程序中使用的默认计划程序，但你想要为该计划程序来使用，调用指定策略[concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)方法之前在计划并行工作。 如果不调用`Scheduler::SetDefaultSchedulerPolicy`方法，运行时使用的默认策略值表中。

使用[concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy)并[concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy)方法来检索计划程序策略的副本。 接收从这些方法的策略值可以不同于在创建计划程序时指定的策略值。

## <a name="example"></a>示例

若要查看使用特定计划程序策略来控制计划程序的行为的示例，请参阅[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)和[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。

## <a name="see-also"></a>请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
