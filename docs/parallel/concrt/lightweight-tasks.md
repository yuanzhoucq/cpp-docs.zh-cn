---
title: 轻量级任务
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 7b798312c9660e51338d51a97a052ad4e5bdca6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512177"
---
# <a name="lightweight-tasks"></a>轻量级任务

本文档介绍并发运行时中轻量级任务的角色。 *轻型任务*是直接从`concurrency::Scheduler`或`concurrency::ScheduleGroup`对象计划的任务。 轻量级任务类似于你向 Windows API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数提供的功能。 因此, 当您改编现有代码以使用并发运行时的计划功能时, 轻量级任务非常有用。 并发运行时本身使用轻量级任务来计划异步代理并在异步消息块之间发送消息。

> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序有助于微调应用程序的性能, 因此, 如果你不熟悉并发运行时, 则建议你从[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)开始。

轻量级任务比异步代理和任务组的开销更少。 例如, 运行时不会在轻量级任务完成时通知您。 此外, 运行时不捕获或处理从轻量级任务引发的异常。 有关异常处理和轻量级任务的详细信息, 请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

对于大多数任务, 建议使用更强大的功能, 例如任务组和并行算法, 因为这样可以更轻松地将复杂任务分解为更基本的任务。 有关任务组的详细信息, 请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 有关并行算法的详细信息, 请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

若要创建轻量级任务, 请调用[concurrency:: ScheduleGroup:: ScheduleTask](reference/schedulegroup-class.md#scheduletask)、 [Concurrency:: CurrentScheduler:: ScheduleTask](reference/currentscheduler-class.md#scheduletask)或[concurrency:: 计划程序:: ScheduleTask](reference/scheduler-class.md#scheduletask)方法。 若要等待轻量级任务完成, 请等待父计划程序关闭, 或使用同步机制 (如[concurrency:: event](../../parallel/concrt/reference/event-class.md)对象)。

## <a name="example"></a>示例

有关演示如何改编现有代码以使用轻量级任务的示例, 请参阅[演练:改编现有代码以使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)。

## <a name="see-also"></a>请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[演练：调整现有代码以使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
