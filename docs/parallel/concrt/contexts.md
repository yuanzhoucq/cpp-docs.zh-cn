---
title: "上下文 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "上下文 [并发运行时]"
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 上下文
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍并发运行时中的上下文中的角色。 附加到计划程序线程被称为 *执行上下文*, ，或只是 *上下文*。  [Concurrency:: wait](../Topic/wait%20Function.md) 函数和并发::[上下文类](../../parallel/concrt/reference/context-class.md) 使您可以控制上下文的行为。 使用 `wait` 函数以挂起指定的时间的当前上下文。 使用 `Context` 类时需要更好地控制上下文时阻止、 取消阻止，和生成，或如果想要过度订阅当前上下文。  
  
> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序可帮助您优化您的应用程序的性能，我们建议您从开始 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md) 如果您不熟悉并发运行时。  
  
## <a name="the-wait-function"></a>Wait 函数  
  [Concurrency:: wait](../Topic/wait%20Function.md) 函数以协作方式将产生当前上下文让出指定毫秒数的执行。 运行时使用让出时间执行其他任务。 指定的时间已过之后，运行时重新安排执行上下文。 因此， `wait` 函数可能会挂起当前上下文为提供的值超过 `milliseconds` 参数。  
  
 为传递 0 （零） `milliseconds` 参数会导致运行时挂起当前上下文，直到所有其他活动上下文提供了机会来执行工作。 这样可以生成任务的所有活动任务。  
  
### <a name="example"></a>示例  
 有关使用示例， `wait` 函数让出当前上下文，因此允许获得其他上下文中运行，请参阅 [如何︰ 使用计划组影响执行顺序为](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)。  
  
## <a name="the-context-class"></a>Context 类  
 并发::[上下文类](../../parallel/concrt/reference/context-class.md) 提供编程抽象为执行上下文，并提供两个重要功能︰ 以协作方式阻止、 取消阻止，和让出当前上下文的能力以及过度订阅当前上下文的能力。  
  
### <a name="cooperative-blocking"></a>协作阻止  
  `Context` 类，可以阻止或退出当前执行上下文。 当前上下文无法继续，因为资源不可用时，阻止或退出功能非常有用。  
  
  [Concurrency::Context::Block](../Topic/Context::Block%20Method.md) 方法将一直阻塞当前上下文。 被阻止上下文让出其处理资源，以便运行时可以执行其他任务。  [Concurrency::Context::Unblock](../Topic/Context::Unblock%20Method.md) 方法可取消阻止的上下文。  `Context::Unblock` 方法必须比调用不同的上下文从调用 `Context::Block`。 运行时会引发 [concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) 如果上下文尝试取消阻止自身。  
  
 若要以协作方式阻止和取消阻止上下文，通常调用 [concurrency::Context::CurrentContext](../Topic/Context::CurrentContext%20Method.md) 来检索一个指向 `Context` 与当前线程并保存结果相关联的对象。 然后，可以调用 `Context::Block` 方法阻止当前上下文。 稍后，调用 `Context::Unblock` 从单独的上下文，若要取消阻止被阻止的上下文。  
  
 必须匹配调用每个对 `Context::Block` 和 `Context::Unblock`。 运行时会引发 [concurrency:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) 时 `Context::Block` 或 `Context::Unblock` 而无需与另一种方法的匹配调用连续调用方法。 但是，不需要调用 `Context::Block` 之前调用 `Context::Unblock`。 例如，如果一个上下文调用 `Context::Unblock` 之前另一个上下文调用 `Context::Block` 为相同的上下文，该上下文保持未阻止状态。  
  
  [Concurrency::Context::Yield](../Topic/Context::Yield%20Method.md) 方法可让出执行，以便运行时可以执行其他任务，然后重新计划执行上下文。 当您调用 `Context::Block` 方法时，运行时不重新计划上下文。  
  
#### <a name="example"></a>示例  
 有关使用示例， `Context::Block`, ，`Context::Unblock`, ，和 `Context::Yield` 方法来实现协作信号量类，请参阅 [如何︰ 使用 Context 类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。  
  
##### <a name="oversubscription"></a>过度订阅  
 默认计划程序创建相同的线程数，因为没有可用硬件线程。 您可以使用 *过度订阅* 若要为给定的硬件线程创建附加线程。  
  
 对于计算密集型操作，过度订阅通常不会进行扩展，因为这样做会产生额外的开销。 但是，对于具有很长的延迟的任务，例如，从磁盘或网络连接、 读取数据过度订阅可以提高某些应用程序的整体效率。  
  
> [!NOTE]
>  仅从由并发运行时创建的线程中启用过度订阅。 从不由运行库 （包括主线程） 创建的线程中调用时，过度订阅无效。  
  
 若要启用过度订阅当前上下文中的，调用 [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) 方法 `_BeginOversubscription` 参数设置为 `true`。 当启用过度订阅由并发运行时创建的线程上时，则会导致运行时创建一个附加线程。 在需要过度订阅完成的所有任务之后, 调用 `Context::Oversubscribe` 与 `_BeginOversubscription` 参数设置为 `false`。  
  
 您可以启用过度订阅多次从当前上下文，但您必须将其禁用，使其同样次数。 此外可以嵌套过度订阅;即，由另一个使用过度订阅的任务创建的任务可以过度订阅其上下文。 但是，如果嵌套的任务和其父级属于相同的上下文中，只有最外层到调用 `Context::Oversubscribe` 将导致其他线程的创建。  
  
> [!NOTE]
>  运行时会引发 [concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) 如果过度订阅处于禁用状态，然后才能启用它。  
  
###### <a name="example"></a>示例  
 使用过度订阅抵消延迟所致通过网络连接读取数据的示例，请参阅 [如何︰ 使用过度订阅到偏移量延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何︰ 使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)   
 [如何︰ 使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [如何︰ 使用过度订阅抵消延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

