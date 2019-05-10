---
title: 同步数据结构
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: f9b949e7782c4b9ca302e9e623ce5f09061c39ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185953"
---
# <a name="synchronization-data-structures"></a>同步数据结构

并发运行时提供了一些可用的数据结构，可从多个线程同步对共享数据的访问。 如果要使用共享不常修改的数据，这些数据结构非常有用。 同步对象，例如，关键部分，会导致其他线程等待，直到该共享的资源可用。 因此，如果使用此类对象频繁使用的数据对访问进行同步，你可以在应用程序中失去可伸缩性。 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)提供[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类，使您能够在多个线程或任务而无需同步之间资源共享。 有关详细信息`combinable`类，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

##  <a name="top"></a> 部分

本主题介绍详细信息中的以下异步消息块类型：

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock 和 scoped_lock_read](#scoped_lock)

- [event](#event)

##  <a name="critical_section"></a> critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)类表示一个协作性互斥对象，而不是优先这些其他任务生成。 当多个线程需要独占读取和写入访问对共享数据时，关键部分非常有用。

`critical_section`类是不可重入。 [Concurrency::critical_section::lock](reference/critical-section-class.md#lock)方法将引发类型的异常[concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md)如果已拥有锁的线程调用。

### <a name="methods-and-features"></a>方法和功能

下表显示了由定义的重要方法`critical_section`类。

|方法|描述|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|获取临界区。 调用上下文受到阻止，直到它获取该锁。|
|[try_lock](reference/critical-section-class.md#try_lock)|尝试获取关键节，但不会阻止。|
|[unlock](reference/critical-section-class.md#unlock)|释放关键节。|

[[返回页首](#top)]

##  <a name="reader_writer_lock"></a> reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)类提供对共享数据的线程安全的读/写操作。 当多个线程需要共享资源的并发读访问权限，但很少写入到该共享资源时，请使用读取器/编写器锁。 此类允许对象在任何时候只有一个线程写入访问。

`reader_writer_lock`类可以执行优于`critical_section`类，因为`critical_section`对象获取独占访问共享资源，这会阻止并发读取访问权限。

像`critical_section`类，`reader_writer_lock`类表示一个协作性互斥对象，而不是优先这些其他任务生成。

当必须将写入到共享资源的线程获取读取器/写入器锁时，直到编写器释放锁将阻止其他线程，还必须访问的资源。 `reader_writer_lock`类是举例*写首选项*锁，这是之前它将取消阻止正在等待读取器将取消阻止正在等待编写器的锁。

像`critical_section`类，`reader_writer_lock`类是不可重入。 [Concurrency::reader_writer_lock::lock](reference/reader-writer-lock-class.md#lock)并[concurrency::reader_writer_lock::lock_read](reference/reader-writer-lock-class.md#lock_read)方法将引发类型的异常`improper_lock`时进行调用的线程已拥有该锁。

> [!NOTE]
>  因为`reader_writer_lock`类是不可重入的不能将只读锁升级到读取器/写入器锁或降级为只读的锁的读取器/编写器锁。 执行这些操作生成未指定的行为。

### <a name="methods-and-features"></a>方法和功能

下表显示了由定义的重要方法`reader_writer_lock`类。

|方法|描述|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|获取对锁的读/写访问。|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|尝试获取对锁的读/写访问权限，但不会阻止。|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|获取对锁的只读访问权限。|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|尝试获取锁，对的只读访问权限，但不会阻止。|
|[unlock](reference/reader-writer-lock-class.md#unlock)|释放锁。|

[[返回页首](#top)]

##  <a name="scoped_lock"></a> scoped_lock 和 scoped_lock_read

`critical_section`和`reader_writer_lock`类提供简化的方式使用互斥对象的嵌套的帮助器类。 这些帮助器类被称为*作用域锁*。

`critical_section`类包含[scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)类。 构造函数获取访问提供的`critical_section`对象; 对该对象的析构函数版本访问权限。 `reader_writer_lock`类包含[scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)类，它类似于`critical_section::scoped_lock`，只不过它管理写入访问权限提供`reader_writer_lock`对象。 `reader_writer_lock`类还包含[2&gt;concurrency::reader_writer_lock::scoped_lock_read&lt;2](reference/reader-writer-lock-class.md#scoped_lock_read_class)类。 此类管理到所提供的读取访问`reader_writer_lock`对象。

指定了作用域的锁时正在使用提供以下几个好处`critical_section`和`reader_writer_lock`手动对象。 通常情况下，分配到堆栈上的指定了作用域的锁。 指定了作用域的锁释放到其互相排斥的对象的访问权自动销毁; 时因此，您不手动解锁的基础对象。 这是有用的当函数包含多个`return`语句。 指定了作用域的锁还有助于你编写异常安全的代码。 当`throw`语句导致要展开的堆栈，调用任何活动的限定了作用域锁的析构函数，且因此始终正确释放互斥对象。

> [!NOTE]
>  当你使用`critical_section::scoped_lock`， `reader_writer_lock::scoped_lock`，和`reader_writer_lock::scoped_lock_read`类，不要手动释放对基础互斥对象的访问。 这可以将运行时放在无效状态。

##  <a name="event"></a> 事件

[Concurrency:: event](../../parallel/concrt/reference/event-class.md)类表示一个同步对象可以发出信号或非终止其状态。 与同步对象，如临界区，其目的是保护对共享数据的访问，不同的事件同步执行流。

`event`类很有用，当一个任务完成另一个任务的工作。 例如，一个任务可能告知另一项任务它已从网络连接或从文件读取数据。

### <a name="methods-and-features"></a>方法和功能

下表显示了多个定义的重要方法`event`类。

|方法|描述|
|------------|-----------------|
|[wait](reference/event-class.md#wait)|等待事件收到信号。|
|[set](reference/event-class.md#set)|将事件设置为终止状态。|
|[reset](reference/event-class.md#reset)|将事件设置为非终止状态。|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|等待多个事件收到信号。|

### <a name="example"></a>示例

有关示例，演示如何使用`event`类，请参阅[比较同步数据结构与 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。

[[返回页首](#top)]

## <a name="related-sections"></a>相关章节

[将同步数据结构与 Windows API 进行比较](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
比较同步数据结构与所提供的 Windows API 的行为。

[并发运行时](../../parallel/concrt/concurrency-runtime.md)<br/>
描述可以简化并发编程并包含相关主题链接的并发运行时。
