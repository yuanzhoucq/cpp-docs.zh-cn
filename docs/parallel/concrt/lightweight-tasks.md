---
title: "轻量级任务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9b9caa028d7f870ecdd6c67503c6bc9448cff1d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="lightweight-tasks"></a>轻量级任务
本文档介绍并发运行时中的轻量任务的角色。 A*轻量级任务*是直接从计划的任务`concurrency::Scheduler`或`concurrency::ScheduleGroup`对象。 轻量级任务类似于对 Windows API 提供的函数[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函数。 因此，轻量级任务非常有用，当改编现有代码以使用并发运行时的计划功能时。 并发运行时本身使用轻量任务来计划异步代理和之间异步消息块发送消息。  
  
> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序有助于细微调整你的应用程序的性能，我们建议你开始使用[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)如果你是新的并发运行。  
  
 轻量任务所需的开销小于异步代理和任务组。 例如，运行时不会通知你在轻量级任务完成后。 此外，运行时不会捕捉或处理从轻量级任务引发的异常。 有关异常处理和轻量级任务的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 对于大多数任务，我们建议使用更强大的功能，如任务组和并行算法因为它们可让你更轻松地为更基本的中断复杂的任务。 有关任务组的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 有关并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 若要创建轻量级任务，请调用[concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask)， [:: scheduletask](reference/currentscheduler-class.md#scheduletask)，或[concurrency::Scheduler::ScheduleTask](reference/scheduler-class.md#scheduletask)方法。 若要等待轻量级任务完成，请等待父计划程序以便关闭或使用同步机制，如[concurrency:: event](../../parallel/concrt/reference/event-class.md)对象。  
  
## <a name="example"></a>示例  
 有关演示如何改编现有代码以使用轻量级任务示例，请参阅[演练： 调整现有代码，以便使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [演练：调整现有代码以使用轻量级任务](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

