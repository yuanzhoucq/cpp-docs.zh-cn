---
title: 计划程序实例
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: 19bd871857dcef6aaef153798388c0272239fa1f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301293"
---
# <a name="scheduler-instances"></a>计划程序实例

本文档介绍并发运行时以及如何使用计划程序实例的角色[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)并[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)类来创建和管理计划程序实例。 当你想要将显式计划策略与特定类型的工作负荷相关联时，计划程序实例很有用。 例如，你可以创建一个计划程序实例来以提升的线程优先级运行一些任务，并使用默认计划程序以普通线程优先级运行其他任务。

> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 因为任务计划程序可帮助您优化您的应用程序的性能，我们建议您开始[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)你是否新并发运行时。

##  <a name="top"></a> 部分

- [计划程序和 CurrentScheduler 类](#classes)

- [创建计划程序实例](#creating)

- [管理计划程序实例的生存期](#managing)

- [方法和功能](#features)

- [示例](#example)

##  <a name="classes"></a> 计划程序和 CurrentScheduler 类

任务计划程序允许应用程序使用一个或多个*计划程序实例*安排工作。 [Concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)类表示计划程序实例并封装与计划任务相关的功能。

附加到计划程序线程被称为*执行上下文*，或仅*上下文*。 在任何时候，一个计划程序可以处于活动状态在当前上下文。 活动的计划程序也称为*当前计划程序*。 并发运行时使用[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)类，以提供对当前计划程序的访问。 一个上下文的当前计划程序可能不同于另一个上下文的当前计划程序。 在运行时不提供当前计划程序的进程级表示形式。

通常情况下，`CurrentScheduler`类用于访问当前计划程序。 `Scheduler`需要管理的计划程序不是当前类十分有用。

以下部分介绍如何创建和管理计划程序实例。 有关完整示例，说明了这些任务的说明，请参阅[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。

[[返回页首](#top)]

##  <a name="creating"></a> 创建计划程序实例

有以下三种方法来创建`Scheduler`对象：

- 如果没有计划程序存在，则运行时创建一个默认计划程序为你使用运行时功能，例如，并行算法来执行工作。 默认计划程序将成为启动并行工作的上下文的当前计划程序。

- [Concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)方法创建`Scheduler`使用特定策略并将该计划程序与当前上下文关联的对象。

- [Concurrency::Scheduler::Create](reference/scheduler-class.md#create)方法创建`Scheduler`使用特定策略，但不会将它与当前上下文关联的对象。

允许运行时创建一个默认计划程序允许所有的并发任务可以共享相同的计划程序。 通常情况下，由提供的功能[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL) 或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)用于执行并行工作。 因此，无需直接使用计划程序来控制其策略或有生存期。 当你使用 PPL 或代理库时，运行时将创建默认计划程序，如果它不存在，并使其每个上下文的当前计划程序。 如果您创建的计划，将其设置为当前计划程序运行时将使用该计划程序计划任务。 只有当需要特定的计划策略时，请创建其他计划程序实例。 有关与计划程序关联的策略的详细信息，请参阅[计划程序策略](../../parallel/concrt/scheduler-policies.md)。

[[返回页首](#top)]

##  <a name="managing"></a> 管理计划程序实例的生存期

运行时使用的引用计数机制来控制的生存期`Scheduler`对象。

当你使用`CurrentScheduler::Create`方法或`Scheduler::Create`方法来创建`Scheduler`对象时，运行时该计划程序的初始引用计数设置为 1。 在运行时递增引用计数在调用时[concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)方法。 `Scheduler::Attach`方法将`Scheduler`对象与当前上下文。 这样，就在当前计划程序。 当您调用`CurrentScheduler::Create`方法时，运行时这两种创建`Scheduler`对象并将其附加到当前上下文 （和引用计数设置为 1）。 此外可以使用[concurrency::Scheduler::Reference](reference/scheduler-class.md#reference)方法来递增引用数`Scheduler`对象。

运行时递减引用计数在调用[concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach)方法以分离当前计划程序，或调用[concurrency::Scheduler::Release](reference/scheduler-class.md#release)方法。 当引用计数达到零时，运行时销毁`Scheduler`对象后所有计划任务完成。 允许正在运行的任务来增加当前计划程序的引用计数。 因此，如果引用计数达到零时，并且任务递增引用计数，在运行时不会销毁`Scheduler`对象，直到引用计数再次达到零，所有任务都完成。

在运行时维护的内部堆栈`Scheduler`为每个上下文的对象。 当您调用`Scheduler::Attach`或`CurrentScheduler::Create`方法中，运行时推送的`Scheduler`到当前上下文堆栈上的对象。 这样，就在当前计划程序。 当您调用`CurrentScheduler::Detach`，运行时从当前计划程序从当前上下文的堆栈中弹出和设置当前计划程序上的一个。

在运行时提供多种方式来管理计划程序实例的生存期。 下表显示了相应的方法释放或分离的计划程序从每个方法的创建，或将一个计划程序附加到当前上下文的当前上下文。

|创建或附加方法|释放或分离方法|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

调用不适当发布或分离方法会生成未指定的行为运行时中。

当您使用的功能，例如，PPL 导致要创建您的默认计划程序的运行时，不发布或分离此计划程序。 在运行时管理它会创建任何计划程序的生存期。

因为运行时不会销毁`Scheduler`对象的所有任务都完成之前，您可以使用[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法或[concurrency:: currentscheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法来接收通知时`Scheduler`对象被销毁。 这是有用的必须等待所计划的每个任务时`Scheduler`对象才能完成。

[[返回页首](#top)]

##  <a name="features"></a> 方法和功能

本部分中总结的重要方法`CurrentScheduler`和`Scheduler`类。

想一想`CurrentScheduler`作为创建使用的计划程序在当前上下文的帮助程序类。 `Scheduler`类可用于控制的计划程序属于另一个上下文。

下表显示了由定义的重要方法`CurrentScheduler`类。

|方法|描述|
|------------|-----------------|
|[创建](reference/currentscheduler-class.md#create)|创建`Scheduler`对象，它使用指定的策略并将其与当前上下文关联起来。|
|[Get](reference/currentscheduler-class.md#get)|检索指向的`Scheduler`与当前上下文关联的对象。 此方法不会递增引用数`Scheduler`对象。|
|[分离](reference/currentscheduler-class.md#detach)|从当前上下文的当前计划程序中分离，并设置当前计划程序上的一个。|
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|注册时销毁当前计划程序运行时设置的事件。|
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|创建[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)当前计划程序中的对象。|
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|将轻量级任务添加到当前计划程序在调度队列中。|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|检索与当前计划程序相关联的策略的副本。|

下表显示了由定义的重要方法`Scheduler`类。

|方法|描述|
|------------|-----------------|
|[创建](reference/scheduler-class.md#create)|创建`Scheduler`对象，它使用指定的策略。|
|[附加](reference/scheduler-class.md#attach)|将相关联`Scheduler`对象与当前上下文。|
|[引用](reference/scheduler-class.md#reference)|递增引用计数器的`Scheduler`对象。|
|[发布](reference/scheduler-class.md#release)|递减的引用计数器`Scheduler`对象。|
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|注册一个运行时设置的事件`Scheduler`对象被销毁。|
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|创建[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)对象中`Scheduler`对象。|
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|计划轻量级任务从`Scheduler`对象。|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|检索与之关联的策略的副本`Scheduler`对象。|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|设置运行时要创建的默认计划程序时所使用的策略。|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|还原到之前调用处于活动状态的默认策略`SetDefaultSchedulerPolicy`。 如果此调用后创建的默认计划程序，则运行时将使用默认策略设置来创建计划程序。|

[[返回页首](#top)]

##  <a name="example"></a> 示例

有关如何创建和管理计划程序实例的基本示例，请参阅[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)。

## <a name="see-also"></a>请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[计划程序策略](../../parallel/concrt/scheduler-policies.md)<br/>
[计划组](../../parallel/concrt/schedule-groups.md)
