---
title: 并行模式库中的最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: 641d85b03fca13a6592610d87563e3e701ad3e3e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142090"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>并行模式库中的最佳做法

本文档介绍如何最佳有效地使用并行模式库 (PPL)。 PPL 提供通用的容器、对象和算法，用于执行细化并行。

有关 PPL 的详细信息，请参阅[并行模式库（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)。

## <a name="top"></a> 部分

本文档包含以下各节：

- [不要并行化小型循环主体](#small-loops)

- [最高可能级别的快速并行度](#highest)

- [使用 parallel_invoke 解决除法和治问题](#divide-and-conquer)

- [使用取消或异常处理来中断并行循环](#breaking-loops)

- [了解取消和异常处理如何影响对象析构](#object-destruction)

- [不要在并行循环中重复阻塞](#repeated-blocking)

- [取消并行工作时不要执行阻止操作](#blocking)

- [不要在并行循环中写入共享数据](#shared-writes)

- [如果可能，请避免错误共享](#false-sharing)

- [确保变量在任务的整个生存期内有效](#lifetime)

## <a name="small-loops"></a>不要并行化小型循环主体

相对较小的循环体并行化可能会导致相关的计划开销超过并行处理的获益。 考虑下面的示例，它可将每对元素添加到两个数组。

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

每个并行循环迭代的工作负荷太小，因而无法受益于并行处理的开销。 通过在循环体中执行更多的工作或通过按顺序执行循环，可以提高此循环的性能。

[[返回页首](#top)]

## <a name="highest"></a>最高可能级别的快速并行度

当只在较低级别并行化代码时，可引入 fork-join 构造，它不随处理器数量的增加而变化。 *分叉联接*构造是一种构造，其中一个任务将其工作划分为较小的并行子任务，并等待这些子任务完成。 每个子任务可以递归方式将其自身划分为其他子任务。

尽管 fork-join 模型可用于解决各种问题，但也存在同步开销会降低可伸缩性的情况。 例如，下面处理图像数据的串行代码。

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

由于每个循环迭代是独立的，因此可以并行化大部分工作，如下面的示例所示。 此示例使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法并行化外部循环。

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

下面的示例通过调用循环中的 `ProcessImage` 函数阐释 fork-join 构造。 每个对 `ProcessImage` 的调用直到每个子任务完成后才返回。

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

如果并行循环的每次迭代几乎不执行任何工作，或执行非平衡并行循环执行的工作（即一些循环迭代比另一些花费更长的时间），那么频繁进行分叉和联接工作所需的计划开销可能超过并行执行的带来的好处。 此开销会随着处理器数量增加而增加。

要减少此示例中计划开销的数量，可在并行内部循环前先并行外部循环，或使用其他并行构造，如流水线结构。 下面的示例将 `ProcessImages` 函数修改为使用[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法并行化外部循环。

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

有关使用管道并行执行图像处理的类似示例，请参阅[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[返回页首](#top)]

## <a name="divide-and-conquer"></a>使用 parallel_invoke 解决除法和治问题

*分割和治*问题是一种使用递归将任务分解为子任务的分叉联接构造形式。 除了[concurrency：： task_group](reference/task-group-class.md)和[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)类之外，你还可以使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法解决除法和治问题。 `parallel_invoke` 算法具有比任务组对象更简洁的语法，并当具有固定数目的并行任务时非常有用。

下面的示例演示使用 `parallel_invoke` 算法来实现双调排序算法。

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

为了降低开销，`parallel_invoke` 算法将在调用上下文时执行系列任务的最后一个。

有关此示例的完整版本，请参阅[如何：使用 Parallel_invoke 编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。 有关 `parallel_invoke` 算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

[[返回页首](#top)]

## <a name="breaking-loops"></a>使用取消或异常处理来中断并行循环

PPL 提供了两种方法来取消任务组或并行算法所执行的并行工作。 一种方法是使用[concurrency：： task_group](reference/task-group-class.md)和[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)类提供的取消机制。 另一种方法是在任务工作函数体中引发异常。 当取消并行工作树时，取消机制比异常处理更有效。 *并行工作树*是一组相关的任务组，其中某些任务组包含其他任务组。 取消机制以自上而下的方式取消任务组及其子任务组。 相反，异常处理以自下而上的方式工作，并且必须在异常向上传播时单独取消每个子任务组。

直接处理任务组对象时，使用[concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)或[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)方法取消属于该任务组的工作。 若要取消并行算法（如 `parallel_for`），创建父任务组并取消该任务组。 例如，可使用以下函数，`parallel_find_any`，它以并行方式搜索数组中的值。

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

由于并行算法使用任务组，当一个并行迭代取消父任务组时，整个任务将被取消。 有关此示例的完整版本，请参阅[如何：使用取消中断并行循环](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)。

尽管异常处理是一种比取消机制效率更低的取消并行工作的方法，但在某些情况中异常处理也非常适用。 例如，下面的方法，`for_all`，以递归方式在 `tree` 结构的每个节点上执行工作函数。 在此示例中，`_children` 数据成员是包含 `tree` 对象的[std：： list](../../standard-library/list-class.md) 。

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

如果不要求对树的每个元素调用工作函数，则 `tree::for_all` 方法的调用方可以引发异常。 下面的介绍了 `search_for_value` 函数，它可在所提供的 `tree` 对象中搜索值。 `search_for_value` 函数使用工作函数，可在树的当前元素匹配提供的值时引发异常。 `search_for_value` 函数使用 `try-catch` 块来捕获异常，并将结果打印到控制台。

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

有关此示例的完整版本，请参阅[如何：使用异常处理中断并行循环](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

有关 PPL 提供的取消和异常处理机制的更多常规信息，请参阅[ppl 中的取消](cancellation-in-the-ppl.md)操作和[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

[[返回页首](#top)]

## <a name="object-destruction"></a>了解取消和异常处理如何影响对象析构

在并行工作树中，取消的任务会阻止子任务运行。 如果一个子任务执行的操作对于应用程序很重要（如释放资源），则这可能会导致问题。 此外，任务取消可能导致异常通过对象析构函数进行传播，并在应用程序中导致不明确的行为。

在下面的示例中，`Resource` 类描述资源，`Container` 类描述保存资源的容器。 在其析构函数中，`Container` 类在它两个 `cleanup` 成员上并行调用 `Resource` 方法，然后在它第三个 `cleanup` 成员上调用 `Resource` 方法。

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

尽管这种模式在其自身上没有任何问题，但建议使用下面并行运行两个任务的代码。 第一个任务创建 `Container` 对象，第二个任务取消整个任务。 为了举例说明，该示例使用两个[concurrency：： event](../../parallel/concrt/reference/event-class.md)对象，以确保在创建 `Container` 对象之后取消操作，并确保 `Container` 对象在取消操作发生后被销毁。

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

该示例产生下面的输出：

```Output
Container 1: Freeing resources...Exiting program...
```

此代码示例包含的以下问题可能导致其与预期行为不同：

- 取消父任务会导致子任务（对[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)的调用也被取消。 因此，不会释放这两个资源。

- 父任务的取消将导致子任务引发内部异常。 由于 `Container` 析构函数不会处理此异常，因此异常会向上传播并且不会释放第三个资源。

- 子任务引发的异常通过 `Container` 析构函数进行传播。 从析构函数引发会将应用程序置于未定义的状态。

我们建议不在任务中执行关键操作（如释放资源），除非可以保证这些任务不会被取消。 我们还建议不使用可在类型的析构函数中引发的运行时功能。

[[返回页首](#top)]

## <a name="repeated-blocking"></a>不要在并行循环中重复阻塞

并行循环，如[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)或[并发性：](reference/concurrency-namespace-functions.md#parallel_for_each)由阻止操作所占据的:p arallel_for_each，这可能会导致运行时在一小段时间内创建多个线程。

当任务完成，或以协作方式停滞或让出时，并发运行时将执行其他工作。 当一个并行循环迭代停滞时，运行时可能会开始另一个迭代。 当不存在可用的空闲线程时，运行时将创建一个新线程。

当并行循环体偶尔停滞时，此机制可帮助最大化整体任务吞吐量。 但当多个迭代停滞时，运行时可能会创建多个线程来运行其他工作。 这可能导致内存不足的情况或较差的硬件资源使用情况。

请考虑以下示例，该示例在 `parallel_for` 循环的每次迭代中调用[concurrency：： send](reference/concurrency-namespace-functions.md#send)函数。 由于 `send` 以协作方式停滞，所以每次调用 `send` 时运行时都会创建一个新线程来运行其他工作。

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

我们建议你重构代码来避免这种模式。 在此示例中，可通过在串行 `send` 循环中调用 `for` 来避免其他线程的创建。

[[返回页首](#top)]

## <a name="blocking"></a>取消并行工作时不要执行阻止操作

如果可能，请在调用[concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)或[concurrency：： structured_task_group：：](reference/structured-task-group-class.md#cancel) cancel 方法来取消并行工作之前，不要执行阻止操作。

在任务执行协作停滞操作时，运行时可在第一个任务等待数据时执行其他工作。 当运行时取消停滞时，它将重新安排正在等待的任务。 通常运行时会先重新安排最近取消停滞的任务，然后再重新安排后来取消停滞的任务。 因此，运行时在停滞操作期间可能安排不必要的工作，这会导致性能下降。 相应地，如果在取消并行工作前执行停滞操作，则停滞操作会延迟对 `cancel` 的调用。 这将导致其他任务执行不必要的工作。

请看下面定义 `parallel_find_answer` 函数的示例，该函数搜索所提供的满足提供的谓词函数的数组的元素。 当谓词函数返回**true**时，并行工作函数将创建一个 `Answer` 对象并取消整个任务。

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

`new` 运算符可执行可能会停滞的堆分配。 仅当任务执行协作式阻塞调用（如调用[concurrency：： critical_section：： lock](reference/critical-section-class.md#lock)）时，运行时才执行其他操作。

下面的示例介绍如何防止不必要的工作，从而提高性能。 此示例在为 `Answer` 对象分配存储前先取消任务组。

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[返回页首](#top)]

## <a name="shared-writes"></a>不要在并行循环中写入共享数据

并发运行时提供了几个数据结构，例如[并发：： critical_section](../../parallel/concrt/reference/critical-section-class.md)，用于同步对共享数据的并发访问。 很多情况下这些数据结构非常有用，例如，当多个任务很少需要对资源的共享访问时。

请考虑以下示例，该示例使用[concurrency：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法，并使用 `critical_section` 对象计算[std：： array](../../standard-library/array-class-stl.md)对象中质数的计数。 此示例不会进行扩展，因为每个线程必须等待以访问共享的变量 `prime_sum`。

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

此示例也可能导致性能不佳，因为频繁的锁定操作有力地对循环进行了序列化。 此外，当并发运行时对象执行停滞操作时，计划程序可能会在第一个线程等待数据时创建其他线程来执行其他工作。 如果运行时因许多任务正等待共享数据而创建许多线程，那么应用程序可能不会很好地运行，或进入资源不足的状态。

PPL 定义[concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md)类，通过以无锁方式提供对共享资源的访问权限，有助于消除共享状态。 `combinable` 类提供了线程本地存储，该存储允许你执行细化的计算，然后将这些计算合并为最终的结果。 你可以将 `combinable` 对象当作 reduction 变量。

下面的示例使用 `combinable` 对象而不是 `critical_section` 对象来计算总和，从而修改前一个结果。 此示例可进行缩放，因为每个线程都会保存自己的总和本地副本。 此示例使用[concurrency：：可组合](reference/combinable-class.md#combine)方法将本地计算合并为最终结果。

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

有关此示例的完整版本，请参阅[如何：使用可组合来提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。 有关 `combinable` 类的详细信息，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

[[返回页首](#top)]

## <a name="false-sharing"></a>如果可能，请避免错误共享

如果在不同的处理器上运行的多个并发任务写入同一缓存行中的变量，则会发生*错误共享*。 当一个任务写入一个变量时，这两个变量的缓存行将会失效。 每当缓存行失效时，每个处理器必须重新加载缓存行。 因此，错误共享会导致应用程序中的性能降低。

以下基本示例介绍了两个并发任务，每个任务都增加了共享的计数器变量。

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

若要消除两个任务间的数据共享，可修改该示例以使用两个计数器变量。 任务完成后，此示例将计算最终的计数器值。 但此示例还说明了错误共享，因为变量 `count1` 和 `count2` 可能位于同一缓存行。

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

消除错误共享的一种方法是确保计数器变量位于不同的缓存行。 下面的示例将对齐 64 字节边界上的 `count1` 和 `count2` 变量。

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

此示例假定内存缓存的大小为 64 个或更少的字节。

如果必须在任务之间共享数据，建议使用[concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md)类。 `combinable` 类以不太可能发生错误共享的方式创建线程本地变量。 有关 `combinable` 类的详细信息，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

[[返回页首](#top)]

## <a name="lifetime"></a>确保变量在任务的整个生存期内有效

如果向任务组或并行算法提供 Lambda 表达式，capture 子句将指定 Lambda 表达式的主体是否通过值或引用访问封闭范围中的变量。 通过引用将变量传递到 Lambda 表达式时，必须保证该变量的生存期在任务完成之前一直保持。

请看下面的示例，该示例定义了 `object` 类和 `perform_action` 函数。 `perform_action` 函数创建 `object` 变量，并在该变量中以异步方式执行某项操作。 由于不能保证在 `perform_action` 函数返回前完成任务，因此，如果 `object` 变量在任务运行时被销毁，则程序将崩溃或发生未指定的行为。

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

具体取决于应用程序的要求，可使用以下方法之一来保证变量在每项任务的整个生存期保持有效。

下面的示例通过值将 `object` 变量传入任务。 因此，任务可在自己的变量副本上进行操作。

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

由于 `object` 变量通过值进行传递，因此，此变量发生的任何状态更改不会出现在原始副本。

下面的示例使用[concurrency：： task_group：： wait](reference/task-group-class.md#wait)方法确保任务在 `perform_action` 函数返回之前完成。

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

由于函数返回前任务现在完成了，因此，`perform_action` 函数不再以异步方式进行。

下面的示例修改 `perform_action` 函数以获取对 `object` 变量的引用。 调用方必须保证 `object` 变量的生存期在任务完成前是有效的。

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

也可使用指针来控制传入任务组或并行算法的对象的生存期。

有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)。

[[返回页首](#top)]

## <a name="see-also"></a>另请参阅

[并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[如何：使用 parallel_invoke 来编写并行排序例程](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[如何：使用取消来中断并行循环](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[如何：使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[异步代理库中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
