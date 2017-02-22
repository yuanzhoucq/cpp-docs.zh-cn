---
title: "如何：管理计划程序实例 | Microsoft Docs"
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
  - "管理计划程序实例 [并发运行时]"
  - "计划程序实例, 管理 [并发运行时]"
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：管理计划程序实例
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过使用计划程序实例，您可以将特定的计划策略与各种类型的工作负载相关联。  本主题包含两个基本示例，这些示例演示了如何创建和管理计划程序实例。  
  
 这些示例将创建使用默认计划程序策略的计划程序。  有关创建使用自定义策略的计划程序的示例，请参阅[如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
### 管理应用程序中的计划程序实例  
  
1.  创建 [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) 对象，该对象包含供计划程序使用的策略值。  
  
2.  调用 [Concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md) 方法或 [concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) 方法来创建计划程序实例。  
  
     如果您使用 `Scheduler::Create` 方法，请在需要将计划程序与当前上下文关联时调用 [concurrency::Scheduler::Attach](../Topic/Scheduler::Attach%20Method.md) 方法。  
  
3.  调用 [CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396) 函数来创建非终止的自动重置事件对象的句柄。  
  
4.  将您刚创建的事件对象的句柄传递给 [concurrency::CurrentScheduler::RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md) 方法或 [concurrency::Scheduler::RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md) 方法。  这将注册要在销毁计划程序时设置的事件。  
  
5.  执行想要当前计划程序计划的任务。  
  
6.  调用 [concurrency::CurrentScheduler::Detach](../Topic/CurrentScheduler::Detach%20Method.md) 方法，以分离当前计划程序并将以前的计划程序还原为当前计划程序。  
  
     如果您使用 `Scheduler::Create` 方法，请调用 [concurrency::Scheduler::Release](../Topic/Scheduler::Release%20Method.md) 方法以递减 `Scheduler` 对象的引用计数。  
  
7.  将事件句柄传递给 [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032) 函数以等待计划程序关闭。  
  
8.  调用 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) 函数以关闭事件对象的句柄。  
  
## 示例  
 下面的代码演示了管理计划程序实例的两种方法。  每个示例首先均使用默认计划程序来执行一项打印出当前计划程序的唯一标识符的任务。  然后，每个示例使用计划程序实例再次执行相同任务。  最后，每个示例都将默认计划程序还原为当前计划程序并再次执行该任务。  
  
 第一个示例使用 [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) 类创建计划程序实例，并将该实例与当前上下文关联。  第二个示例使用 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 类执行相同任务。  通常，`CurrentScheduler` 类用于处理当前计划程序。  如果您希望控制计划程序与当前上下文关联的时间，或者希望将特定计划程序与特定任务关联，则第二个示例（使用 `Scheduler` 类）很有用。  
  
 [!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/CPP/how-to-manage-a-scheduler-instance_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **使用CurrentScheduler 类…**   
**当前计划程序 ID:0**  
**创建和附加计划程序。**  
**当前计划程序 ID:1**  
**分离计划程序。**  
**当前计划程序 ID:0**  
**使用调度程序类。**  
**当前计划程序 ID:0**  
**创建计划程序。**  
**附加计划程序。**  
**当前计划程序 ID:2**  
**分离计划程序。**  
**当前计划程序 ID:0**   
## 编译代码  
 复制代码示例，并将此代码粘贴到 Visual Studio 项目中或一个名为 `scheduler-instance.cpp`的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc scheduler\-instance.cpp**  
  
## 请参阅  
 [计划程序实例](../../parallel/concrt/scheduler-instances.md)   
 [如何：指定特定的计划程序策略](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)