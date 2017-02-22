---
title: "并行模式库中的最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "并行模式库中，要避免的做法"
  - "要避免并行模式库的做法"
  - "最佳实践、 并行模式库"
  - "并行模式库中，最佳做法"
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# 并行模式库中的最佳做法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍如何最佳有效地使用并行模式库 (PPL)。 PPL 提供通用的容器、对象和算法，用于执行细化并行。  
  
 有关 PPL 的详细信息，请参阅 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)。  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 部分  
 本文档包含以下各节：  
  
- [未对小型循环主体进行并行化](#small-loops)  
  
- [表示并行度最高](#highest)  
  
- [使用 parallel_invoke 来求解分割和解决问题](#divide-and-conquer)  
  
- [使用取消或异常处理中断 Parallel 循环](#breaking-loops)  
  
- [了解如何取消和异常处理影响对象销毁](#object-destruction)  
  
- [不能在并行循环中反复阻止](#repeated-blocking)  
  
- [不要执行停滞操作时取消并行工作](#blocking)  
  
- [未写入到并行循环中的共享数据](#shared-writes)  
  
- [如果可能，避免错误共享](#false-sharing)  
  
- [请确保变量在任务的整个生存期内有效](#lifetime)  
  
##  <a name="a-namesmall-loopsa-do-not-parallelize-small-loop-bodies"></a><a name="small-loops"></a> 未对小型循环主体进行并行化  
 相对较小的循环体并行化可能会导致相关的计划开销超过并行处理的获益。 考虑下面的示例，它可将每对元素添加到两个数组。  
  
 [!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_1.cpp)]  
  
 每个并行循环迭代的工作负荷太小，因而无法受益于并行处理的开销。 通过在循环体中执行更多的工作或通过按顺序执行循环，可以提高此循环的性能。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namehighesta-express-parallelism-at-the-highest-possible-level"></a><a name="highest"></a> 表示并行度最高  
 当只在较低级别并行化代码时，可引入 fork-join 构造，它不随处理器数量的增加而变化。 一个 *派生-联结* 构造是一个构造，其中一个任务将其工作划分为较小的并行子任务并等待这些子任务完成。 每个子任务可以递归方式将其自身划分为其他子任务。  
  
 尽管 fork-join 模型可用于解决各种问题，但也存在同步开销会降低可伸缩性的情况。 例如，下面处理图像数据的串行代码。  
  
 [!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_2.cpp)]  
  
 由于每个循环迭代是独立的，因此可以并行化大部分工作，如下面的示例所示。 此示例使用 [concurrency:: parallel_for](../Topic/parallel_for%20Function.md) 算法并行化外部循环。  
  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_3.cpp)]  
  
 下面的示例通过调用循环中的 `ProcessImage` 函数阐释 fork-join 构造。 每个对 `ProcessImage` 的调用直到每个子任务完成后才返回。  
  
 [!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_4.cpp)]  
  
 如果并行循环的每次迭代几乎不执行任何工作，或执行非平衡并行循环执行的工作（即一些循环迭代比另一些花费更长的时间），那么频繁进行分叉和联接工作所需的计划开销可能超过并行执行的带来的好处。 此开销会随着处理器数量增加而增加。  
  
 要减少此示例中计划开销的数量，可在并行内部循环前先并行外部循环，或使用其他并行构造，如流水线结构。 下面的示例修改 `ProcessImages` 函数，以使用 [concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) 算法并行化外部循环。  
  
 [!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_5.cpp)]  
  
 有关使用管道中并行执行图像处理的类似示例，请参阅 [演练︰ 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namedivide-and-conquera-use-parallelinvoke-to-solve-divide-and-conquer-problems"></a><a name="divide-and-conquer"></a> 使用 parallel_invoke 来求解分割和解决问题  
 一个 *分割和解决* 问题是一种使用递归来将一个任务细分为多个子任务的派生-联结构造。 除了 [concurrency:: task_group](../Topic/task_group%20Class.md) 和 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 类，您还可以使用 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 算法解决分割和解决问题。 `parallel_invoke` 算法具有比任务组对象更简洁的语法，并当具有固定数目的并行任务时非常有用。  
  
 下面的示例演示使用 `parallel_invoke` 算法来实现双调排序算法。  
  
 [!CODE [concrt-parallel-bitonic-sort#12](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#12)]  
  
 为了降低开销，`parallel_invoke` 算法将在调用上下文时执行系列任务的最后一个。  
  
 此示例的完整版本，请参阅 [如何︰ 使用 parallel_invoke 来编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。 有关详细信息 `parallel_invoke` 算法，请参阅 [并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namebreaking-loopsa-use-cancellation-or-exception-handling-to-break-from-a-parallel-loop"></a><a name="breaking-loops"></a> 使用取消或异常处理中断 Parallel 循环  
 PPL 提供了两种方法来取消任务组或并行算法所执行的并行工作。 一种方法是使用提供的取消机制 [concurrency:: task_group](../Topic/task_group%20Class.md) 和 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 类。 另一种方法是在任务工作函数体中引发异常。 当取消并行工作树时，取消机制比异常处理更有效。 一个 *并行工作树* 是一组相关的任务组，其中一些任务组包含其他任务组。 取消机制以自上而下的方式取消任务组及其子任务组。 相反，异常处理以自下而上的方式工作，并且必须在异常向上传播时单独取消每个子任务组。  
  
 当您直接使用任务组对象，使用 [concurrency::task_group::cancel](../Topic/task_group::cancel%20Method.md) 或 [concurrency::structured_task_group::cancel](../Topic/structured_task_group::cancel%20Method.md) 方法取消属于该任务组的工作。 若要取消并行算法（如 `parallel_for`），创建父任务组并取消该任务组。 例如，可使用以下函数，`parallel_find_any`，它以并行方式搜索数组中的值。  
  
 [!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_6.cpp)]  
  
 由于并行算法使用任务组，当一个并行迭代取消父任务组时，整个任务将被取消。 此示例的完整版本，请参阅 [如何︰ 使用取消中断并行循环](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)。  
  
 尽管异常处理是一种比取消机制效率更低的取消并行工作的方法，但在某些情况中异常处理也非常适用。 例如，下面的方法，`for_all`，以递归方式在 `tree` 结构的每个节点上执行工作函数。 在此示例中， `_children` 数据成员是 [std::list](../../standard-library/list-class.md) ，其中包含 `tree` 对象。  
  
 [!CODE [concrt-task-tree-search#6](../CodeSnippet/VS_Snippets_ConcRT/concrt-task-tree-search#6)]  
  
 如果不要求对树的每个元素调用工作函数，则 `tree::for_all` 方法的调用方可以引发异常。 下面的介绍了 `search_for_value` 函数，它可在所提供的 `tree` 对象中搜索值。 `search_for_value` 函数使用工作函数，可在树的当前元素匹配提供的值时引发异常。 `search_for_value` 函数使用 `try-catch` 块来捕获异常，并将结果打印到控制台。  
  
 [!CODE [concrt-task-tree-search#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-task-tree-search#3)]  
  
 此示例的完整版本，请参阅 [如何︰ 使用异常处理中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。  
  
 有关取消和 PPL 提供的异常处理机制的详细信息，请参阅 [取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl) 和 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameobject-destructiona-understand-how-cancellation-and-exception-handling-affect-object-destruction"></a><a name="object-destruction"></a> 了解如何取消和异常处理影响对象销毁  
 在并行工作树中，取消的任务会阻止子任务运行。 如果一个子任务执行的操作对应用程序很重要（如释放资源），则这可能会导致问题。 此外，任务取消可能导致异常通过对象析构函数进行传播，并在应用程序中导致不明确的行为。  
  
 在下面的示例中，`Resource` 类描述资源，`Container` 类描述保存资源的容器。 在其析构函数中，`Container` 类在它两个 `Resource` 成员上并行调用 `cleanup` 方法，然后在它第三个 `Resource` 成员上调用 `cleanup` 方法。  
  
 [!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_7.h)]  
  
 尽管这种模式在其自身上没有任何问题，但建议使用下面并行运行两个任务的代码。 第一个任务创建 `Container` 对象，第二个任务取消整个任务。 为了便于演示，该示例使用两个 [concurrency:: event](../../parallel/concrt/reference/event-class.md) 对象来确保取消操作之后 `Container` 创建对象， `Container` 对象被销毁后执行取消操作。  
  
 [!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_8.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
Container 1: Freeing resources...Exiting program...  
```  
  
 此代码示例包含的以下问题可能导致其与预期行为不同：  
  
-   父任务的取消将导致子任务，对调用 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md), ，也会取消。 因此，不会释放这两个资源。  
  
-   父任务的取消将导致子任务引发内部异常。 由于 `Container` 析构函数不会处理此异常，因此异常会向上传播并且不会释放第三个资源。  
  
-   子任务引发的异常通过 `Container` 析构函数进行传播。 从析构函数引发会将应用程序置于未定义的状态。  
  
 我们建议不在任务中执行关键操作（如释放资源），除非可以保证这些任务不会被取消。 我们还建议不使用可在类型的析构函数中引发的运行时功能。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namerepeated-blockinga-do-not-block-repeatedly-in-a-parallel-loop"></a><a name="repeated-blocking"></a> 不能在并行循环中反复阻止  
 并行循环如 [concurrency:: parallel_for](../Topic/parallel_for%20Function.md) 或 [concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) 进行控制的阻止操作可能会导致运行时在很短时间内创建多个线程。  
  
 当任务完成，或以协作方式停滞或让出时，并发运行时将执行其他工作。 当一个并行循环迭代停滞时，运行时可能会开始另一个迭代。 当不存在可用的空闲线程时，运行时将创建一个新线程。  
  
 当并行循环体偶尔停滞时，此机制可帮助最大化整体任务吞吐量。 但当多个迭代停滞时，运行时可能会创建多个线程来运行其他工作。 这可能导致内存不足的情况或较差的硬件资源使用情况。  
  
 请考虑下面的示例中调用 [concurrency:: send](../Topic/send%20Function.md) 函数中的每个迭代 `parallel_for` 循环。 由于 `send` 以协作方式停滞，所以每次调用 `send` 时运行时都会创建一个新线程来运行其他工作。  
  
 [!CODE [concrt-repeated-blocking#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-repeated-blocking#1)]  
  
 我们建议你重构代码来避免这种模式。 在此示例中，可通过在串行 `for` 循环中调用 `send` 来避免其他线程的创建。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameblockinga-do-not-perform-blocking-operations-when-you-cancel-parallel-work"></a><a name="blocking"></a> 不要执行停滞操作时取消并行工作  
 如果可能，请不要执行停滞操作然后才能调用 [concurrency::task_group::cancel](../Topic/task_group::cancel%20Method.md) 或 [concurrency::structured_task_group::cancel](../Topic/structured_task_group::cancel%20Method.md) 方法来取消并行工作。  
  
 在任务执行协作停滞操作时，运行时可在第一个任务等待数据时执行其他工作。 当运行时取消停滞时，它将重新安排正在等待的任务。 通常运行时会先重新安排最近取消停滞的任务，然后再重新安排后来取消停滞的任务。 因此，运行时在停滞操作期间可能安排不必要的工作，这会导致性能下降。 相应地，如果在取消并行工作前执行停滞操作，则停滞操作会延迟对 `cancel` 的调用。 这将导致其他任务执行不必要的工作。  
  
 请看下面定义 `parallel_find_answer` 函数的示例，该函数搜索所提供的满足提供的谓词函数的数组的元素。 当谓词函数返回 `true` 时，并行工作函数将创建 `Answer` 对象并取消整个任务。  
  
 [!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_9.cpp)]  
  
 `new` 运算符可执行可能会停滞的堆分配。 运行时执行其他工作，仅在该任务执行协作停滞调用，例如，对调用 [concurrency::critical_section::lock](../Topic/critical_section::lock%20Method.md)。  
  
 下面的示例介绍如何防止不必要的工作，从而提高性能。 此示例在为 `Answer` 对象分配存储前先取消任务组。  
  
 [!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_10.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameshared-writesa-do-not-write-to-shared-data-in-a-parallel-loop"></a><a name="shared-writes"></a> 未写入到并行循环中的共享数据  
 并发运行时提供了几种数据结构，例如， [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), ，同步对共享数据的并发访问。 很多情况下这些数据结构非常有用，例如，当多个任务很少需要对资源的共享访问时。  
  
 请考虑下面的示例中使用 [concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) 算法和 `critical_section` 对象来计算中质数的计数 [std:: array](../../standard-library/array-class-stl.md) 对象。 此示例不会进行扩展，因为每个线程必须等待以访问共享的变量 `prime_sum`。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_11.cpp)]  
  
 此示例也可能导致性能不佳，因为频繁的锁定操作有力地对循环进行了序列化。 此外，当并发运行时对象执行停滞操作时，计划程序可能会在第一个线程等待数据时创建其他线程来执行其他工作。 如果运行时因许多任务正等待共享数据而创建许多线程，那么应用程序可能不会很好地运行，或进入资源不足的状态。  
  
 PPL 定义 [concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) 类，该类可帮助您取消共享的状态，通过以无锁方式提供对共享资源的访问。 `combinable` 类提供了线程本地存储，该存储允许你执行细化的计算，然后将这些计算合并为最终的结果。 你可以将 `combinable` 对象当作 reduction 变量。  
  
 下面的示例使用 `combinable` 对象而不是 `critical_section` 对象来计算总和，从而修改前一个结果。 此示例可进行缩放，因为每个线程都会保存自己的总和本地副本。 此示例使用 [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) 方法，以将本地计算合并为最终的结果。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_12.cpp)]  
  
 此示例的完整版本，请参阅 [如何︰ 使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。 有关详细信息 `combinable` 类，请参阅 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namefalse-sharinga-when-possible-avoid-false-sharing"></a><a name="false-sharing"></a> 如果可能，避免错误共享  
 *错误共享* 同一缓存行写入变量，它们位于单独的处理器运行的多个并发任务时发生。 当一个任务写入一个变量时，这两个变量的缓存行将会失效。 每当缓存行失效时，每个处理器必须重新加载缓存行。 因此，错误共享会导致应用程序中的性能降低。  
  
 以下基本示例介绍了两个并发任务，每个任务都增加了共享的计数器变量。  
  
 [!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_13.cpp)]  
  
 若要消除两个任务间的数据共享，可修改该示例以使用两个计数器变量。 任务完成后，此示例将计算最终的计数器值。 但此示例还说明了错误共享，因为变量 `count1` 和 `count2` 可能位于同一缓存行。  
  
 [!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_14.cpp)]  
  
 消除错误共享的一种方法是确保计数器变量位于不同的缓存行。 下面的示例将对齐 64 字节边界上的 `count1` 和 `count2` 变量。  
  
 [!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_15.cpp)]  
  
 此示例假定内存缓存的大小为 64 个或更少的字节。  
  
 我们建议你使用 [concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) 类时，则必须共享在任务之间的数据。 `combinable` 类以不太可能发生错误共享的方式创建线程本地变量。 有关详细信息 `combinable` 类，请参阅 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namelifetimea-make-sure-that-variables-are-valid-throughout-the-lifetime-of-a-task"></a><a name="lifetime"></a> 请确保变量在任务的整个生存期内有效  
 如果向任务组或并行算法提供 Lambda 表达式，capture 子句将指定 Lambda 表达式的主体是否通过值或引用访问封闭范围中的变量。 通过引用将变量传递到 lambda 表达式时，必须保证该变量的生存期在任务完成之前一直保持。  
  
 请看下面的示例，该示例定义了 `object` 类和 `perform_action` 函数。 `perform_action` 函数创建 `object` 变量，并在该变量中以异步方式执行某项操作。 由于不能保证在 `perform_action` 函数返回前完成任务，因此，如果 `object` 变量在任务运行时被销毁，则程序将崩溃或发生未指定的行为。  
  
 [!CODE [concrt-lambda-lifetime#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-lambda-lifetime#1)]  
  
 具体取决于应用程序的需求，可使用以下方法之一来保证变量在每项任务的整个生存期保持有效。  
  
 下面的示例通过值将 `object` 变量传入任务。 因此，任务可在自己的变量副本上进行操作。  
  
 [!CODE [concrt-lambda-lifetime#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-lambda-lifetime#2)]  
  
 由于 `object` 变量通过值进行传递，因此，此变量发生的任何状态更改不会出现在原始副本。  
  
 下面的示例使用 [concurrency::task_group::wait](../Topic/task_group::wait%20Method.md) 方法以确保在任务完成之前 `perform_action` 函数返回。  
  
 [!CODE [concrt-lambda-lifetime#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-lambda-lifetime#3)]  
  
 由于函数返回前任务现在完成了，因此，`perform_action` 函数不再以异步方式进行。  
  
 下面的示例修改 `perform_action` 函数以获取对 `object` 变量的引用。 调用方必须保证 `object` 变量的生存期在任务完成前是有效的。  
  
 [!CODE [concrt-lambda-lifetime#4](../CodeSnippet/VS_Snippets_ConcRT/concrt-lambda-lifetime#4)]  
  
 也可使用指针来控制传入任务组或并行算法的对象的生存期。  
  
 有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。  
  
 [[返回页首](#top)]  
  
## <a name="see-also"></a>另请参阅  
 [并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [演练︰ 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [如何︰ 使用 parallel_invoke 来编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)   
 [如何︰ 使用取消中断 Parallel 循环](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)   
 [如何︰ 使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)   
 [异步代理库中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)   
 [在并发运行时的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

