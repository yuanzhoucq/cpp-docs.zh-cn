---
title: 如何：使用计划组影响执行顺序
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 1117e0d24aae023fbb4dec4fbb9721e6da2ad768
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642290"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>如何：使用计划组影响执行顺序

在并发运行时，任务计划的顺序是不确定的。 但是，可以使用计划策略来影响任务的运行的顺序。 本主题演示如何使用计划组一起使用[concurrency::SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey)计划程序策略来影响任务的运行的顺序。

该示例运行一组任务两次，每个都有不同的计划策略。 这两种策略限制为两个处理资源的最大数目。 首次运行使用`EnhanceScheduleGroupLocality`策略，这是默认设置，以及第二次运行使用`EnhanceForwardProgress`策略。 下`EnhanceScheduleGroupLocality`策略，计划程序的所有任务在组中都运行一个计划之前每个任务完成或生成。 下`EnhanceForwardProgress`策略，计划程序将移到下一步计划组以轮循机制的方式的其中一个任务完成或生成后。

当计划的每个组包含相关的任务时`EnhanceScheduleGroupLocality`策略通常会提高性能由于任务之间保留缓存区域。 `EnhanceForwardProgress`策略使任务，才能使进程向前推进，您需要跨计划组的计划的公平性时很有用。

## <a name="example"></a>示例

此示例定义了`work_yield_agent`类，该类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `work_yield_agent`类执行的工作单元、 产生当前上下文，然后执行另一个工作单元。 代理使用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数让出当前上下文，以便可以运行其他上下文。

此示例创建四个`work_yield_agent`对象。 为了说明如何设置计划程序策略来影响代理的运行的顺序，该示例将与一个计划组以及与另一计划组的其他两个代理关联的前两个代理。 该示例使用[concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)方法来创建[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)对象。 此示例运行所有四个代理两次，每次使用不同的计划策略。

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

这两种策略会产生相同的事件序列。 但是，该策略，会使用`EnhanceScheduleGroupLocality`启动两个是第一个计划组的一部分，然后会启动第二个组中的代理的代理。 使用策略`EnhanceForwardProgress`从第一个组开始一个代理，然后启动第二个组中的第一个代理。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`scheduling-protocol.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 计划 protocol.cpp**

## <a name="see-also"></a>请参阅

[计划组](../../parallel/concrt/schedule-groups.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)

