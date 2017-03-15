---
title: "如何：使用计划组影响执行顺序 | Microsoft Docs"
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
  - "计划组, 使用 [并发运行时]"
  - "使用计划组 [并发运行时]"
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：使用计划组影响执行顺序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在并发运行时中，计划任务的顺序是不确定的。  但是，可以使用计划策略影响任务的运行顺序。  本主题演示如何配合使用计划组与 [concurrency::SchedulingProtocol](../Topic/PolicyElementKey%20Enumeration.md) 计划程序策略来影响任务运行的顺序。  
  
 该示例对一组任务运行了两次，每次使用不同的计划策略。  这两个策略均将处理资源的最大数目限制为 2。  第一次运行使用 `EnhanceScheduleGroupLocality` 策略（默认设置），第二次运行使用 `EnhanceForwardProgress` 策略。  按照 `EnhanceScheduleGroupLocality` 策略，计划程序会运行一个计划组中的所有任务，直到每个任务完成或退出为止。  按照 `EnhanceForwardProgress` 策略，在只完成或退出一项任务后，计划程序便会以循环方式移到下一个计划组。  
  
 如果每个计划组均包含相关任务，则 `EnhanceScheduleGroupLocality` 策略通常会导致性能提高，因为任务之间保留了缓存地址。  `EnhanceForwardProgress` 策略使任务能够向前推进，在需要跨计划组计划任务的顺利执行时非常有用。  
  
## 示例  
 此示例定义派生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 的 `work_yield_agent` 的类。  `work_yield_agent` 类执行某个工作单元，退出当前上下文，然后执行另一个工作单元。  代理使用 [concurrency::wait](../Topic/wait%20Function.md) 函数以协作方式退出当前上下文，以便其他上下文可以运行。  
  
 此示例创建了四个 `work_yield_agent` 对象。  为了演示如何设置计划程序策略以影响代理运行的顺序，该示例将前两个代理与一个计划组关联，将其他两个代理与另一个计划组关联。  该示例使用 [concurrency::CurrentScheduler::CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md) 方法创建 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 对象。  该示例对所有这四个代理运行了两次，每次使用不同的计划策略。  
  
 [!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/CPP/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **使用 EnhanceScheduleGroupLocality…**  
**组 0 中，任务 0:第一个循环…**  
**组 0 中，任务 1:第一个循环…**  
**组 0 中，任务 0:等待…**  
**组 1 中，任务 0:第一个循环…**  
**组 0 中，任务 1:等待…**  
**组 1 中，任务 1:第一个循环…**  
**组 1 中，任务 0:等待…**  
**组 0 中，任务 0:然后循环…**  
**组 1 中，任务 1:等待…**  
**组 0 中，任务 1:然后循环…**  
**组 0 中，任务 0:完成…**  
**组 1 中，任务 0:然后循环…**  
**组 0 中，任务 1:完成…**  
**组 1 中，任务 1:然后循环…**  
**组 1 中，任务 0:完成…**  
**组 1 中，任务 1:完成…**  
**使用 EnhanceForwardProgress…**  
**组 0 中，任务 0:第一个循环…**  
**组 1 中，任务 0:第一个循环…**  
**组 0 中，任务 0:等待…**  
**组 0 中，任务 1:第一个循环…**  
**组 1 中，任务 0:等待…**  
**组 1 中，任务 1:第一个循环…**  
**组 0 中，任务 1:等待…**  
**组 0 中，任务 0:然后循环…**  
**组 1 中，任务 1:等待…**  
**组 1 中，任务 0:然后循环…**  
**组 0 中，任务 0:完成…**  
**组 0 中，任务 1:然后循环…**  
**组 1 中，任务 0:完成…**  
**组 1 中，任务 1:然后循环…**  
**组 0 中，任务 1:完成…**  
**组 1 中，任务 1:完成…** 这两个策略会产生相同的事件顺序。  然而，使用 `EnhanceScheduleGroupLocality` 的策略先启动均在第一个计划组中的两个代理，然后启动第二个组中的代理。  使用 `EnhanceForwardProgress` 的策略先启动第一个组中的一个代理，然后启动第二个组中的第一个代理。  
  
## 编译代码  
 复制代码示例，并将此代码粘贴到Visual Studio项目中或一个名为 `scheduling-protocol.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc scheduling\-protocol.cpp**  
  
## 请参阅  
 [计划组](../../parallel/concrt/schedule-groups.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)