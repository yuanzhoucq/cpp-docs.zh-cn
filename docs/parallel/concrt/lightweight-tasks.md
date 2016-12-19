---
title: "轻量级任务 | Microsoft Docs"
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
  - "轻量级任务"
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
caps.latest.revision: 7
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 轻量级任务
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍并发运行时中轻量级任务的作用。  轻量级任务是直接从 `concurrency::Scheduler` 或 `concurrency::ScheduleGroup` 对象计划的任务。  轻量级任务类似于您提供给 Windows API [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函数的函数.  因此，当改编现有代码以使用并发运行时的计划功能时，轻量级任务非常有用。  并发运行时本身使用轻量级任务来计划异步代理和在异步消息块之间发送消息。  
  
> [!TIP]
>  并发运行时提供默认的计划程序，因此您不需要在应用程序中再创建一个计划程序。  由于任务计划程序可帮助您优化应用程序的性能，因此，如果您初次接触并发运行时，则建议您先使用 [并行模式库 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
 轻量级任务的系统开销比异步代理和任务组的系统开销小。  例如，运行时在轻量级任务完成时不通知您。  另外，运行时不会捕捉或处理轻量级任务引发的异常。  有关异常处理和轻量级任务的更多信息，请参见[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 对于大多数任务，建议使用更强大的功能（如任务组和并行算法），因为它们使您可以更轻松地将复杂任务拆分为更基本的任务。  有关任务组的更多信息，请参见[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  有关并行算法的更多信息，请参见[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 若要创建轻量级任务，请调用 [concurrency::ScheduleGroup::ScheduleTask](../Topic/ScheduleGroup::ScheduleTask%20Method.md)、[concurrency::CurrentScheduler::ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md) 或 [concurrency::Scheduler::ScheduleTask](../Topic/Scheduler::ScheduleTask%20Method.md) 方法。  若要等待轻量级任务完成，请等待父计划程序以便关闭或使用同步机制，如 [concurrency::event](../../parallel/concrt/reference/event-class.md) 对象。  
  
## 示例  
 有关演示如何改编现有代码以使用轻量级任务的示例，请参见[演练：调整现有代码以使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)。  
  
## 请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [演练：调整现有代码以使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)