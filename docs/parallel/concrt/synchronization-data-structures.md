---
title: 同步数据结构
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 244aaac9bd40c83d0bbec3c360bdf7351da54baf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231658"
---
# <a name="synchronization-data-structures"></a>同步数据结构

并发运行时提供了几个数据结构，使您可以同步对多个线程中的共享数据的访问。 当你有不经常修改的共享数据时，这些数据结构非常有用。 例如，一个同步对象会导致其他线程等待，直到共享资源可用。 因此，如果你使用此类对象来同步对频繁使用的数据的访问，则你的应用程序中的可伸缩性会丢失。 [并行模式库（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)提供[concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md)类，使你能够在多个线程或任务之间共享资源，而无需进行同步。 有关类的详细信息 `combinable` ，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="sections"></a><a name="top"></a>个

本主题详细描述了以下异步消息块类型：

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock 和 scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a><a name="critical_section"></a>critical_section

[Concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)类表示生成到其他任务而不是对其进行抢占的协作式互斥对象。 当多个线程需要对共享数据进行排他读写访问时，关键部分会很有用。

`critical_section`类是非重入的。 如果已拥有锁的线程调用[concurrency：： critical_section：： lock](reference/critical-section-class.md#lock)方法，则该方法将引发类型为[concurrency：： improper_lock](../../parallel/concrt/reference/improper-lock-class.md)的异常。

### <a name="methods-and-features"></a>方法和功能

下表显示了由类定义的重要方法 `critical_section` 。

|方法|描述|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|获取临界区。 调用上下文将被阻止，直到它获取锁。|
|[try_lock](reference/critical-section-class.md#try_lock)|尝试获取临界区，但不会阻止。|
|[解锁](reference/critical-section-class.md#unlock)|释放临界区。|

[[顶部](#top)]

## <a name="reader_writer_lock"></a><a name="reader_writer_lock"></a>reader_writer_lock

[Concurrency：： reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)类向共享数据提供线程安全的读/写操作。 当多个线程需要对共享资源进行并发读取访问，但很少写入该共享资源时，请使用读取器/编写器锁。 此类在任何时候都只为一个对象提供一个线程写入访问权限。

`reader_writer_lock`类的性能比类更好 `critical_section` `critical_section` ，因为对象获取共享资源的独占访问权限，这会阻止并发读取访问。

与 `critical_section` 类一样， `reader_writer_lock` 类表示对其他任务产生的合作互斥对象，而不是对其进行抢占。

当必须写入共享资源的线程获取读取器/写入器锁时，还必须访问该资源的其他线程将被阻止，直到编写器释放该锁。 此 `reader_writer_lock` 类是*写首选项*锁的一个示例，它是在取消阻止等待读取器之前取消阻止等待写入器的锁。

与 `critical_section` 类一样， `reader_writer_lock` 类是不可重入的。 如果已拥有锁的线程调用[concurrency：： reader_writer_lock：： lock](reference/reader-writer-lock-class.md#lock)和[concurrency：： reader_writer_lock：： lock_read](reference/reader-writer-lock-class.md#lock_read)方法，则会引发该异常 `improper_lock` 。

> [!NOTE]
> 由于 `reader_writer_lock` 类是不可重入的，因此不能将只读锁升级为读取器/写入器锁或将读取器/写入器锁降级为只读锁。 执行其中任一操作都会产生未指定的行为。

### <a name="methods-and-features"></a>方法和功能

下表显示了由类定义的重要方法 `reader_writer_lock` 。

|方法|描述|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|获取对锁的读/写访问权限。|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|尝试获取对锁的读/写访问权限，但不会阻止。|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|获取对锁的只读访问权限。|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|尝试获取对锁的只读访问权限，但不会阻止。|
|[解锁](reference/reader-writer-lock-class.md#unlock)|释放锁。|

[[顶部](#top)]

## <a name="scoped_lock-and-scoped_lock_read"></a><a name="scoped_lock"></a>scoped_lock 和 scoped_lock_read

`critical_section`和 `reader_writer_lock` 类提供了嵌套的帮助器类，这些类可简化对互斥对象的处理方式。 这些帮助器类称为*范围锁*。

`critical_section`类包含[concurrency：： critical_section：： scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)类。 构造函数获取对所提供对象的访问权限 `critical_section` ; 析构函数释放对该对象的访问权限。 `reader_writer_lock`类包含[concurrency：： reader_writer_lock：： scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)类，这类似于 `critical_section::scoped_lock` ，但它管理对提供的对象的写访问权限 `reader_writer_lock` 。 `reader_writer_lock`类还包含[concurrency：： reader_writer_lock：： scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class)类。 此类管理提供的对象的读取访问权限 `reader_writer_lock` 。

当你手动使用和对象时，作用域锁具有几个优点 `critical_section` `reader_writer_lock` 。 通常，在堆栈上分配范围锁。 范围锁在销毁时自动释放对其互斥对象的访问权限;因此，您不需要手动解锁基础对象。 当函数包含多个语句时，这非常有用 **`return`** 。 范围锁还有助于编写异常安全的代码。 当 **`throw`** 语句导致堆栈展开时，将调用任何活动范围锁的析构函数，因此，始终会正确释放互斥对象。

> [!NOTE]
> 当你使用 `critical_section::scoped_lock` 、 `reader_writer_lock::scoped_lock` 和类时 `reader_writer_lock::scoped_lock_read` ，不要手动释放对基础互斥排除对象的访问权限。 这会使运行时处于无效状态。

## <a name="event"></a><a name="event"></a> 事件

[Concurrency：： event](../../parallel/concrt/reference/event-class.md)类表示一个同步对象，该对象的状态可以为 "已终止" 或 "非终止"。 与诸如临界区（其目的是保护对共享数据的访问）的同步对象不同，事件同步执行流。

`event`当一个任务已完成另一个任务的工作时，此类很有用。 例如，一个任务可以通知另一个任务它已从网络连接或文件中读取数据。

### <a name="methods-and-features"></a>方法和功能

下表显示了由类定义的几个重要方法 `event` 。

|方法|描述|
|------------|-----------------|
|[再](reference/event-class.md#wait)|等待事件进入终止状态。|
|[set](reference/event-class.md#set)|将事件设置为终止状态。|
|[reset](reference/event-class.md#reset)|将事件设置为非终止状态。|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|等待多个事件发出信号。|

### <a name="example"></a>示例

有关演示如何使用类的示例 `event` ，请参阅将[同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。

[[顶部](#top)]

## <a name="related-sections"></a>相关章节

[将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
比较同步数据结构与 Windows API 提供的结构的行为。

[并发运行时](../../parallel/concrt/concurrency-runtime.md)<br/>
描述可以简化并发编程并包含相关主题链接的并发运行时。
