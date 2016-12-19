---
title: "同步数据结构 | Microsoft Docs"
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
  - "同步数据结构"
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
caps.latest.revision: 26
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 同步数据结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

并发运行时提供了几个数据结构，利用这些结构可以同步对多个线程中的共享数据的访问。  当您不经常修改共享数据时，这些数据结构很有用。  同步对象（如临界区）会导致其他线程在共享资源可用之前一直等待。  因此，如果使用此类对象来同步对常用数据的访问，则会让应用程序失去可伸缩性。  [并行模式库 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 提供 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 类，以使您能够在无需同步的情况下在几个线程或任务之间共享资源。  有关 `combinable` 类的更多信息，请参见[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
##  <a name="top"></a> 各节内容  
 本主题详细介绍下列异步消息块类型：  
  
-   [critical\_section](#critical_section)  
  
-   [reader\_writer\_lock](#reader_writer_lock)  
  
-   [scoped\_lock and scoped\_lock\_read](#scoped_lock)  
  
-   [event](#event)  
  
##  <a name="critical_section"></a> critical\_section  
 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 类表示一个协作性互斥对象，该对象将会让位于其他任务，而不是优先于它们。  当多个线程需要对共享数据进行独占读写访问时，临界区很有用。  
  
 `critical_section` 类是非重入的。  如果已拥有锁的线程调用 [concurrency::critical\_section::lock](../Topic/critical_section::lock%20Method.md) 方法，则该方法将引发类型为 [concurrency::improper\_lock](../../parallel/concrt/reference/improper-lock-class.md) 的异常。  
  
### 方法和功能  
 下表显示 `critical_section` 类定义的重要方法。  
  
|方法|说明|  
|--------|--------|  
|[lock](../Topic/critical_section::lock%20Method.md)|获取临界区。  调用上下文在获取锁之前将阻塞。|  
|[try\_lock](../Topic/critical_section::try_lock%20Method.md)|尝试获取临界区，但不阻塞。|  
|[unlock](../Topic/critical_section::unlock%20Method.md)|释放临界区。|  
  
 \[[Top](#top)\]  
  
##  <a name="reader_writer_lock"></a> reader\_writer\_lock  
 [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 类提供对共享数据的线程安全的读\/写操作。  当多个线程需要对共享资源的并发读访问，但很少需要对该共享资源的写访问时，请使用读取器\/编写器锁。  此类任何时候都只允许一个线程对一个对象进行写访问。  
  
 `reader_writer_lock` 类的性能好于 `critical_section` 类，这是因为 `critical_section` 对象获取了对共享资源的独占访问权，这将阻止并发读访问。  
  
 与 `critical_section` 类似，`reader_writer_lock` 类表示一个协作性互斥对象，该对象将会让位于其他任务，而不是优先于它们。  
  
 当某个必须写入一个共享资源的线程获取读取器\/编写器锁时，也必须访问该资源的其他线程将被阻塞，直到编写器释放锁。  `reader_writer_lock` 类是“写优先”锁的一个示例，这种锁会先为等待的编写器解锁，然后再为等待的读取器解锁。  
  
 与 `critical_section` 类相似，`reader_writer_lock` 类是非重入的。  如果已拥有锁的线程调用 [concurrency::reader\_writer\_lock::lock](../Topic/reader_writer_lock::lock%20Method.md) 和 [concurrency::reader\_writer\_lock::lock\_read](../Topic/reader_writer_lock::lock_read%20Method.md) 方法，则二者将引发类型为 `improper_lock` 的异常。  
  
> [!NOTE]
>  由于 `reader_writer_lock` 类是非重入的，因此您无法将只读锁升级为读取器\/编写器锁，也无法将读取器\/编写器锁降级为只读锁定。  执行其中任何一项操作都将产生未指定的行为。  
  
### 方法和功能  
 下表显示 `reader_writer_lock` 类定义的重要方法。  
  
|方法|说明|  
|--------|--------|  
|[lock](../Topic/reader_writer_lock::lock%20Method.md)|获取对锁的读\/写访问权。|  
|[try\_lock](../Topic/reader_writer_lock::try_lock%20Method.md)|尝试获取对锁的读\/写访问权，但不阻塞。|  
|[lock\_read](../Topic/reader_writer_lock::lock_read%20Method.md)|获取对锁的只读访问权。|  
|[try\_lock\_read](../Topic/reader_writer_lock::try_lock_read%20Method.md)|尝试获取对锁的只读访问权，但不阻塞。|  
|[unlock](../Topic/reader_writer_lock::unlock%20Method.md)|释放锁。|  
  
 \[[Top](#top)\]  
  
##  <a name="scoped_lock"></a> scoped\_lock and scoped\_lock\_read  
 `critical_section` 和 `reader_writer_lock` 类提供了嵌套的帮助器类，这些类可简化使用互斥对象的方法。  这些帮助器类称作“范围锁”。  
  
 `critical_section` 类包含 [concurrency::critical\_section::scoped\_lock](../Topic/critical_section::scoped_lock%20Class.md) 类。  构造函数获取对提供的 `critical_section` 对象的访问权；析构函数释放对该对象的访问权。  `reader_writer_lock` 类包含 [concurrency::reader\_writer\_lock::scoped\_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md) 类，后者与 `critical_section::scoped_lock` 类相似，只不过它管理对提供的 `reader_writer_lock` 对象的写访问权。  `reader_writer_lock` 类还包含 [concurrency::reader\_writer\_lock::scoped\_lock\_read](../Topic/reader_writer_lock::scoped_lock_read%20Class.md) 类。  此类管理对提供的 `reader_writer_lock` 对象的读访问权。  
  
 在手动使用 `critical_section` 和 `reader_writer_lock` 对象时，范围锁会提供一些好处。  通常，可以在堆栈上分配一个范围锁。  当销毁范围锁时，它会自动释放对其互斥对象的访问权；因此，请不要手动为基础对象解锁。  当函数包含多个 `return` 语句时，这会很有用。  范围锁还可帮助您编写不会发生异常的代码。  当 `throw` 语句导致展开堆栈时，将会调用任何活动范围锁的析构函数，因而始终可以正确释放互斥对象。  
  
> [!NOTE]
>  当使用 `critical_section::scoped_lock`、`reader_writer_lock::scoped_lock` 和 `reader_writer_lock::scoped_lock_read` 类时，请不要手动释放对基础互斥对象的访问权。  这会导致运行时处于无效状态。  
  
##  <a name="event"></a> event  
 [concurrency::event](../../parallel/concrt/reference/event-class.md) 类表示一个同步对象，此对象的状态可以是终止的，也可以是非终止的。  与用于保护对共享数据的访问的同步对象（如临界区）不同，事件用于同步执行流。  
  
 当一个任务已完成另一个任务的工作时，`event` 类很有用。  例如，一个任务可能告知另一个任务它已从网络连接或文件读取数据。  
  
### 方法和功能  
 下表显示 `event` 类定义的几个重要方法。  
  
|方法|说明|  
|--------|--------|  
|[wait](../Topic/event::wait%20Method.md)|等待事件变为终止状态。|  
|[set](../Topic/event::set%20Method.md)|将事件设置为终止状态。|  
|[reset](../Topic/event::reset%20Method.md)|将事件设置为非终止状态。|  
|[wait\_for\_multiple](../Topic/event::wait_for_multiple%20Method.md)|等待多个事件变为终止状态。|  
  
### 示例  
 有关说明如何使用 `event` 类的示例，请参见[将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 \[[Top](#top)\]  
  
## 相关章节  
 [将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 将同步数据结构的行为与 Windows API 提供的行为进行比较。  
  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)  
 描述可简化并行编程的并发运行时，并包含指向相关主题的链接。