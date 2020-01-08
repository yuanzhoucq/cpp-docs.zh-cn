---
title: 并发运行时中的常规最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: bb00c3ddb9a50a159174deccf8954f1e3bf1689d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302219"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>并发运行时中的常规最佳做法

本文档介绍适用于并发运行时的多个区域的最佳实践。

##  <a name="top"></a> 部分

本文档包含以下各节：

- [尽可能使用协作式同步构造](#synchronization)

- [避免不会产生的漫长任务](#yield)

- [使用过度订阅偏移阻止或具有高延迟的操作](#oversubscription)

- [尽可能使用并发内存管理函数](#memory)

- [使用 RAII 管理并发对象的生存期](#raii)

- [不要在全局范围内创建并发对象](#global-scope)

- [不要使用共享数据段中的并发对象](#shared-data)

##  <a name="synchronization"></a>尽可能使用协作式同步构造

并发运行时提供了许多不需要外部同步对象的并发安全构造。 例如， [concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类提供并发安全追加和元素访问操作。 此处，并发安全意味着指针或迭代器始终有效。 它不能保证元素初始化，也不能保证特定的遍历顺序。 但是，对于需要对资源进行独占访问的情况，运行时提供[concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)、 [concurrency：： reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)和[concurrency：：事件类](../../parallel/concrt/reference/event-class.md)。 这些类型以协作方式进行：因此，任务计划程序可以在第一个任务等待数据时将处理资源重新分配给另一个上下文。 如果可能，请使用这些同步类型，而不是其他同步机制，如 Windows API 提供的那些方法，这些同步机制不是以协作方式进行的。 有关这些同步类型和代码示例的详细信息，请参阅[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)和将[同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。

[[返回页首](#top)]

##  <a name="yield"></a>避免不会产生的漫长任务

因为任务计划程序的行为是合作的，所以它不能在任务之间实现公平。 因此，任务会阻止其他任务启动。 尽管这在某些情况下是可接受的，但在其他情况下，这可能会导致死锁或资源不足。

下面的示例执行的任务比分配的处理资源数多。 第一个任务不会生成任务计划程序，因此第一个任务完成后，第一个任务才会开始。

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

该示例产生下面的输出：

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

有多种方法可实现两个任务之间的协作。 其中一种方法是在长时间运行的任务中偶尔产生任务计划程序。 下面的示例修改了 `task` 函数以调用[concurrency：： Context：： yield](reference/context-class.md#yield)方法，以将执行任务计划程序，以便可以运行其他任务。

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

`Context::Yield` 方法仅在当前线程所属的计划程序、轻量级任务或其他操作系统线程上生成另一个活动线程。 此方法不会产生计划在[concurrency：： task_group](reference/task-group-class.md)或[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象中运行，但尚未开始的工作。

还可以通过其他方式在长时间运行的任务之间实现协作。 可以将大型任务拆分为较小的子任务。 你还可以在漫长的任务期间启用过度订阅。 可以通过过度订阅创建比可用硬件线程数更多的线程。 当漫长的任务包含大量延迟时（例如，从磁盘或从网络连接读取数据），过度订阅特别有用。 有关轻量级任务和过度订阅的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[返回页首](#top)]

##  <a name="oversubscription"></a>使用过度订阅偏移阻止或具有高延迟的操作

并发运行时提供了同步基元（如[Concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)），它们使任务能够以协作方式阻止和生成。 当某个任务以协作方式阻止或生成时，任务计划程序可以在第一个任务等待数据时将处理资源重新分配给另一个上下文。

有些情况下，不能使用由并发运行时提供的协作阻止机制。 例如，你使用的外部库可能会使用不同的同步机制。 另一个示例是当你执行可能具有大量延迟的操作时，例如，当你使用 Windows API `ReadFile` 函数从网络连接读取数据时。 在这些情况下，过度订阅可以允许其他任务在其他任务处于空闲状态时运行。 可以通过过度订阅创建比可用硬件线程数更多的线程。

请考虑下面的函数 `download`，它将在给定的 URL 下载文件。 此示例使用[concurrency：： Context：：超额订阅](reference/context-class.md#oversubscribe)方法来暂时增加活动线程数。

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

由于 `GetHttpFile` 函数会执行潜在的潜在操作，因此，过度订阅可以允许其他任务在当前任务等待数据时运行。 有关此示例的完整版本，请参阅[如何：使用过度订阅抵消滞后时间](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

[[返回页首](#top)]

##  <a name="memory"></a>尽可能使用并发内存管理函数

当你具有经常分配生存期相对较短的小型对象的精细任务时，可使用内存管理函数[concurrency：：分配](reference/concurrency-namespace-functions.md#alloc)和[Concurrency：： Free](reference/concurrency-namespace-functions.md#free)。 并发运行时保存每个正在运行的线程的单独内存缓存。 `Alloc` 和 `Free` 函数在不使用锁或内存屏障的情况下，从这些缓存分配并释放内存。

有关这些内存管理函数的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 有关使用这些函数的示例，请参阅[如何：使用分配和自由提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。

[[返回页首](#top)]

##  <a name="raii"></a>使用 RAII 管理并发对象的生存期

并发运行时使用异常处理来实现某些功能，如取消。 因此，当你调入运行时或调用调用运行时的另一个库时，请编写异常安全的代码。

*资源采集为初始化*（RAII）模式是一种安全管理给定范围下并发对象生存期的方法。 在 RAII 模式下，在堆栈上分配数据结构。 此数据结构在创建时初始化或获取资源，并在数据结构销毁时销毁或释放该资源。 RAII 模式可确保在封闭范围退出之前调用析构函数。 当函数包含多个 `return` 语句时，此模式非常有用。 此模式还有助于编写异常安全的代码。 当 `throw` 语句导致堆栈展开时，将调用 RAII 对象的析构函数;因此，始终会正确地删除或释放资源。

运行时定义了几个使用 RAII 模式的类，例如[concurrency：： critical_section：： scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency：： reader_writer_lock：： scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)。 这些帮助器类称为*范围锁*。 使用[concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)或[concurrency：： reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)对象时，这些类提供了若干优点。 这些类的构造函数获取对所提供 `critical_section` 或 `reader_writer_lock` 对象的访问权限;析构函数释放对该对象的访问权限。 由于作用域锁定在销毁时，会自动释放对其互斥对象的访问权限，因此你不会手动解锁基础对象。

请考虑以下类，`account`，它是由外部库定义的，因此无法修改。

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

下面的示例并行对 `account` 对象执行多个事务。 该示例使用 `critical_section` 对象同步对 `account` 对象的访问，因为 `account` 类不是并发安全的类。 每个并行操作都使用 `critical_section::scoped_lock` 对象来保证当操作成功或失败时，`critical_section` 对象处于解锁状态。 当帐户余额为负数时，`withdraw` 操作会引发异常。

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

此示例将生成以下示例输出：

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

有关使用 RAII 模式来管理并发对象生存期的其他示例，请参阅[演练：从用户界面线程中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)，[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)，以及[如何：使用过度订阅抵消延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

[[返回页首](#top)]

##  <a name="global-scope"></a>不要在全局范围内创建并发对象

在全局范围内创建并发对象时，会导致应用程序中出现死锁或内存访问冲突等问题。

例如，在创建并发运行时对象时，如果尚未创建计划程序，运行时会创建一个默认计划程序。 相应地，在全局对象构造期间创建的运行时对象将导致运行时创建此默认计划程序。 但是，此过程采用了内部锁，这会干扰支持并发运行时基础结构的其他对象的初始化过程。 另一个尚未初始化的基础结构对象可能需要此内部锁，因此会导致您的应用程序中发生死锁。

下面的示例演示如何创建全局[concurrency：：计划程序](../../parallel/concrt/reference/scheduler-class.md)对象。 此模式不仅适用于 `Scheduler` 类，还适用于并发运行时提供的所有其他类型。 建议您不要遵循此模式，因为它可能会导致您的应用程序中出现意外行为。

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

有关创建 `Scheduler` 对象的正确方法的示例，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[返回页首](#top)]

##  <a name="shared-data"></a>不要使用共享数据段中的并发对象

并发运行时不支持在共享数据部分中使用并发对象，例如，由[data_seg](../../preprocessor/data-seg.md)`#pragma` 指令创建的数据节。 跨进程边界共享的并发对象可能将运行时置于不一致或无效状态。

[[返回页首](#top)]

## <a name="see-also"></a>另请参阅

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
