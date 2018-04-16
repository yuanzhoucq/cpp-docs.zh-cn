---
title: "并发运行时中的常规最佳做法 |Microsoft 文档"
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
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d5c2c626ceb0243e91e56d70f0d8ae71208b157f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>并发运行时中的常规最佳做法
本文档描述应用于的并发运行时的多个区域的最佳做法。  
  
##  <a name="top"></a> 部分  
 本文档包含以下各节：  
  
- [使用尽可能协作同步构造](#synchronization)  
  
- [避免不产生的时间较长的任务](#yield)  
  
- [使用过度订阅于阻止或具有高延时的偏移量操作](#oversubscription)  
  
- [使用尽可能并发内存管理函数](#memory)  
  
- [使用 RAII 来管理并发对象的生存期](#raii)  
  
- [不要在全局范围内创建并发对象](#global-scope)  
  
- [不在共享的数据段中使用并发对象](#shared-data)  
  
##  <a name="synchronization"></a>使用尽可能协作同步构造  
 并发运行时提供许多不需要外部同步对象的并发安全构造。 例如， [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)类提供并发安全追加和元素访问操作。 但是，对于需要对资源的独占访问的情况下，运行时提供[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)， [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)，和[并发:: 事件](../../parallel/concrt/reference/event-class.md)类。 这些类型的行为以协作方式;因此，第一个任务等待数据任务计划程序可以重新分配到另一个上下文的处理资源。 请尽可能使用这些同步类型而不是其他同步机制，如提供的 Windows API 中，不以协作方式那样工作。 有关这些同步类型和代码示例的详细信息，请参阅[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)和[比较同步数据结构与 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="yield"></a>避免不产生的时间较长的任务  
 由于任务计划程序的行为以协作方式，它不提供任务间的公平性。 因此，任务可以阻止其他任务启动。 虽然这是可接受在某些情况下，这会在其他情况下导致死锁或资源不足。  
  
 下面的示例执行多个任务比已分配的处理资源数。 第一个任务不会生成任务计划程序，因此第二个任务不会在第一个任务完成之前不启动。  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 该示例产生下面的输出：  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  

 有多种方法可以启用这两个任务间的协作。 一种方法是有时将控制权转交给长时间运行任务的任务计划程序。 下面的示例修改`task`函数调用[concurrency::Context::Yield](reference/context-class.md#yield)方法来让任务计划程序执行，以便可以运行另一个任务。  

  
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
  
 `Context::Yield`方法可让出仅另一个活动线程在与当前线程的所属，轻量级任务或另一个操作系统线程计划程序上。 此方法不会生成工作计划运行[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象但尚未开始。  
  
 还有其他方法，以便在长时间运行的任务之间的协作。 为较小的多个子任务，可以中断大型任务。 你还可以启用较长的任务执行期间的过度订阅。 可以通过过度订阅创建比可用硬件线程数更多的线程。 时间较长的任务包含很长的延迟，例如，从磁盘或从网络连接读取数据，过度订阅时特别有用。 有关轻量级任务和过度订阅的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="oversubscription"></a>使用过度订阅于阻止或具有高延时的偏移量操作  
 并发运行时提供同步基元，如[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)，，以便任务能够以协作方式停滞和将控制权转交给彼此。 当一个任务以协作方式阻止或生成时，任务计划程序可以重新分配到另一个上下文的处理资源，如第一个任务等待数据。  
  
 在你不能在其中使用并发运行时提供的协作停滞机制的情况下。 例如，你使用的外部库可能使用不同的同步机制。 另一个示例是执行操作时，可能存在很长的延迟，例如，当你使用 Windows API`ReadFile`函数从网络连接读取数据。 在这些情况下，过度订阅可以启用要在另一个任务空闲时运行的其他任务。 可以通过过度订阅创建比可用硬件线程数更多的线程。  
  
 请考虑以下函数， `download`，其中下载了给定的 URL 的文件。 此示例使用[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法临时增加活动线程数。  

 [!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 因为`GetHttpFile`函数执行潜在延迟操作，过度订阅可以启用其他任务运行在当前任务等待数据。 此示例的完整版本，请参阅[如何： 使用过度订阅偏移延迟到](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="memory"></a>使用尽可能并发内存管理函数  

 使用内存管理函数[concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)和[concurrency:: free](reference/concurrency-namespace-functions.md#free)，如果你具有经常分配生存期相对较短的小型对象的精细任务。 并发运行时包含单独的内存缓存中，以便每个正在运行的线程。 `Alloc`和`Free`函数分配和释放内存从这些缓存而不使用锁或内存屏障。  
  
 有关这些内存管理函数的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 有关使用这些函数的示例，请参阅[如何： 使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="raii"></a>使用 RAII 来管理并发对象的生存期  
 并发运行时使用异常处理来实现的功能，例如取消。 调入运行时或调用调入运行时的另一个库时，因此，编写异常安全的代码。  
  
 *获取资源即初始化*(RAII) 模式是一种方法，以便安全地管理在给定作用域下的并发对象的生存期。 下 RAII 模式，在堆栈上分配一种数据结构。 该数据结构初始化，或在创建和销毁或销毁数据结构时释放该资源时，获取一个资源。 RAII 模式可确保在封闭作用域退出之前被调用的析构函数。 当函数包含多个时，此模式将有用`return`语句。 此模式还可帮助你编写异常安全的代码。 当`throw`语句会导致堆栈展开，析构函数调用 RAII 对象的; 因此，资源是始终正确地删除或释放。  
  
 运行时定义了几种使用 RAII 模式，例如，类[concurrency::critical_section::scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)。 这些帮助器类称为*范围锁*。 当您使用时，这些类将提供以下几个好处[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)或[concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)对象。 这些类的构造函数获取对提供的访问`critical_section`或`reader_writer_lock`对象; 对该对象的析构函数版本访问权限。 因为它被销毁时自动范围的锁释放对其的互相排斥对象的访问，你手动解锁基础对象。  
  
 请考虑以下类， `account`，这由外部库定义，并因此不能修改。  
  
 [!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]  
  
 下面的示例执行多个事务上`account`并行的对象。 该示例使用`critical_section`对访问进行同步的对象`account`对象，因为`account`类不是并发安全。 每个并行操作使用`critical_section::scoped_lock`对象来保证`critical_section`该操作成功或失败时，对象处于解除锁定状态。 当帐户余额为负，`withdraw`通过引发异常的操作失败。  
  
 [!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]  
  
 该示例产生下面的示例输出：  
  
```Output  
Balance before deposit: 1924  
Balance after deposit: 2924  
Balance before withdrawal: 2924  
Balance after withdrawal: -76  
Balance before withdrawal: -76  
Error details:  
    negative balance: -76  
```  
  
 有关使用 RAII 模式，来管理并发对象的生存期的其他示例，请参阅[演练： 从用户界面线程中删除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)，[如何： 使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)，和[如何： 使用过度订阅抵消延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="global-scope"></a>不要在全局范围内创建并发对象  
 在全局范围内创建并发对象时，会导致应用程序中出现死锁或内存访问冲突等问题。  
  
 例如，在创建并发运行时对象时，如果尚未创建计划程序，运行时会创建一个默认计划程序。 相应地，在全局对象构造期间创建的运行时对象将导致运行时创建此默认计划程序。 但是，此过程采用了内部锁，这会干扰支持并发运行时基础结构的其他对象的初始化过程。 另一个尚未初始化的基础结构对象可能需要此内部锁，因此会导致您的应用程序中发生死锁。  
  
 下面的示例演示如何创建全局[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)对象。 此模式不仅适用于 `Scheduler` 类，还适用于并发运行时提供的所有其他类型。 建议您不要遵循此模式，因为它可能会导致您的应用程序中出现意外行为。  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]  
  
 有关创建的正确方法的示例`Scheduler`对象，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="shared-data"></a>不在共享的数据段中使用并发对象  
 并发运行时不支持在共享的数据部分中，例如，在 data 节创建并发对象的使用[data_seg](../../preprocessor/data-seg.md) `#pragma`指令。 跨进程边界共享的并发对象无法将运行时置于不一致或无效的状态。  
  
 [[返回页首](#top)]  
  
## <a name="see-also"></a>请参阅  
 [并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)   
 [将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [如何： 使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [如何： 使用过度订阅抵消延迟](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [如何： 使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [演练： 从用户界面线程中删除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [异步代理库中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
