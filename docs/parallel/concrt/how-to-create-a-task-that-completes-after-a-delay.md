---
title: 如何：创建在延迟一段时间后完成的任务
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 76189f45eb486e06b040155f6697bf003659b474
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141742"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>如何：创建在延迟一段时间后完成的任务

此示例演示如何使用[concurrency：： task](../../parallel/concrt/reference/task-class.md)、 [concurrency：： cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)、 [concurrency：： cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)、 [concurrency：： task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)、 [concurrency：： timer](../../parallel/concrt/reference/timer-class.md)和[concurrency：： call](../../parallel/concrt/reference/call-class.md)类来创建一个在延迟后完成的任务。 你可使用此方法来生成偶尔轮询数据的循环，引入超时，将对用户输入的处理延迟预定的一段时间等。

## <a name="example"></a>示例

下面的示例显示 `complete_after` 和 `cancel_after_timeout` 函数。 `complete_after` 函数将创建在指定的延迟后完成的 `task` 对象。 它使用 `timer` 对象和 `call` 对象在指定延迟后设置 `task_completion_event` 对象。 通过使用 `task_completion_event` 类，您可以定义在一个线程或另一个任务发出有可用值的信号后完成的任务。 设置事件后，侦听器任务完成，它们的延续按计划运行。

> [!TIP]
> 有关 `timer` 和 `call` 类的详细信息，这些类是异步代理库的一部分，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

如果某任务在给定超时之前没有完成，则 `cancel_after_timeout` 函数基于 `complete_after` 函数构建以用于取消该任务。 `cancel_after_timeout` 函数将创建两个任务。 第一个任务指示成功且在提供的任务完成后完成；第二个任务指示失败且在指定的超时后完成。 `cancel_after_timeout` 函数将创建一个在成功或失败任务完成后运行的延续任务。 如果失败任务先完成，则延续将取消标记源，以便取消整个任务。

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>示例

下面的示例多次计算范围 [0, 100000] 内质数的计数。 如果在给定时间限制内没有完成，则操作失败。 `count_primes` 函数演示如何使用 `cancel_after_timeout` 函数。 它会对给定范围内的质数进行计数，而且如果任务未在提供的时间内完成，则会失败。 `wmain` 函数多次调用 `count_primes` 函数。 每次将时间限制减半。 当操作未在当前时间限制内完成后，程序结束。

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

当您使用此技术在延迟后取消任务时，任何尚未启动的任务在整个任务取消后都不会启动。 但是，及时响应取消对任何长时间运行的任务而言都非常重要。 有关任务取消的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

## <a name="example"></a>示例

以下是该示例的完整代码：

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>编译代码

若要编译代码，请复制代码并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `task-delay.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl/EHsc task-delay**

## <a name="see-also"></a>另请参阅

[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task 类（并发运行时）](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source 类](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token 类](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event 类](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer 类](../../parallel/concrt/reference/timer-class.md)<br/>
[call 类](../../parallel/concrt/reference/call-class.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)
