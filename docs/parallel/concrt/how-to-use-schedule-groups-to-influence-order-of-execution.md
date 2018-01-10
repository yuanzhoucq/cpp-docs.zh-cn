---
title: "如何： 使用计划组影响执行顺序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fcb37c1c14a9d09230bfa5d4fdce1da5eddfb4f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>如何：使用计划组影响执行顺序
在并发运行时，计划任务的顺序是不确定的。 但是，你可以使用计划策略影响任务运行的顺序。 本主题演示如何使用计划组连同[concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey)计划程序策略，来影响任务运行的顺序。  

  
 该示例运行一组任务两次，每个都有不同的计划策略。 这两个策略限制为两个处理资源的最大数目。 首次运行使用`EnhanceScheduleGroupLocality`策略，这是默认设置，和第二次运行使用`EnhanceForwardProgress`策略。 下`EnhanceScheduleGroupLocality`策略，计划程序运行所有任务的计划组之前每个任务完成，或者可以生成。 下`EnhanceForwardProgress`策略，计划程序将移到下一步计划组以轮循机制方式后只需一个任务完成，或生成。  
  
 当每个计划组包含相关的任务，`EnhanceScheduleGroupLocality`策略通常会导致改进性能由于任务之间保留缓存区域。 `EnhanceForwardProgress`策略使任务能够使进程向前推进，你需要跨计划组计划公平性时很有用。  
  
## <a name="example"></a>示例  
 此示例定义`work_yield_agent`类，该类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `work_yield_agent`类执行的工作单元，生成的当前上下文中，并且随后会执行另一个工作单元。 代理使用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数以协作方式，以便可以运行其他上下文让出当前上下文。  
  
 此示例将创建四个`work_yield_agent`对象。 为了说明如何设置计划程序策略，以影响代理运行的顺序，该示例将与一个计划组和其他两个代理与另一计划组关联的前两个代理。 该示例使用[concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)方法来创建[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)对象。 该示例运行所有四个代理两次，每次使用不同的计划策略。  
  
 [!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
Using EnhanceScheduleGroupLocality...  
group 0,
    task 0: first loop...  
group 0,
    task 1: first loop...  
group 0,
    task 0: waiting...  
group 1,
    task 0: first loop...  
group 0,
    task 1: waiting...  
group 1,
    task 1: first loop...  
group 1,
    task 0: waiting...  
group 0,
    task 0: second loop...  
group 1,
    task 1: waiting...  
group 0,
    task 1: second loop...  
group 0,
    task 0: finished...  
group 1,
    task 0: second loop...  
group 0,
    task 1: finished...  
group 1,
    task 1: second loop...  
group 1,
    task 0: finished...  
group 1,
    task 1: finished...  
 
Using EnhanceForwardProgress...  
group 0,
    task 0: first loop...  
group 1,
    task 0: first loop...  
group 0,
    task 0: waiting...  
group 0,
    task 1: first loop...  
group 1,
    task 0: waiting...  
group 1,
    task 1: first loop...  
group 0,
    task 1: waiting...  
group 0,
    task 0: second loop...  
group 1,
    task 1: waiting...  
group 1,
    task 0: second loop...  
group 0,
    task 0: finished...  
group 0,
    task 1: second loop...  
group 1,
    task 0: finished...  
group 1,
    task 1: second loop...  
group 0,
    task 1: finished...  
group 1,
    task 1: finished...  
```  
  
 这两个策略生成相同的事件序列。 但是，该策略，使用`EnhanceScheduleGroupLocality`启动之前启动属于第二个组的代理是第一个计划组的一部分这两个代理。 使用策略`EnhanceForwardProgress`从第一个组开始一个代理，然后启动第二个组中的第一个代理。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`scheduling-protocol.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 计划 protocol.cpp**  
  
## <a name="see-also"></a>请参阅  
 [计划组](../../parallel/concrt/schedule-groups.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)

