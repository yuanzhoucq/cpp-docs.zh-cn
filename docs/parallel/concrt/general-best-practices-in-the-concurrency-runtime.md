---
title: "并发运行时中的常规最佳做法 | Microsoft Docs"
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
  - "并发运行时，常规最佳做法"
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 并发运行时中的常规最佳做法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档描述应用于并发运行时的多个领域的最佳实践。  
  
##  <a name="top"></a> 各节内容  
 本文档包含以下几节：  
  
-   [尽可能使用协作同步构造](#synchronization)  
  
-   [避免不让步的长任务](#yield)  
  
-   [使用过度订阅抵消停滞或高延迟的操作](#oversubscription)  
  
-   [尽可能使用并发内存管理函数](#memory)  
  
-   [使用 RAII 管理并发对象的生存期](#raii)  
  
-   [不要在全局范围内创建并发对象](#global-scope)  
  
-   [不要在共享数据段中使用并发对象](#shared-data)  
  
##  <a name="synchronization"></a> 尽可能使用协作同步构造  
 并发运行时提供了许多无需外部同步对象的并发安全的构造。  例如，[concurrency::concurrent\_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 类可提供并发安全的追加和元素访问操作。  但是，如果您需要对资源进行独占访问，则运行时可提供 [Concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md)、[concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 和 [concurrency::event](../../parallel/concrt/reference/event-class.md) 类。  这些类型以协作方式工作；因此，当第一个任务等待数据时，任务计划程序可以将处理资源重新分配给另一个上下文。  请尽可能使用这些同步类型而不是其他同步机制，例如 Windows API（它不以协作方式工作）提供的同步机制。  有关这些同步类型和代码示例的更多信息，请参见[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)和[将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="yield"></a> 避免不让步的长任务  
 因为任务计划程序以协作方式工作，所以它无法保证任务之间的公平性。  因此，一项任务可以阻止其他任务启动。  虽然这在某些情况下是可以接受的，但在其他情况下可能导致死锁或匮乏。  
  
 以下示例可执行比已分配的处理资源数更多的任务。  第一个任务不对任务计划程序让步，因此在完成第一个任务之前，第二个任务不会启动。  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 该示例产生下面的输出：  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  
 可通过几种方式在这两个任务之间实现协作。  一种方式是在长期运行任务中偶尔对任务计划程序做出让步。  以下示例修改了 `task` 函数，以便调用 [concurrency::Context::Yield](../Topic/Context::Yield%20Method.md) 方法来让任务计划程序先运行另一个任务。  
  
 [!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_2.cpp)]  
  
 该示例产生下面的输出：  
  
  **1: 250000000**  
**2: 250000000**  
**1: 500000000**  
**2: 500000000**  
**1: 750000000**  
**2: 750000000**  
**1: 1000000000**  
**2: 1000000000** `Context::Yield` 方法只对当前线程所属的计划程序中的其他活动线程、轻量级任务或另一个操作系统线程做出让步。  此方法不会对 [Concurrency::task\_group](../Topic/task_group%20Class.md) 或 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 对象中计划运行但尚未开始的工作做出让步。  
  
 还可以通过其他方式在长期运行的任务之间实现协作。  您可以将大任务划分为较小的子任务，  还可以在执行长期任务期间启用过度订阅。  您可以通过过度订阅创建比可用硬件线程数更多的线程。  如果长期任务包含大量延迟（例如，从磁盘或网络连接读取数据），则过度订阅会很有用。  有关轻量级任务和过度订阅的更多信息，请参见[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="oversubscription"></a> 使用过度订阅抵消停滞或高延迟的操作  
 并发运行时可提供同步基元（如 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md)），以便任务能够以协作方式停滞和互相做出让步。  如果一项任务以协作方式停滞或做出让步，那么当第一个任务等待数据时，任务计划程序可以将处理资源重新分配给另一个上下文。  
  
 在某些情况下，您无法使用并发运行时提供的协作停滞机制。  例如，您所使用的外部库可能使用不同的同步机制。  又比如，当您执行包含大量延迟的操作时，例如，您使用 Windows API `ReadFile` 函数从网络连接读取数据。  在这些情况下，过度订阅会在另一个任务闲置时使其他任务能够运行。  您可以通过过度订阅创建比可用硬件线程数更多的线程。  
  
 请考虑下面的 `download` 函数，它使用指定 URL 下载文件。  此示例使用 [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) 方法临时增加活动线程的数量。  
  
 [!CODE [concrt-download-oversubscription#4](../CodeSnippet/VS_Snippets_ConcRT/concrt-download-oversubscription#4)]  
  
 因为 `GetHttpFile` 函数执行潜在延迟操作，所以在当前任务等待数据时，过度订阅可以使其他任务能够运行。  有关此示例的完整版本，请参见[如何：使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="memory"></a> 尽可能使用并发内存管理函数  
 如果您具有经常分配生存期相对较短的小型对象的精细任务时，可使用内存管理函数 [concurrency::Alloc](../Topic/Alloc%20Function.md) 和 [concurrency::Free](../Topic/Free%20Function.md)。  并发运行时为每个正在运行的线程保留单独的内存缓存。  在不使用锁或内存屏障的情况下，`Alloc` 和 `Free` 函数从这些缓存分配和释放内存。  
  
 有关这些内存管理函数的更多信息，请参见[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  有关使用这些函数的示例，请参见[如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="raii"></a> 使用 RAII 管理并发对象的生存期  
 并发运行时使用异常处理实现取消等功能。  因此，在您调用运行时或调用另一个调用该运行时的库时，可编写异常安全代码。  
  
 “资源获取即初始化”\(RAII\) 模式是一种在给定范围内安全管理并发对象的生存期的方式。  在 RAII 模式下，将在堆栈上分配一个数据结构。  该数据结构在创建时将会初始化或获取一个资源，而且该数据结构在销毁时将会销毁或释放该资源。  RAII 模式可确保在封闭范围退出之前调用析构函数。  在函数包含多个 `return` 语句时，此模式很有用。  此模式还可帮助您编写异常安全代码。  在 `throw` 语句导致堆栈展开时，将会调用 RAII 对象的析构函数；因此，始终会正确删除或释放资源。  
  
 运行时定义了几种使用 RAII 模式的类，例如，[concurrency::critical\_section::scoped\_lock](../Topic/critical_section::scoped_lock%20Class.md) 和 [concurrency::reader\_writer\_lock::scoped\_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md)。  这些帮助器类称作“范围锁”。  在使用 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 或 [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 对象时，这些类可提供若干好处。  这些类的构造函数需要对已提供的 `critical_section` 或 `reader_writer_lock` 对象的访问权限；而析构函数可释放对此对象的访问权限。  当销毁范围锁时，它会自动释放对其互斥对象的访问权；因此，请不要手动为基础对象解锁。  
  
 请考虑 `account` 类，它由外部库定义，因此无法修改。  
  
 [!CODE [concrt-account-transactions#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-account-transactions#1)]  
  
 以下示例对 `account` 对象并行执行多个事务。  该示例使用 `critical_section` 对象同步访问 `account` 对象，因为 `account` 类是并发安全的。  每项并行操作都使用 `critical_section::scoped_lock` 对象来保证在操作成功或失败时可以解锁 `critical_section` 对象。  如果帐户余额为负，则可引发异常以使 `withdraw` 操作失败。  
  
 [!CODE [concrt-account-transactions#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-account-transactions#2)]  
  
 此示例产生下面的示例输出：  
  
  **在存款之前平衡：1924**   
**存款之后平衡：2924**  
**提款之前平衡：2924**  
**提款之后平衡：\-76**  
**提款之前平衡：\-76**  
**错误详细信息:**   
 **负数平衡：\-76** 有关使用 RAII 模式管理并发对象生存期的其他示例，请参见[演练：从用户界面线程中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)、[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)和[如何：使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="global-scope"></a> 不要在全局范围内创建并发对象  
 在全局范围内创建并发对象时可在应用程序中导致问题 ，如内存访问冲突或死锁。  
  
 例如，在创建并发运行时对象时，如果尚未创建计划程序，那么运行时会创建一个默认计划程序。  在全局对象构造期间创建的运行时对象创建将相应地造成此运行时创建默认计划程序。  但是，此过程采用了内部锁，这可能会干扰支持并发运行时基础结构的其他对象的初始化过程。  另一个尚未初始化的基础结构对象可能需要此内部锁，所以您的应用程序可能发生死锁。  
  
 以下示例演示了如何创建全局 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 对象。  此模式不仅适用于 `Scheduler` 类，还适用于并发运行时提供的所有其他类型。  建议您不要遵循此模式，因为它可能导致您的应用程序出现意外的行为。  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 有关创建 `Scheduler` 对象的正确方式的示例，请参见[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="shared-data"></a> 不要在共享数据段中使用并发对象  
 并发运行时不支持在共享数据段（例如，由 [data\_seg](../../preprocessor/data-seg.md) `#pragma` 指令创建的数据段）中使用并发对象。  跨进程边界共享的并发对象可使运行时处于不一致或无效的状态。  
  
 \[[Top](#top)\]  
  
## 请参阅  
 [并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [并行模式库 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)   
 [将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [如何：使用过度订阅偏移延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [演练：从用户界面线程中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [异步代理库中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)