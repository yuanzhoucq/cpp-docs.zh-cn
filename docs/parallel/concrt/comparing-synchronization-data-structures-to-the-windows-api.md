---
title: "将同步数据结构与 Windows API 进行比较 | Microsoft Docs"
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
  - "同步数据结构, 与 Windows API 比较"
  - "event 类, 示例"
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 将同步数据结构与 Windows API 进行比较
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题将并发运行时提供的同步数据结构的行为与 Windows API 提供的同步数据结构的行为进行比较。  
  
 并发运行时提供的同步数据结构效仿协作式线程模型。  在协作式线程模型中，同步基元将其处理资源显式让给其他线程。  这不同于抢先式线程模型，在该模型中，处理资源由控制计划程序或操作系统传输给其他线程。  
  
## critical\_section  
 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 类与 Windows `CRITICAL_SECTION` 结构类似，因为它只能由一个进程的线程使用。  有关 Windows API 中的临界区的更多信息，请参见[临界区对象](http://msdn.microsoft.com/library/windows/desktop/ms682530)。  
  
## reader\_writer\_lock  
 [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 类与 Windows 轻量级读\/写 \(SRW\) 锁类似。  下表说明了一些相似性和差异。  
  
|功能|`reader_writer_lock`|SRW 锁|  
|--------|--------------------------|-----------|  
|非重入|是|是|  
|可以将读取器升级为编写器（升级支持）|否|否|  
|可以将编写器降级为读取器（降级支持）|否|否|  
|写优先锁|是|否|  
|FIFO 方式访问编写器|是|否|  
  
 有关 SRW 锁的更多信息，请参见平台 SDK 中的[轻量级读取器\/编写器 \(SRW\) 锁](http://msdn.microsoft.com/library/windows/desktop/aa904937)。  
  
## event  
 [concurrency::event](../../parallel/concrt/reference/event-class.md) 类与未命名的 Windows 手动重置事件类似。  但是，`event` 对象以协作方式工作，而 Windows 事件以抢先式方式工作。  有关 Windows 事件的更多信息，请参见[事件对象](http://msdn.microsoft.com/library/windows/desktop/ms682655)。  
  
## 示例  
  
### 说明  
 为了更好地了解 `event` 类和 Windows 事件之间的区别，请考虑下面的示例。  本示例使计划程序最多能够创建两个同时发生的任务，然后调用使用 `event` 类和 Windows 手动重置事件的两个相似函数。  每个函数首先创建一些等待共享事件变为终止状态的任务。  接着，每个函数让位于正在运行的任务，并用信号通知该事件。  然后，每个函数将等待终止的事件。  
  
### 代码  
 [!CODE [concrt-event-comparison#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-event-comparison#1)]  
  
### 注释  
 此示例产生下面的示例输出：  
  
  **协作事件：**  
 **上下文 0:等待事件。**  
 **上下文 1:等待事件。**  
 **上下文 2:等待事件。**  
 **上下文 3:等待事件。**  
 **上下文 4:等待事件。**  
 **设置事件。**  
 **上下文 5:接收事件。**  
 **上下文 6:接收事件。**  
 **上下文 7:接收事件。**  
 **上下文 8:接收事件。**  
 **上下文 9:接收事件。**  
**Windows 事件**  
 **上下文 10:等待事件。**  
 **上下文 11:等待事件。**  
 **设置事件。**  
 **上下文 12:接收事件。**  
 **上下文 14:等待事件。**  
 **上下文 15:接收事件。**  
 **上下文 16:等待事件。**  
 **上下文 17:接收事件。**  
 **上下文 18:等待事件。**  
 **上下文 19:接收事件。**  
 **上下文 13:接收事件。** 因为 `event` 类以协作方式工作，所以当事件等待进入终止状态时，计划程序可以将处理资源重新分配给另一个上下文。  因此，使用 `event` 类的版本将完成更多的工作。  在使用 Windows 事件的版本中，每个正在等待的任务必须进入终止状态，下一个任务才能开始。  
  
 有关任务的更多信息，请参见 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## 请参阅  
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)   
 [关键代码段对象](http://msdn.microsoft.com/library/windows/desktop/ms682530)   
 [亭亭玉立的读取器\/编写器锁 \(SRW\)](http://msdn.microsoft.com/library/windows/desktop/aa904937)   
 [事件对象](http://msdn.microsoft.com/library/windows/desktop/ms682655)