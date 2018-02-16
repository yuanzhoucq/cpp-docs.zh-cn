---
title: "并发运行时 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d7822c552345f9492dcca6822a133290c2a82be
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="concurrency-runtime"></a>并发运行时
适用于 C++ 的并发运行时可帮助你编写可靠、可伸缩且响应迅速的并行应用程序。 它提升了抽象级别，因此无需管理与并发相关的基础结构详细信息。 你还可以使用它来指定符合应用程序服务要求质量的计划策略。 使用这些资源帮助你开始使用并发运行时。  
  
 参考文档，请参阅[引用](../../parallel/concrt/reference/reference-concurrency-runtime.md)。  
  
> [!TIP]
>  并发运行时十分依赖 C++11 功能，并采用更现代的 C++ 样式。 要了解详细信息，请阅读[欢迎回到 c + +](../../cpp/welcome-back-to-cpp-modern-cpp.md)。  
  
## <a name="choosing-concurrency-runtime-features"></a>选择并发运行时功能  
  
|||  
|-|-|  
|[概述](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|讲解并发运行时之所以重要的原因并介绍它的主要功能。|  
|[与其他并发模型进行比较](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|演示并发运行时如何与其他并发模型（例如 Windows 线程池和 OpenMP）进行比较，以便你能够使用最适合你应用程序需求的并发模型。|  
|[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|将 OpenMP 与并发运行时进行比较，并提供有关如何迁移现有 OpenMP 代码以使用并发运行时的示例。|  
|[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|向你介绍 PPL，它提供并行循环、任务和并行容器。|  
|[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)|向你介绍如何使用异步代理和消息传递来轻松地将数据流和流水线操作任务合并到应用程序中。|  
|[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|向你介绍任务计划程序，它使你能够微调使用并发运行时的桌面应用的性能。|  
  
## <a name="task-parallelism-in-the-ppl"></a>PPL 中的任务并行度  
  
|||  
|-|-|  
|[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [如何：使用 parallel_invoke 来编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [如何：使用 parallel_invoke 来执行并行操作](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [如何：创建在延迟一段时间后完成的任务](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|介绍任务和任务组，它们可帮助你编写异步代码并将并行工作分解为较小的部分。|  
|[演练：实现 Future](../../parallel/concrt/walkthrough-implementing-futures.md)|演示如何组合使用并发运行时功能来完成更多任务。|  
|[演练：从用户界面线程中删除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|演示如何将由 MFC 应用程序中的 UI 线程执行的工作移到工作线程中。|  
|[并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|提供使用 PPL 的提示和最佳做法。|  
  
## <a name="data-parallelism-in-the-ppl"></a>PPL 中的数据并行度  
  
|||  
|-|-|  
|[并行算法](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [如何：编写 parallel_for 循环](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [如何：编写 parallel_for_each 循环](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [如何：并行执行映射和减少操作](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|介绍 `parallel_for`、 `parallel_for_each`、 `parallel_invoke`和其他并行算法。 使用并行算法来解决涉及数据集合的 *数据并行* 问题。|  
|[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [如何：使用并行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [如何：使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [如何：使用 combinable 来组合集](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|介绍 `combinable` 类，以及 `concurrent_vector`、 `concurrent_queue`、 `concurrent_unordered_map`和其他并行容器。 当你需要提供对其元素的线程安全访问的容器时，请使用并行容器和对象。|  
|[并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|提供使用 PPL 的提示和最佳做法。|  
  
## <a name="canceling-tasks-and-parallel-algorithms"></a>取消任务和并行算法  
  
|||  
|-|-|  
|[PPL 中的取消操作](cancellation-in-the-ppl.md)|介绍 PPL 中取消操作的角色，包括如何启动和相应取消请求。|  
|[如何：使用取消来中断并行循环](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [如何：使用异常处理来中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|演示取消数据并行工作的两种方法。|  
  
## <a name="universal-windows-platform-apps"></a>通用 Windows 平台应用  
  
|||  
|-|-|  
|[在为 UWP 应用的 c + + 中创建异步操作](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|介绍了一些使用并发运行时生成异步操作中的 UWP 应用时，需要注意的要点。|  
|[演练：使用任务和 XML HTTP 请求进行连接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|演示如何组合使用 PPL 任务和`IXMLHTTPRequest2`和`IXMLHTTPRequest2Callback`接口以将 HTTP GET 和 POST 请求发送到 web 服务中的 UWP 应用。|  
|[Windows 运行时应用示例](http://code.msdn.microsoft.com/windowsapps)|包含可下载代码示例和演示应用适用于 Windows 8.x。 C++ 示例使用 PPL 任务等并发运行时功能在后台处理数据，以保持 UX 随时响应。|  
  
## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>异步代理库中的数据流编程  
  
|||  
|-|-|  
|[异步代理](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [消息传递函数](../../parallel/concrt/message-passing-functions.md)<br /><br /> [如何：实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [如何：为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [如何：在已完成的任务之间选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [如何：定期发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)|介绍异步代理、消息块和消息传递函数，它们是在并发运行时中执行数据流操作的构建基块。|  
|[演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|演示如何创建基本的基于代理的应用程序。|  
|[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|演示如何创建执行图像处理的异步消息块网络。|  
|[演练：使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|通过哲学家就餐问题说明如何使用并发运行时来避免应用程序中发生死锁。|  
|[演练：创建自定义消息块](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|演示如何创建根据优先级对传入消息进行排序的自定义消息块类型。|  
|[异步代理库中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|提供使用代理的提示和最佳做法。|  
  
## <a name="exception-handling-and-debugging"></a>异常处理和调试  
  
|||  
|-|-|  
|[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|介绍如何处理并发运行时中的异常。|  
|[并行诊断工具](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|讲解如何微调应用程序以及最有效地利用并发运行时。|  
  
## <a name="tuning-performance"></a>调整性能  
  
|||  
|-|-|  
|[并行诊断工具](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|讲解如何微调应用程序以及最有效地利用并发运行时。|  
|[计划程序实例](../../parallel/concrt/scheduler-instances.md)<br /><br /> [如何：管理计划程序实例](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [计划程序策略](../../parallel/concrt/scheduler-policies.md)<br /><br /> [如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [如何：创建使用特定计划程序策略的代理](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|演示如何使用管理计划程序实例和计划程序策略。 对于桌面应用，计划程序策略使你能够将特定规则与特定工作负载类型关联。 例如，你可以创建一个计划程序实例来以提升的线程优先级运行一些任务，并使用默认计划程序以普通线程优先级运行其他任务。|  
|[计划组](../../parallel/concrt/schedule-groups.md)<br /><br /> [如何：使用计划组影响执行顺序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|演示如何使用计划组来关联相关任务或将它们组合到一起。 例如，当相关任务从在同一处理器节点上执行中获益时，你可能需要这些任务具有高度的局域性。|  
|[轻量级任务](../../parallel/concrt/lightweight-tasks.md)|说明轻量级任务如何有助于创建不需要负载平衡或取消的工作，以及它们如何有助于调整现有代码以便与并发运行时一起使用。|  
|[上下文](../../parallel/concrt/contexts.md)<br /><br /> [如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [如何：使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|介绍如何控制由并发运行时管理的线程的行为。|  
|[内存管理函数](../../parallel/concrt/memory-management-functions.md)<br /><br /> [如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|介绍并发运行时提供的内存管理函数，可帮助你以并发方式分配和释放内存。|  
  
## <a name="additional-resources"></a>其他资源  
  
|||  
|-|-|  
|[Hilo（使用 C++ 和 XAML 的 Windows 应用商店应用）中的异步编程模式和提示](http://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|了解我们如何使用并发运行时在 Hilo，使用 c + + 和 XAML 的 Windows 运行时应用程序中实现异步操作。|  
|[并发运行时和 Visual Studio 2010 中的并行模式库的代码示例](http://go.microsoft.com/fwlink/p/?linkid=183875)|提供演示并发运行时的示例应用程序和实用程序。|  
|[在本机代码的博客中的并行编程](http://go.microsoft.com/fwlink/p/?linkid=183873)|提供有关并发运行时中的并行编程的其他深度博客文章。|  
|[在 c + + 和本机代码论坛中的并行计算](http://go.microsoft.com/fwlink/p/?linkid=183874)|使你能够参与关于并发运行时的社区讨论。|  
|[并行编程](/dotnet/standard/parallel-programming/index)|讲解关于 [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)]中可用的并行编程模型的内容。|  
  
## <a name="see-also"></a>请参阅  
 [参考](../../parallel/concrt/reference/reference-concurrency-runtime.md)


