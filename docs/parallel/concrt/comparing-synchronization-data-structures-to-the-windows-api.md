---
title: 将同步数据结构与 Windows API 进行比较
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 16d58431ae3f9859677302010f15a75b37ebedbf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510593"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>将同步数据结构与 Windows API 进行比较

本主题比较并发运行时提供的同步数据结构与 Windows API 提供的结构的行为。

并发运行时提供的同步数据结构遵循*协作线程处理模型*。 在协作式线程处理模型中, 同步基元会将其处理资源显式生成到其他线程。 这不同于*抢先线程模型*, 在该模型中, 处理资源由控制计划程序或操作系统传输到其他线程。

## <a name="critical_section"></a>critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)类类似于 Windows `CRITICAL_SECTION`结构, 因为它只能由一个进程的线程使用。 有关 Windows API 中重要部分的详细信息, 请参阅[临界区对象](/windows/win32/Sync/critical-section-objects)。

## <a name="reader_writer_lock"></a>reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)类类似于 Windows 超薄读取器/写入器 (SRW) 锁。 下表说明了相似性和差异。

|功能|`reader_writer_lock`|SRW 锁|
|-------------|--------------------------|--------------|
|非重入|是|是|
|可以将读取器升级到编写器 (升级支持)|No|No|
|可以将编写器降级到读取器 (降级支持)|No|No|
|写首选项锁|是|No|
|对编写器的 FIFO 访问|是|No|

有关 SRW 锁的详细信息, 请参阅 Platform SDK 中的[超薄读取器/写入器 (SRW) 锁](/windows/win32/sync/slim-reader-writer--srw--locks)。

## <a name="event"></a>事件

[Concurrency:: 事件类](../../parallel/concrt/reference/event-class.md)类似于未命名的 Windows 手动重置事件。 但是, 对象`event`的行为是协同的, 而 Windows 事件的行为提前。 有关 Windows 事件的详细信息, 请参阅[事件对象](/windows/win32/Sync/event-objects)。

## <a name="example"></a>示例

### <a name="description"></a>描述

为了更好地了解`event`类和 Windows 事件之间的差异, 请考虑以下示例。 此示例允许计划程序创建最多两个同时运行的任务, 然后调用两个使用`event`类和 Windows 手动重置事件的相似函数。 每个函数首先创建多个等待共享事件发出信号的任务。 然后, 每个函数都会生成运行中的任务, 然后发出事件信号。 然后, 每个函数将等待已发出信号的事件。

### <a name="code"></a>代码

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>注释

此示例将生成以下示例输出:

```Output
Cooperative event:
    Context 0: waiting on an event.
    Context 1: waiting on an event.
    Context 2: waiting on an event.
    Context 3: waiting on an event.
    Context 4: waiting on an event.
    Setting the event.
    Context 5: received the event.
    Context 6: received the event.
    Context 7: received the event.
    Context 8: received the event.
    Context 9: received the event.
Windows event:
    Context 10: waiting on an event.
    Context 11: waiting on an event.
    Setting the event.
    Context 12: received the event.
    Context 14: waiting on an event.
    Context 15: received the event.
    Context 16: waiting on an event.
    Context 17: received the event.
    Context 18: waiting on an event.
    Context 19: received the event.
    Context 13: received the event.
```

由于类`event`以协作方式进行工作, 因此当事件等待进入终止状态时, 计划程序可以将处理资源重新分配给另一个上下文。 因此, 使用`event`类的版本可以完成更多的工作。 在使用 Windows 事件的版本中, 每个等待任务都必须在下一任务开始之前进入终止状态。

有关任务的详细信息, 请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

## <a name="see-also"></a>请参阅

[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)
