---
title: 并发运行时中的常规最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: 445e985117929cae2ec9a26a1e148b3eff55c2a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647689"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>并发运行时中的常规最佳做法

本文档介绍适用于并发运行时的多个领域的最佳做法。

##  <a name="top"></a> 部分

本文档包含以下各节：

- [使用协作同步构造在可能的情况](#synchronization)

- [避免耗时较长的任务不生成](#yield)

- [使用过度订阅偏移量的操作阻止或具有高延迟](#oversubscription)

- [使用并发内存管理函数在可能的情况](#memory)

- [使用 RAII 来管理并发对象的生存期](#raii)

- [不要在全局范围内创建并发对象](#global-scope)

- [不在共享的数据段中使用并发对象](#shared-data)

##  <a name="synchronization"></a> 使用协作同步构造在可能的情况

并发运行时提供了许多不需要外部同步对象的并发安全构造。 例如， [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类提供并发安全追加和元素访问操作。 但是，对于需要对资源的独占访问权限的情况下，运行时提供[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)， [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)，和[并发:: 事件](../../parallel/concrt/reference/event-class.md)类。 这些类型的行为以协作方式;因此，如第一个任务等待数据的任务计划程序可以重新分配到另一个上下文的处理资源。 如果可能，请使用这些同步类型而不是同步的其他机制，如所提供的 Windows API 中，不以协作方式工作。 有关这些同步类型和代码示例的详细信息，请参阅[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)并[比较同步数据结构与 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。

[[返回页首](#top)]

##  <a name="yield"></a> 避免耗时较长的任务不生成

由于任务计划程序的行为以协作方式，它不提供任务间的公平性。 因此，任务可以阻止其他任务启动。 虽然这是可以接受在某些情况下，在其他情况下这可能会导致死锁或资源不足。

以下示例执行更多任务的已分配的处理资源的数量。 第一个任务不会生成与任务计划程序，因此第二个任务不会在第一个任务完成之前不启动。

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

该示例产生下面的输出：

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

有几种方法实现两个任务之间的协作。 一种方法是偶尔会将控制权转交给一个长时间运行的任务中的任务计划程序。 下面的示例修改`task`函数来调用[concurrency::Context::Yield](reference/context-class.md#yield)方法来让任务计划程序，以便可以运行另一个任务。

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

该示例产生下面的输出：

```Output
1: 250000000
2: 250000000
1: 500000000
2: 500000000
1: 750000000
2: 750000000
1: 1000000000
2: 1000000000
```

`Context::Yield`方法生成仅另一个活动线程计划程序当前线程所属，轻量级任务或另一个操作系统线程上的。 此方法不会起作用的计划运行[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象，但尚未开始。

还有其他方法，以便在长时间运行的任务之间的协作正常进行。 您可以将大型任务细分为较小的子任务。 此外可以启用过度订阅期间耗时较长的任务。 可以通过过度订阅创建比可用硬件线程数更多的线程。 过度订阅耗时较长的任务包含大量的延迟，例如，从磁盘或网络连接读取数据时尤其有用。 有关轻型任务和过度订阅的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[返回页首](#top)]

##  <a name="oversubscription"></a> 使用过度订阅偏移量的操作阻止或具有高延迟

并发运行时提供同步基元，如[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)，以便任务能够以协作方式阻止和运行到对方。 当一个任务以协作方式阻止或生成时，任务计划程序可以重新分配到另一个上下文的处理资源，如第一个任务等待数据。

有些情况下，不能使用并发运行时提供的协作性阻止机制。 例如，您使用的外部库可能使用不同的同步机制。 另一个示例是在执行可能有大量的延迟，例如，当您使用 Windows API 的操作时`ReadFile`函数来从网络连接读取数据。 在这些情况下，过度订阅可以启用另一个任务处于空闲状态时要运行其他任务。 可以通过过度订阅创建比可用硬件线程数更多的线程。

请考虑以下函数， `download`，这将会下载给定 URL 处的文件。 此示例使用[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法临时增加活动线程数。

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

因为`GetHttpFile`函数执行潜在延迟操作，过度订阅可以启用其他任务运行，因为当前任务等待数据。 此示例的完整版本，请参阅[如何： 使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

[[返回页首](#top)]

##  <a name="memory"></a> 使用并发内存管理函数在可能的情况

使用内存管理函数， [concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)并[concurrency:: free](reference/concurrency-namespace-functions.md#free)，如果你具有经常分配小型对象的生存期相对较短的精细任务。 并发运行时保存每个正在运行的线程的单独的内存缓存。 `Alloc`和`Free`函数分配和释放内存而不使用锁或内存屏障的这些缓存。

有关这些内存管理函数的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 有关使用这些函数的示例，请参阅[如何： 使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。

[[返回页首](#top)]

##  <a name="raii"></a> 使用 RAII 来管理并发对象的生存期

并发运行时使用异常处理实现取消操作等功能。 当调用运行时或调用另一个在运行时调用的库，因此，编写异常安全的代码。

*资源获取即初始化*(RAII) 模式是一种方法，以便安全地管理在给定作用域下并发对象的生存期。 RAII 模式下的数据结构是在堆栈上分配的。 该数据结构初始化，或将它创建和销毁或销毁数据结构时释放该资源时获取资源。 RAII 模式可确保在封闭作用域退出之前调用析构函数。 此模式非常有用，在函数包含多个`return`语句。 此模式还可帮助您编写异常安全的代码。 当`throw`语句会导致堆栈展开，析构函数的调用 RAII 对象; 因此，资源始终正确地删除或发布。

运行时定义使用 RAII 模式，例如，多个类[scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class)并[scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)。 这些帮助器类被称为*作用域锁*。 在使用时，这些类提供以下几个好处[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)或[concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)对象。 这些类的构造函数获取对所提供的访问`critical_section`或`reader_writer_lock`对象; 对该对象的析构函数版本访问权限。 范围的锁时被销毁自动释放对其互相排斥的对象的访问，因为您手动解锁的基础对象。

请考虑以下类， `account`，其定义的外部库，因此不能修改。

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

以下示例对执行多个事务`account`并行中的对象。 该示例使用`critical_section`对象对访问进行同步`account`对象，因为`account`类不是并发安全。 每个并行操作都使用`critical_section::scoped_lock`对象来保证`critical_section`操作成功或失败时，对象处于解锁状态。 当帐户余额为负数，`withdraw`操作将失败并引发异常。

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

此示例产生下面的示例输出：

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

有关使用 RAII 模式来管理并发对象的生存期的其他示例，请参阅[演练： 从用户界面线程中删除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)，[如何： 使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)，并[如何： 使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

[[返回页首](#top)]

##  <a name="global-scope"></a> 不要在全局范围内创建并发对象

在全局范围内创建并发对象时，会导致应用程序中出现死锁或内存访问冲突等问题。

例如，在创建并发运行时对象时，如果尚未创建计划程序，运行时会创建一个默认计划程序。 相应地，在全局对象构造期间创建的运行时对象将导致运行时创建此默认计划程序。 但是，此过程采用了内部锁，这会干扰支持并发运行时基础结构的其他对象的初始化过程。 另一个尚未初始化的基础结构对象可能需要此内部锁，因此会导致您的应用程序中发生死锁。

下面的示例演示如何创建全局[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)对象。 此模式不仅适用于 `Scheduler` 类，还适用于并发运行时提供的所有其他类型。 建议您不要遵循此模式，因为它可能会导致您的应用程序中出现意外行为。

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

有关创建的正确方法的示例`Scheduler`对象，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[返回页首](#top)]

##  <a name="shared-data"></a> 不在共享的数据段中使用并发对象

并发运行时不支持在共享的数据部分中，例如，创建的数据部分使用的并发对象[data_seg](../../preprocessor/data-seg.md) `#pragma`指令。 跨进程边界共享一个并发对象可以在运行时置于不一致或无效状态。

[[返回页首](#top)]

## <a name="see-also"></a>请参阅

[并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)<br/>
[将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[如何：使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[演练：从用户界面线程中删除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[异步代理库中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
