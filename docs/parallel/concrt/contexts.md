---
title: 上下文
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 7df75ae7c1ac2b1d8c0b73ff1f1e3f2800d559b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194870"
---
# <a name="contexts"></a>上下文

本文档介绍并发运行时中上下文的角色。 附加到计划程序的线程称为 "*执行上下文*" 或 "只是*上下文*"。 [Concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函数和 concurrency：：[Context 类](../../parallel/concrt/reference/context-class.md)使你能够控制上下文的行为。 使用 `wait` 函数挂起指定时间的当前上下文。 `Context`当你需要更好地控制上下文何时阻止、取消阻止和生成，或者当你想要在当前上下文中进行订阅时，可使用类。

> [!TIP]
> 并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序有助于微调应用程序的性能，因此，如果你不熟悉并发运行时，则建议你从[并行模式库（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)开始。

## <a name="the-wait-function"></a>Wait 函数

[Concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函数在指定的毫秒数内以协作方式生成当前上下文的执行。 运行时使用生成时间来执行其他任务。 经过指定的时间后，运行时会重新安排执行上下文。 因此，该 `wait` 函数可能会挂起当前上下文，而不是为参数提供的值 `milliseconds` 。

如果为参数传递0（零）， `milliseconds` 将导致运行时挂起当前上下文，直至所有其他活动上下文都有机会执行工作。 这使您可以向所有其他活动任务生成任务。

### <a name="example"></a>示例

有关使用 `wait` 函数生成当前上下文，从而允许其他上下文运行的示例，请参阅[如何：使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

## <a name="the-context-class"></a>Context 类

Concurrency：：[Context 类](../../parallel/concrt/reference/context-class.md)为执行上下文提供编程抽象，并提供两个重要功能：能够以协作方式阻止、取消阻止和生成当前上下文，以及在当前上下文中超额订阅。

### <a name="cooperative-blocking"></a>协作阻止

`Context`类可让你阻止或生成当前的执行上下文。 当当前上下文无法继续，因为资源不可用时，阻止或生成很有用。

[Concurrency：： Context：： Block](reference/context-class.md#block)方法阻止当前上下文。 被阻止的上下文将生成其处理资源，以便运行时可以执行其他任务。 [Concurrency：： Context：：解除阻止方法取消](reference/context-class.md#unblock)阻止已阻止的上下文。 此 `Context::Unblock` 方法必须与调用的上下文不同 `Context::Block` 。 如果上下文尝试取消阻止自身，则运行时将引发[concurrency：： context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) 。

若要以协作方式阻止和取消阻止上下文，通常调用[concurrency：： context：： CurrentContext](reference/context-class.md#currentcontext)来检索指向 `Context` 与当前线程关联的对象的指针并保存结果。 然后调用 `Context::Block` 方法来阻止当前上下文。 稍后， `Context::Unblock` 从单独的上下文调用以取消阻止已阻止的上下文。

必须将对和的每对调用 `Context::Block` 匹配 `Context::Unblock` 。 当连续调用或方法时，运行时将引发[concurrency：： context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) ， `Context::Block` `Context::Unblock` 而不会对另一方法进行匹配调用。 但是，在调用之前无需调用 `Context::Block` `Context::Unblock` 。 例如，如果一个上下文 `Context::Unblock` 在另一个上下文调用同一上下文之前调用，则该上下文将 `Context::Block` 保持取消阻止。

[Concurrency：： Context：： Yield](reference/context-class.md#yield)方法会生成执行，以便运行时可以执行其他任务，然后重新计划执行上下文。 调用 `Context::Block` 方法时，运行时不会重新计划上下文。

#### <a name="example"></a>示例

有关使用 `Context::Block` 、 `Context::Unblock` 和 `Context::Yield` 方法实现协作信号量类的示例，请参阅[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

##### <a name="oversubscription"></a>过度订阅

默认计划程序将创建与可用硬件线程相同的线程数。 您可以使用*过度订阅*为给定的硬件线程创建其他线程。

对于计算密集型操作，过度订阅通常不会扩展，因为它带来了额外的开销。 但是，对于具有大量延迟的任务（例如，从磁盘或从网络连接读取数据），过度订阅可以提高某些应用程序的总体效率。

> [!NOTE]
> 仅从由并发运行时创建的线程中启用过度订阅。 如果从运行时不是由运行时创建的线程（包括主线程）中调用，则过度订阅不起作用。

若要在当前上下文中启用过度订阅，请调用[concurrency：： context：：超额](reference/context-class.md#oversubscribe)工作方法，并将 `_BeginOversubscription` 参数设置为 **`true`** 。 如果在并发运行时创建的线程上启用过度订阅，则会导致运行时创建一个额外的线程。 完成需要过度订阅的所有任务后，请 `Context::Oversubscribe` 在 `_BeginOversubscription` 参数设置为的情况下调用 **`false`** 。

您可以通过当前上下文多次启用过度订阅，但您必须将其禁用多次。 过度订阅还可以嵌套;也就是说，使用过度订阅的其他任务创建的任务也可能会过度订阅其上下文。 但是，如果嵌套任务及其父任务都属于相同的上下文，则仅对的最外面调用 `Context::Oversubscribe` 会导致创建其他线程。

> [!NOTE]
> 如果在启用过度订阅之前禁用了过度订阅，则运行时将引发[concurrency：： invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) 。

###### <a name="example"></a>示例

例如，如果使用过度订阅来抵消通过从网络连接读取数据而导致的延迟，请参阅[如何：使用过度订阅抵消延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

## <a name="see-also"></a>另请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[如何：使用过度订阅抵消延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
