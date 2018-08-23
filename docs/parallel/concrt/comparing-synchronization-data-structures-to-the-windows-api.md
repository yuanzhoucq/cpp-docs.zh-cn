---
title: 将同步数据结构与 Windows API 进行比较 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d1470911b13243a7c8b3befc627801368e89f04
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687369"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>将同步数据结构与 Windows API 进行比较
本主题比较由并发运行时与所提供的 Windows API 提供的同步数据结构的行为。  
  
 通过并发运行时提供的同步数据结构效仿*线程处理模型的协作*。 协作的线程模型，在同步基元显式产生其他线程对其处理资源。 这不同于*preemptive 线程处理模型*，其中处理资源被传输到其他线程的控制计划程序或操作系统。  
  
## <a name="criticalsection"></a>critical_section  
 [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)类类似于 Windows`CRITICAL_SECTION`结构，因为它可仅由一个进程的线程。 有关 Windows API 中的临界区的详细信息，请参阅[关键部分对象](http://msdn.microsoft.com/library/windows/desktop/ms682530)。  
  
## <a name="readerwriterlock"></a>reader_writer_lock  
 [Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)类类似于 Windows 精简读取器/编写 (SRW) 器锁。 下表说明的相似性和差异。  
  
|功能|`reader_writer_lock`|SRW 锁|  
|-------------|--------------------------|--------------|  
|非可重入|是|是|  
|可以将提升到编写器 （升级支持） 的读取器|否|否|  
|可以降级到读取器 （降级支持） 的编写器|否|否|  
|写入首选项锁|是|否|  
|编写器的先进先出访问|是|否|  
  
 有关 SRW 锁的详细信息，请参阅[精简读取器/编写器 (SRW) 锁](http://msdn.microsoft.com/library/windows/desktop/aa904937)平台 SDK 中。  
  
## <a name="event"></a>Event — 事件  
 [Concurrency:: event](../../parallel/concrt/reference/event-class.md)类类似于未命名，Windows 手动重置事件。 但是，`event`对象以协作方式工作，而 Windows 事件的行为优先。 有关 Windows 事件的详细信息，请参阅[事件对象](http://msdn.microsoft.com/library/windows/desktop/ms682655)。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 若要更好地了解之间的差异`event`类和 Windows 事件，请考虑下面的示例。 此示例将启用的计划程序创建最多两个同时进行的任务，然后两个相似函数使用的调用`event`类和 Windows 手动重置事件。 每个函数首先创建若干个任务，等待共享事件变为终止状态。 每个函数然后生成到正在运行的任务，并用信号通知事件。 每个函数然后等待已终止事件。  
  
### <a name="code"></a>代码  
 [!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]  
  
### <a name="comments"></a>注释  
 该示例产生下面的示例输出：  
  
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
  
 因为`event`类，其行为以协作方式，当事件正在等待进入终止的状态时，计划程序可以重新分配到另一个上下文的处理资源。 因此，更多的工作通过使用版本来实现`event`类。 使用 Windows 事件的版本，该下一步的任务开始之前，每个正在等待的任务必须进入终止的状态。  
  
 有关任务的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="see-also"></a>请参阅  
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)
