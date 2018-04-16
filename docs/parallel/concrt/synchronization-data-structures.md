---
title: "同步数据结构 |Microsoft 文档"
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
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1dd1c47cad01e0324f8027593eb4933f70cd6191
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="synchronization-data-structures"></a>同步数据结构
并发运行时提供了一些可以从多个线程同步对共享数据的访问的数据结构。 如果要使用共享不常修改的数据，这些数据结构非常有用。 同步对象，例如，一个临界区，导致其他线程等待，直到共享的资源是可用。 因此，如果使用此类对象来同步访问频繁使用的数据，你可以在你的应用程序中失去可伸缩性。 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)提供[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类，让你可以共享在多个线程或任务，而不需同步的资源。 有关详细信息`combinable`类，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
##  <a name="top"></a> 部分  
 本主题介绍以下异步消息块类型在详细信息：  
  
-   [critical_section](#critical_section)  
  
-   [reader_writer_lock](#reader_writer_lock)  
  
-   [scoped_lock 和 scoped_lock_read](#scoped_lock)  
  
-   [事件](#event)  
  
##  <a name="critical_section"></a>critical_section  
 [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)类表示一个协作性互斥对象，会其他任务，而不是让它们于。 当多个线程需要独占读取和写入访问共享数据，关键部分非常有用。  

 `critical_section`类是不可重入。 [Concurrency::critical_section::lock](reference/critical-section-class.md#lock)方法将引发类型的异常[concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md)如果它由已拥有锁的线程进行调用。  


  
### <a name="methods-and-features"></a>方法和功能  
 下表显示由定义的重要方法`critical_section`类。  
  
|方法|描述|  
|------------|-----------------|  
|[lock](reference/critical-section-class.md#lock)|获取关键部分。 调用上下文受到阻止，直到它获取该锁。|  
|[try_lock](reference/critical-section-class.md#try_lock)|尝试获取关键部分中，但不会阻止。|  
|[unlock](reference/critical-section-class.md#unlock)|释放关键部分。|  
  
 [[返回页首](#top)]  
  
##  <a name="reader_writer_lock"></a>reader_writer_lock  
 [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)类提供对共享数据的线程安全的读/写操作。 如果多个线程需要对共享资源的并发读取访问，但很少写入到该共享的资源，请使用读取器/编写器锁。 此类，对象在任何时候只有一个线程写入访问。  
  
 `reader_writer_lock`类可以执行更好`critical_section`类，因为`critical_section`对象获取对会阻止并发读访问的共享资源独占访问权。  
  
 如`critical_section`类，`reader_writer_lock`类表示一个协作性互斥对象，会其他任务，而不是让它们于。  
  
 时必须将写入到共享资源的线程获取读取器/编写器锁，还必须访问该资源其他线程将被阻止，直到编写器释放的锁。 `reader_writer_lock`类是一种*写首选项*锁，这是一个锁，阻止等待编写器之前它取消阻止正在等待读取器。  
  
 如`critical_section`类，`reader_writer_lock`类是不可重入。 [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock)和[lock_read](reference/reader-writer-lock-class.md#lock_read)方法将引发类型的异常`improper_lock`如果已拥有一个线程调用它们锁定。  


  
> [!NOTE]
>  因为`reader_writer_lock`类是不可重入，不能将只读锁升级到读取器/编写器锁或降级为只读的锁的读取器/编写器锁。 执行这些操作中的生成未指定的行为。  
  
### <a name="methods-and-features"></a>方法和功能  
 下表显示由定义的重要方法`reader_writer_lock`类。  
  
|方法|描述|  
|------------|-----------------|  
|[lock](reference/reader-writer-lock-class.md#lock)|获取为锁的读/写访问。|  
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|尝试获取锁后，对的读/写访问，但不会阻止。|  
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|获取为锁的只读访问权限。|  
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|尝试获取锁后，对的只读访问，但不会阻止。|  
|[unlock](reference/reader-writer-lock-class.md#unlock)|释放的锁。|  
  
 [[返回页首](#top)]  
  
##  <a name="scoped_lock"></a>scoped_lock 和 scoped_lock_read  
 `critical_section`和`reader_writer_lock`类提供嵌套的帮助器类，用于简化使用互相排斥的对象的方式。 这些帮助器类称为*范围锁*。  
  
 `critical_section`类包含[concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)类。 构造函数获取对提供的访问`critical_section`对象; 对该对象的析构函数版本访问权限。 `reader_writer_lock`类包含[concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)类，类似于`critical_section::scoped_lock`，只不过它管理对提供写入访问权限`reader_writer_lock`对象。 `reader_writer_lock`类还包含[concurrency::reader_writer_lock::scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class)类。 此类管理到所提供的读取访问`reader_writer_lock`对象。  

  
 范围的锁时你正在使用提供以下几个好处`critical_section`和`reader_writer_lock`手动对象。 通常情况下，你分配在堆栈上的一个范围的锁。 指定了作用域的锁释放到其互斥对象的访问权自动销毁; 时因此，你不手动解锁基础对象。 这是有用的当函数包含多个`return`语句。 指定了作用域的锁还可以帮助你编写异常安全的代码。 当`throw`语句会导致堆栈展开，调用任何活动范围锁的析构函数，因此始终可以正确释放互斥对象。  
  
> [!NOTE]
>  当你使用`critical_section::scoped_lock`， `reader_writer_lock::scoped_lock`，和`reader_writer_lock::scoped_lock_read`类，不会手动释放的基础的互相排斥对象的访问。 这可以使运行时处于无效状态。  
  
##  <a name="event"></a>事件  
 [Concurrency:: event](../../parallel/concrt/reference/event-class.md)类表示可以发出信号或非终止其状态的同步对象。 与同步对象，例如临界区，其目的是保护对共享数据的访问，不同事件同步执行流。  
  
 `event`一个任务已完成工作的另一个任务类很有用。 例如，一个任务可能告知另一个任务，它已从网络连接或从文件读取数据。  
  
### <a name="methods-and-features"></a>方法和功能  
 下表显示几种重要方法定义的`event`类。  
  
|方法|描述|  
|------------|-----------------|  
|[等待](reference/event-class.md#wait)|等待事件变为终止状态。|  
|[set](reference/event-class.md#set)|将事件设置为终止状态。|  
|[reset](reference/event-class.md#reset)|将事件设置为非终止状态。|  
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|等待多个事件都变为终止状态。|  

  
### <a name="example"></a>示例  
 有关示例，演示如何使用`event`类，请参阅[比较同步数据结构与 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 [[返回页首](#top)]  
  
## <a name="related-sections"></a>相关章节  
 [将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)  
 比较同步数据结构与所提供的 Windows API 的行为。  
  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)  
 描述可以简化并发编程并包含相关主题链接的并发运行时。

