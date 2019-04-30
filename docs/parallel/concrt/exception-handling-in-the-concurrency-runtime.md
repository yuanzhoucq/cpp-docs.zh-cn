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
ms.openlocfilehash: 8239913c369605503134a9ea4c99789528911868
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413926"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>并发运行时中的异常处理

并发运行时使用C++进行通信的许多种错误的异常处理。 这些错误包括提供对任务和任务组的工作函数中使用无效的运行时、 运行时错误问题，无法获取资源，例如和发生的错误。 当任务或任务组引发了异常时，运行时保存该异常，并将其封送到等待的任务或任务组完成的上下文。 对于如轻量级任务和代理组件，运行时不管理为你的异常。 在这些情况下，必须实现您自己的异常处理机制。 本主题介绍如何在运行时处理由任务、 任务组、 轻量级任务和异步代理引发的异常以及如何在您的应用程序中响应异常。

## <a name="key-points"></a>关键点

- 当任务或任务组引发了异常时，运行时保存该异常，并将其封送到等待的任务或任务组完成的上下文。

- 如果可能，括起来的每个调用[concurrency::task::get](reference/task-class.md#get)并[concurrency::task::wait](reference/task-class.md#wait)与`try` / `catch`块，以便可以恢复的错误从。 如果任务引发了异常和任务，其延续或主应用程序之一不捕获异常，运行时终止应用程序。

- 基于任务的延续始终运行;是否已成功完成，在前面的任务引发了异常，或已取消，并不重要。 如果在前面的任务将引发或取消，基于值的延续将不运行。

- 由于基于任务的延续始终运行，因此请考虑是否在延续任务链的末尾添加基于任务的延续。 这可以帮助保证你的代码观察到所有异常。

- 运行时将引发[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)当你调用[concurrency::task::get](reference/task-class.md#get)和该任务将被取消。

- 在运行时不会管理轻量级任务和代理的异常。

##  <a name="top"></a> 本文档中

- [任务和延续](#tasks)

- [任务组和并行算法](#task_groups)

- [由运行时引发的异常](#runtime)

- [多个异常](#multiple)

- [取消](#cancellation)

- [轻量级任务](#lwts)

- [异步代理](#agents)

##  <a name="tasks"></a> 任务和延续

本部分介绍如何在运行时处理引发的异常[concurrency:: task](../../parallel/concrt/reference/task-class.md)对象和它们的延续。 有关任务和延续模型的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

当引发传递给工作函数体中出现的异常`task`对象，则运行时存储该异常并将其封送到调用上下文[concurrency::task::get](reference/task-class.md#get)或[并发::task:: wait](reference/task-class.md#wait)。 文档[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)描述基于任务的基于值的继续符，但若要汇总，与基于值的延续采用的类型参数`T`和基于任务的延续采用的类型参数`task<T>`. 如果任务引发了一个或多个基于值延续，将不会安排这些延续运行。 下面的示例阐释了这种行为：

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

基于任务的延续使你能够处理由前面的任务引发的任何异常。 基于任务的延续始终运行;是否已成功完成，该任务引发了异常，或已取消，并不重要。 当某个任务引发异常时，其基于任务的延续计划运行。 下面的示例演示始终引发的任务。 该任务有两个继续符;一个是基于值的和另一个是基于任务的。 基于任务的异常始终运行，并因此可以捕获由前面的任务引发的异常。 因为任务异常时始终引发示例等待完成这两个继续符时, 再次引发异常`task::get`或`task::wait`调用。

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

我们建议使用基于任务的延续来捕获可以处理的异常。 由于基于任务的延续始终运行，因此请考虑是否在延续任务链的末尾添加基于任务的延续。 这可以帮助保证你的代码观察到所有异常。 下面的示例演示一个基本的基于值的延续链。 链中的第三个任务引发，并因此后面它的任何基于值的延续将不会运行。 但是，最终延续任务，是基于任务的并因此始终运行。 此最终延续处理由第三个任务引发的异常。

我们建议您捕获的最特定异常，则可以。 如果没有捕获特定异常，则可以省略此最终的基于任务的延续。 任何异常保持未处理，可以终止该应用程序。

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
>  可以使用[concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md)方法以将异常与任务完成事件相关联。 文档[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)介绍[concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)中更详细地介绍的类。

[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)是与重要的运行时异常类型`task`。 运行时将引发`task_canceled`当您调用`task::get`和该任务将被取消。 (也可反过来`task::wait`将返回[task_status:: canceled](reference/concurrency-namespace-enums.md#task_group_status) ，而不会引发。)您可以捕获和处理此异常从基于任务的延续，或在调用时`task::get`。 有关任务取消的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)。

> [!CAUTION]
>  切勿从代码中引发 `task_canceled`。 调用[concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)相反。

如果任务引发了异常和任务，其延续或主应用程序之一不捕获异常，运行时终止应用程序。 如果你的应用程序崩溃，则可以配置 Visual Studio 时中断C++引发异常。 诊断的未经处理的异常位置后，使用基于任务的延续来处理它。

部分[由运行时引发的异常](#runtime)本文档中介绍了如何使用中更详细地介绍运行时异常。

[[返回页首](#top)]

##  <a name="task_groups"></a> 任务组和并行算法

本部分介绍如何在运行时处理由任务组引发的异常。 本部分还适用于并行算法等[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)，因为这些算法基于任务组生成。

> [!CAUTION]
>  请确保了解异常都有依赖任务的影响。 有关如何使用异常处理的任务或并行算法的建议做法，请参阅[了解如何取消和异常处理会影响对象析构](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)部分中并行的最佳实践模式库主题。

有关任务组的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 有关并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

当引发传递给工作函数体中出现的异常[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象，则运行时存储该异常并将其封送到调用上下文[task_group](reference/task-group-class.md#wait)， [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)， [run_and_wait](reference/task-group-class.md#run_and_wait)，或[concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait)。 运行时也会停止任务组 （包括那些子任务组中） 中的所有活动任务，并放弃任何尚未启动的任务。

下面的示例演示引发异常的工作函数的基本结构。 该示例使用`task_group`对象的两个值输出`point`并行中的对象。 `print_point`的工作函数将的值输出`point`到控制台的对象。 工作函数引发异常，如果输入的值为`NULL`。 运行时将存储此异常，并将其封送到调用上下文`task_group::wait`。

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

本示例生成以下输出。

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

有关使用任务组中的异常处理的完整示例，请参阅[如何：使用异常处理来中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

[[返回页首](#top)]

##  <a name="runtime"></a> 由运行时引发的异常

异常可能会导致运行时调用。 大多数异常类型，除了[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)并[concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md)，指示编程错误。 这些错误通常无法恢复，并因此不应捕获或由应用程序代码处理。 我们建议你仅捕获或时诊断的编程错误所需的应用程序代码处理不可恢复的错误。 但是，了解运行时定义的异常类型可以帮助您诊断的编程错误。

异常处理机制是相同的运行时作为工作函数引发的异常引发的异常。 例如， [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数，则会引发`operation_timed_out`时未指定的时间段内收到一条消息。 如果`receive`传递给任务组，则运行时存储该异常并将其封送到调用上下文中工作函数引发异常`task_group::wait`， `structured_task_group::wait`， `task_group::run_and_wait`，或`structured_task_group::run_and_wait`。

下面的示例使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法在并行运行两个任务。 第一个任务等待五秒钟，然后将消息发送到消息缓冲区。 第二个任务使用`receive`函数等待三秒钟，以接收来自相同的消息缓冲区的消息。 `receive`函数，则会引发`operation_timed_out`如果时间段内未收到消息。

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

本示例生成以下输出。

```Output
The operation timed out.
```

若要阻止的应用程序异常终止，请确保你的代码处理异常，当它在运行时调用。 在调用外部代码，例如，使用并发运行时，到第三方库时，还处理的异常。

[[返回页首](#top)]

##  <a name="multiple"></a> 多个异常

如果任务或并行算法收到多个异常，运行时将封送到调用上下文那些异常之一。 在运行时不保证它封送处理的异常。

下面的示例使用`parallel_for`算法将数字打印到控制台。 如果输入的值小于一些最小值或大于某个最大值，它会引发异常。 在此示例中，多个工作函数可以引发异常。

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

下面显示了此示例中的示例输出。

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[返回页首](#top)]

##  <a name="cancellation"></a> 取消

并非所有异常都表示错误。 例如，搜索算法可能使用异常处理来找到结果时停止其关联的任务。 有关如何在代码中使用取消机制的详细信息，请参阅[PPL 中的取消](../../parallel/concrt/cancellation-in-the-ppl.md)。

[[返回页首](#top)]

##  <a name="lwts"></a> 轻量级任务

轻量级任务是直接从计划的任务[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)对象。 轻量级任务所需更少的开销比普通任务。 但是，在运行时不会捕获由轻量级任务引发的异常。 相反，异常是捕获了未经处理的异常处理程序，它默认情况下终止进程。 因此，在应用程序中使用适当的错误处理机制。 轻量级任务有关的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[返回页首](#top)]

##  <a name="agents"></a> 异步代理

轻量级任务，如运行时不管理异步代理引发的异常。

下面的示例演示一种方法在派生类中处理异常[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 此示例定义`points_agent`类。 `points_agent::run`方法读取`point`消息缓冲区中的对象并将其打印到控制台。 `run`方法将引发异常，如果它收到`NULL`指针。

`run`方法会将中的所有工作`try` - `catch`块。 `catch`块的消息缓冲区中存储该异常。 应用程序将检查代理是否在代理完成之后在通过读取此缓冲区中遇到了错误。

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

本示例生成以下输出。

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

因为`try` - `catch`块之外`while`循环，该代理将结束处理时遇到的第一个错误。 如果`try` - `catch`块内已`while`循环中，代理将继续出现错误后。

此示例将异常存储在消息缓冲区中，以便在运行，另一个组件可以监视错误的代理。 此示例使用[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)对象来存储错误。 在这种情况，代理将处理多个异常`single_assignment`类存储仅第一条消息传递到它。 若要存储仅最后一个异常，请使用[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)类。 若要存储的所有异常，请使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)类。 有关这些消息块的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

有关异步代理的详细信息，请参阅[异步代理](../../parallel/concrt/asynchronous-agents.md)。

[[返回页首](#top)]

##  <a name="summary"></a> 摘要

[[返回页首](#top)]

## <a name="see-also"></a>请参阅

[并发运行时](../../parallel/concrt/concurrency-runtime.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)
