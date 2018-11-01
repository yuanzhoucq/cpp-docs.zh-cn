---
title: 上下文
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: b7d1a5bbc63781e865be8053cb4365d6a8590935
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529163"
---
# <a name="contexts"></a>上下文

本文档介绍并发运行时中的上下文的角色。 附加到计划程序线程被称为*执行上下文*，或仅*上下文*。 [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数和并发::[上下文类](../../parallel/concrt/reference/context-class.md)，您可以控制上下文的行为。 使用`wait`函数在当前上下文暂停指定的时间。 使用`Context`类时您需要对上下文何时阻止、 取消阻止，和产生，或当你想要过度订阅当前上下文的更多控制。

> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 因为任务计划程序可帮助您优化您的应用程序的性能，我们建议您开始[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)你是否新并发运行时。

## <a name="the-wait-function"></a>等待函数

[Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数以协作方式将产生在指定的毫秒数的当前上下文的执行。 在运行时使用 yield 时间来执行其他任务。 在指定的时间已过之后，运行时重新安排执行的上下文。 因此，`wait`函数可能会挂起超过为提供的值在当前上下文`milliseconds`参数。

为传递 0 （零）`milliseconds`参数会导致运行时挂起当前上下文，直到为所有其他活动上下文提供机会来执行工作。 这样可以生成任务与其他所有活动任务。

### <a name="example"></a>示例

有关使用示例`wait`函数将让出当前上下文，因此允许获得其他上下文中运行，请参阅[如何： 使用计划组影响执行顺序为](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。

## <a name="the-context-class"></a>上下文类

并发::[上下文类](../../parallel/concrt/reference/context-class.md)提供编程抽象的执行上下文，并提供了两个重要功能： 能够以协作方式阻止、 取消阻止，和让出当前上下文，以及到功能过度订阅当前上下文。

### <a name="cooperative-blocking"></a>协作阻止

`Context`类，可以阻止或退出当前执行上下文。 当前上下文无法继续，因为资源不可用时，阻止或退出功能非常有用。

[Concurrency::Context::Block](reference/context-class.md#block)方法阻止当前上下文。 被阻止的上下文生成其处理资源，以便在运行时可以执行其他任务。 [Concurrency::Context::Unblock](reference/context-class.md#unblock)方法取消阻止已阻止的上下文。 `Context::Unblock`必须从比的名为不同的上下文中调用方法`Context::Block`。 运行时将引发[concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md)如果上下文尝试取消阻止自身。

若要以协作方式阻止和取消阻止上下文，通常调用[concurrency::Context::CurrentContext](reference/context-class.md#currentcontext)来检索一个指向`Context`关联与当前线程并保存结果对象。 然后，调用`Context::Block`方法阻止当前上下文。 更高版本，调用`Context::Unblock`从单独的上下文，若要取消阻止已阻止的上下文。

必须匹配的调用的每个对`Context::Block`和`Context::Unblock`。 运行时将引发[concurrency:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md)时`Context::Block`或`Context::Unblock`到另一种方法的匹配调用连续调用方法。 但是，不需要调用`Context::Block`之前调用`Context::Unblock`。 例如，如果一个上下文调用`Context::Unblock`之前另一个上下文调用`Context::Block`相同的上下文中，该上下文保持未阻止状态。

[Concurrency::Context::Yield](reference/context-class.md#yield)方法可让出执行，以便在运行时可以执行其他任务，然后重新计划执行的上下文。 当您调用`Context::Block`方法时，运行时不重新计划上下文。

#### <a name="example"></a>示例

有关使用示例`Context::Block`， `Context::Unblock`，并`Context::Yield`方法来实现协作信号量类，请参阅[如何： 使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

##### <a name="oversubscription"></a>过度订阅

默认计划程序创建相同数量的线程，因为没有可用的硬件线程。 可以使用*过度订阅*来创建给定的硬件线程的其他线程。

对于计算密集型操作，过度订阅通常不会进行扩展，因为它引入了额外的开销。 但是，对于具有大量的延迟的任务，例如，从磁盘或网络连接、 读取数据过度订阅可以提高某些应用程序的整体效率。

> [!NOTE]
>  仅从由并发运行时创建的线程中启用过度订阅。 不由运行时 （包括主线程） 创建的线程调用时，则过度订阅无效。

若要启用过度订阅当前上下文中的，调用[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法替换`_BeginOversubscription`参数设置为**true**。 如果启用过度订阅由并发运行时创建的线程上，这会导致运行时创建一个其他线程。 在所有需要过度订阅完成的任务之后, 调用`Context::Oversubscribe`与`_BeginOversubscription`参数设置为**false**。

您可以启用过度订阅多个时间从当前上下文中，但必须启用它同样次数禁用它。 此外可以嵌套过度订阅;它是由另一个使用过度订阅的任务创建的任务可以过度订阅其上下文。 但是，如果嵌套的任务和其父级属于相同的上下文中，只有最外层到调用`Context::Oversubscribe`将导致其他线程的创建。

> [!NOTE]
>  运行时将引发[concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md)如果它启用之前禁用过度订阅。

###### <a name="example"></a>示例

使用过度订阅偏移延迟引起通过网络连接读取数据的示例，请参阅[如何： 使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

## <a name="see-also"></a>请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[如何：使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

