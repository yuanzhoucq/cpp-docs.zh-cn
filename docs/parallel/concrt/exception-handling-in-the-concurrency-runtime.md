---
title: 并发运行时中的异常处理
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: 4c7fee363da023b9252471a35aaecd262a55f17c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141791"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>并发运行时中的异常处理

并发运行时使用C++异常处理来传达多种类型的错误。 这些错误包括对运行时的使用、运行时错误（例如获取资源失败）以及在提供给任务和任务组的工作函数中发生的错误。 当任务或任务组引发异常时，运行时会保存该异常，并将其封送到等待任务或任务组完成的上下文中。 对于轻量级任务和代理等组件，运行时不会为你管理异常。 在这些情况下，必须实现自己的异常处理机制。 本主题介绍运行时如何处理任务、任务组、轻量级任务和异步代理引发的异常以及如何在应用程序中响应异常。

## <a name="key-points"></a>关键点

- 当任务或任务组引发异常时，运行时会保存该异常，并将其封送到等待任务或任务组完成的上下文中。

- 如果可能，请将每次调用[concurrency：： task：： get](reference/task-class.md#get)和[concurrency：： task：： wait](reference/task-class.md#wait)与 `try`/`catch` 块以处理可从恢复的错误。 如果任务引发异常，并且任务、该任务的延续之一或主应用无法捕获该异常，则运行时会终止应用。

- 基于任务的延续始终运行;前面的任务是否已成功完成、引发异常或已取消，这并不重要。 如果前面的任务引发或取消，则基于值的延续将不会运行。

- 由于基于任务的延续始终运行，因此请考虑是否在延续链的末尾添加基于任务的继续符。 这有助于保证你的代码能够观察到所有异常。

- 调用[concurrency：： task：： get](reference/task-class.md#get)并且取消该任务时，运行时将引发[concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md) 。

- 运行时不会管理轻量级任务和代理的异常。

## <a name="top"></a>本文档中

- [任务和延续](#tasks)

- [任务组和并行算法](#task_groups)

- [运行时引发的异常](#runtime)

- [多个异常](#multiple)

- [取消](#cancellation)

- [轻量级任务](#lwts)

- [异步代理](#agents)

## <a name="tasks"></a>任务和延续

本部分介绍运行时如何处理[concurrency：： task](../../parallel/concrt/reference/task-class.md)对象及其延续引发的异常。 有关任务和延续模型的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

当你在传递到 `task` 对象的工作函数体中引发异常时，运行时将存储该异常，并将其封送到调用[concurrency：： task：： get](reference/task-class.md#get)或[concurrency：： task：： wait](reference/task-class.md#wait)的上下文中。 文档[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)性描述基于任务和基于值的延续，但要进行汇总，基于值的延续采用类型 `T` 的参数，基于任务的继续采用 `task<T>`类型的参数。 如果引发的任务具有一个或多个基于值的延续，则不计划运行这些延续任务。 下面的示例阐释了这种行为：

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

基于任务的延续使你可以处理前面的任务所引发的任何异常。 基于任务的延续始终运行;任务是否已成功完成、引发异常或已取消，这并不重要。 当任务引发异常时，将计划运行其基于任务的延续任务。 下面的示例演示始终引发的任务。 该任务具有两个延续：一个是基于值的，另一个是基于任务的。 基于任务的异常始终运行，因此可以捕获前面的任务所引发的异常。 当示例等待两个延续都完成时，将再次引发异常，因为调用 `task::get` 或 `task::wait` 时，始终会引发异常。

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

建议使用基于任务的延续来捕获能够处理的异常。 由于基于任务的延续始终运行，因此请考虑是否在延续链的末尾添加基于任务的继续符。 这有助于保证你的代码能够观察到所有异常。 下面的示例演示一个基于值的基本延续链。 该链中的第三个任务将引发，因此不会运行遵循它的任何基于值的延续。 不过，最后一个延续是基于任务的，因此始终运行。 这最后一个延续处理第三个任务引发的异常。

建议您捕获最具体的异常。 如果没有要捕捉的特定异常，则可以省略此最后一个基于任务的继续符。 任何异常都将保持未处理的，并可以终止应用程序。

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
> 你可以使用[concurrency：： task_completion_event：： set_exception](../../parallel/concrt/reference/task-completion-event-class.md)方法将异常与任务完成事件关联。 文档[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)对[concurrency：： task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)类进行了更详细的介绍。

[concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md)是与 `task`相关的重要运行时异常类型。 调用 `task::get` 并且该任务被取消时，运行时将引发 `task_canceled`。 （相反，`task::wait` 返回[task_status：：已取消](reference/concurrency-namespace-enums.md#task_group_status)且不引发。）你可以从基于任务的继续或在调用 `task::get`时捕获和处理此异常。 有关任务取消的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

> [!CAUTION]
> 切勿从代码中引发 `task_canceled`。 改[为调用 concurrency：： cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) 。

如果任务引发异常，并且任务、该任务的延续之一或主应用无法捕获该异常，则运行时会终止应用。 如果你的应用程序崩溃，你可以将 Visual Studio 配置C++为在引发异常时中断。 诊断未经处理的异常的位置后，使用基于任务的延续来处理该异常。

本文档中[由运行时引发](#runtime)的部分异常介绍了如何更详细地使用运行时异常。

[[返回页首](#top)]

## <a name="task_groups"></a>任务组和并行算法

本部分介绍运行时如何处理任务组引发的异常。 本节还适用于并行算法，如[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)，因为这些算法基于任务组构建。

> [!CAUTION]
> 请确保了解例外对依赖任务的影响。 有关如何将异常处理与任务或并行算法一起使用的建议做法，请参阅并行模式库中的最佳实践主题中的[了解取消和异常处理如何影响对象析构](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)部分。

有关任务组的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 有关并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

当你在传递给[concurrency：： task_group](reference/task-group-class.md)或[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象的工作函数体中引发异常时，运行时将存储该异常，并将其封送到调用[concurrency：： task_group：： wait](reference/task-group-class.md#wait)、 [concurrency：： structured_task_group：： wait](reference/structured-task-group-class.md#wait)、 [concurrency：： task_group：：](reference/task-group-class.md#run_and_wait)run_and_wait 或[concurrency：](reference/structured-task-group-class.md#run_and_wait)： structured_task_group：： run_and_wait 的上下文中。 运行时还会停止任务组中的所有活动任务（包括子任务组中的任务），并放弃尚未启动的所有任务。

下面的示例演示引发异常的工作函数的基本结构。 该示例使用 `task_group` 对象并行打印两个 `point` 对象的值。 `print_point` 工作函数将 `point` 对象的值打印到控制台。 如果输入值为 `NULL`，则工作函数将引发异常。 运行时存储此异常，并将其封送到调用 `task_group::wait`的上下文中。

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

本示例生成以下输出。

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

有关在任务组中使用异常处理的完整示例，请参阅[如何：使用异常处理中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

[[返回页首](#top)]

## <a name="runtime"></a>运行时引发的异常

调用运行时可能会引发异常。 大多数异常类型（ [concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md)和[concurrency：： operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md)除外）表示存在编程错误。 这些错误通常是不可恢复的，因此不应由应用程序代码捕获或处理。 如果需要诊断编程错误，建议您仅捕获或处理应用程序代码中无法恢复的错误。 但是，了解运行时定义的异常类型可帮助你诊断编程错误。

对于作为工作函数引发的异常的运行时引发的异常，异常处理机制是相同的。 例如， [concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函数在指定的时间段内未收到消息时，将引发 `operation_timed_out`。 如果 `receive` 在传递到任务组的工作函数中引发异常，则运行时将存储该异常，并将其封送到调用 `task_group::wait`、`structured_task_group::wait`、`task_group::run_and_wait`或 `structured_task_group::run_and_wait`的上下文中。

下面的示例使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法并行运行两个任务。 第一个任务等待5秒，然后将消息发送到消息缓冲区。 第二个任务使用 `receive` 函数等待三秒钟，以接收来自同一消息缓冲区的消息。 如果 `receive` 函数在时间段内未收到消息，则会引发 `operation_timed_out`。

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

本示例生成以下输出。

```Output
The operation timed out.
```

若要防止应用程序异常终止，请确保代码在调用运行时时处理异常。 当你调入使用并发运行时的外部代码（例如，第三方库）时，还会处理异常。

[[返回页首](#top)]

## <a name="multiple"></a>多个异常

如果任务或并行算法接收多个异常，则运行时只会将其中一个异常封送到调用上下文。 运行时不保证它封送处理的异常。

下面的示例使用 `parallel_for` 算法将数字输出到控制台。 如果输入值小于某些最小值或大于最大值，则会引发异常。 在此示例中，多个工作函数可能会引发异常。

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

下面显示了此示例的示例输出。

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[返回页首](#top)]

## <a name="cancellation"></a>通知

并非所有异常都表示错误。 例如，搜索算法可能会在找到结果时使用异常处理来停止关联的任务。 有关如何在代码中使用取消机制的详细信息，请参阅[PPL 中的取消](../../parallel/concrt/cancellation-in-the-ppl.md)操作。

[[返回页首](#top)]

## <a name="lwts"></a>轻量级任务

轻量级任务是直接从[concurrency：：](../../parallel/concrt/reference/scheduler-class.md) schedule 对象计划的任务。 轻量级任务比普通任务的开销更少。 但是，运行时不会捕获轻量级任务引发的异常。 相反，此异常由未经处理的异常处理程序捕获，该处理程序在默认情况下会终止进程。 因此，请在应用程序中使用适当的错误处理机制。 有关轻量级任务的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[返回页首](#top)]

## <a name="agents"></a>异步代理

与轻量级任务一样，运行时不会管理异步代理引发的异常。

下面的示例演示了一种方法，用于处理从[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)派生的类中的异常。 此示例定义了 `points_agent` 类。 `points_agent::run` 方法从消息缓冲区中读取 `point` 对象，并将这些对象输出到控制台。 如果 `run` 方法收到 `NULL` 指针，则会引发异常。

`run` 方法将所有工作括在 `try`-`catch` 块中。 `catch` 块在消息缓冲区中存储异常。 在代理完成后，应用程序通过从此缓冲区读取来检查代理是否遇到错误。

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

本示例生成以下输出。

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

由于 `try`-`catch` 块存在于 `while` 循环之外，因此在遇到第一个错误时，代理将结束处理。 如果 `try`-`catch` 块在 `while` 循环内，则在发生错误后，代理将继续。

此示例将异常存储在消息缓冲区中，以便其他组件可以在代理运行时监视其错误。 此示例使用[concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)对象存储错误。 在代理处理多个异常的情况下，`single_assignment` 类只存储传递给它的第一条消息。 若要仅存储最后一个异常，请使用[concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)类。 若要存储所有异常，请使用[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)类。 有关这些消息块的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

有关异步代理的详细信息，请参阅[异步代理](../../parallel/concrt/asynchronous-agents.md)。

[[返回页首](#top)]

## <a name="summary"></a> 摘要

[[返回页首](#top)]

## <a name="see-also"></a>另请参阅

[并发运行时](../../parallel/concrt/concurrency-runtime.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)
