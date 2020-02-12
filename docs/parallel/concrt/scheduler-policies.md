---
title: 计划程序策略
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 0f90b461ecba702501c2f6919572dc828c80907f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142286"
---
# <a name="scheduler-policies"></a>计划程序策略

本文档介绍并发运行时中计划程序策略的角色。 *计划程序策略*控制计划程序在管理任务时使用的策略。 例如，假设一个应用程序需要某些任务在 `THREAD_PRIORITY_NORMAL` 上执行，而其他任务在 `THREAD_PRIORITY_HIGHEST` 上执行。  您可以创建两个计划程序实例：一个指定 `ContextPriority` 策略为 `THREAD_PRIORITY_NORMAL`，另一个指定同一策略为 `THREAD_PRIORITY_HIGHEST`。

通过使用计划程序策略，您可以划分可用处理资源并将一组固定的资源分配给每个计划程序。 例如，假设并行算法不能扩展到四个处理器。 可以创建计划程序策略，将其任务限制为使用四个以上的处理器。

> [!TIP]
> 并发运行时提供默认计划程序。 因此，不必在应用程序中创建计划程序。 由于任务计划程序有助于微调应用程序的性能，因此，如果你不熟悉并发运行时，则建议你从[并行模式库（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)开始。

使用[concurrency：： CurrentScheduler：： create](reference/currentscheduler-class.md#create)、 [Concurrency：：调度](reference/scheduler-class.md#create)器：： create 或[concurrency：： SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)方法创建计划程序实例时，需要提供[concurrency：： SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)对象，该对象包含指定计划程序行为的键值对的集合。 `SchedulerPolicy` 构造函数采用可变数量的参数。 第一个参数是要指定的策略元素的数目。 其余的参数是每个策略元素的键值对。 下面的示例创建一个 `SchedulerPolicy` 对象，该对象指定三个策略元素。 运行时对未指定的策略键使用默认值。

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

[Concurrency：:P olicyelementkey](reference/concurrency-namespace-enums.md#policyelementkey)枚举定义与任务计划程序关联的策略密钥。 下表描述了运行时为每个策略密钥和默认值使用的默认值。

|策略密钥|说明|默认值|
|----------------|-----------------|-------------------|
|`SchedulerKind`|[Concurrency：： SchedulerType](reference/concurrency-namespace-enums.md#schedulertype)值，指定用于计划任务的线程类型。|`ThreadScheduler`（使用正常线程）。 这是此键的唯一有效值。|
|`MaxConcurrency`|一个 `unsigned int` 值，该值指定计划程序使用的最大并发资源数。|[concurrency：： MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|一个 `unsigned int` 值，该值指定计划程序使用的最小并发资源数。|`1`|
|`TargetOversubscriptionFactor`|一个 `unsigned int` 值，该值指定要分配给每个处理资源的线程数。|`1`|
|`LocalContextCacheSize`|一个 `unsigned int` 值，该值指定可以在每个虚拟处理器的本地队列中缓存的最大上下文数。|`8`|
|`ContextStackSize`|一个 `unsigned int` 值，该值指定要为每个上下文保留的堆栈大小（以 kb 为单位）。|`0` （使用默认堆栈大小）|
|`ContextPriority`|一个 `int` 值，该值指定每个上下文的线程优先级。 这可以是可传递给[参见 setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority)或 `INHERIT_THREAD_PRIORITY`的任何值。|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`|一个[concurrency：： SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype)值，该值指定要使用的计划算法。 |`EnhanceScheduleGroupLocality`| |`DynamicProgressFeedback`|[Concurrency：:D ynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype)值，该值指定是否根据基于统计信息的进度信息重新平衡资源。<br /><br /> **注意**请勿将此策略设置为 "`ProgressFeedbackDisabled`"，因为它是保留供运行时使用的。 |`ProgressFeedbackEnabled`|

每个计划程序在计划任务时使用其自己的策略。 与一个计划程序关联的策略不影响任何其他计划程序的行为。 此外，创建 `Scheduler` 对象后，将无法更改计划程序策略。

> [!IMPORTANT]
> 仅使用计划程序策略来控制运行时创建的线程的属性。 不要更改线程关联或运行时创建的线程的优先级，因为这可能会导致未定义的行为。

如果未显式创建，则运行时将为您创建一个默认计划程序。 如果要在应用程序中使用默认计划程序，但要为该计划程序指定要使用的策略，请在计划并行工作之前调用[concurrency：： schedule：： SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)方法。 如果未调用 `Scheduler::SetDefaultSchedulerPolicy` 方法，则运行时使用表中的默认策略值。

使用[concurrency：： CurrentScheduler：： GetPolicy](reference/currentscheduler-class.md#getpolicy)和[Concurrency：：：： GetPolicy](reference/scheduler-class.md#getpolicy)方法检索计划程序策略的副本。 从这些方法接收到的策略值可能与创建计划程序时指定的策略值不同。

## <a name="example"></a>示例

若要检查使用特定计划程序策略来控制计划程序行为的示例，请参阅[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)和[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)。

## <a name="see-also"></a>另请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
