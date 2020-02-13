---
title: 如何：使用计划组影响执行顺序
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
ms.openlocfilehash: 84829664603999893f32caab39af250059bf9788
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141921"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>如何：使用计划组影响执行顺序

在并发运行时中，计划任务的顺序是不确定的。 但是，您可以使用计划策略来影响运行任务的顺序。 本主题说明如何结合使用 schedule 组和[concurrency：： SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey)计划程序策略来影响任务的运行顺序。

此示例运行两次任务集，每个任务都有不同的计划策略。 这两个策略都将处理资源的最大数目限制为两个。 第一次运行使用 `EnhanceScheduleGroupLocality` 策略，默认情况下，第二次运行使用 `EnhanceForwardProgress` 策略。 在 `EnhanceScheduleGroupLocality` 策略下，计划程序将在一个计划组中运行所有任务，直到每个任务完成或生成。 在 `EnhanceForwardProgress` 策略下，计划程序将在一个任务完成或生成后按轮循机制转移到下一个计划组。

当每个计划组包含相关任务时，`EnhanceScheduleGroupLocality` 策略通常会提高性能，因为在任务之间保留缓存区域。 当你需要跨计划组计划公平时，`EnhanceForwardProgress` 策略可使任务前进进度并非常有用。

## <a name="example"></a>示例

此示例定义派生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)的 `work_yield_agent` 类。 `work_yield_agent` 类执行工作单元，生成当前上下文，然后执行另一个工作单元。 代理使用[concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函数以协作方式生成当前上下文，以便其他上下文可以运行。

此示例将创建四个 `work_yield_agent` 的对象。 为了说明如何设置计划程序策略来影响代理运行的顺序，该示例将前两个代理与一个计划组以及另一个具有其他计划组的代理关联起来。 该示例使用[concurrency：： CurrentScheduler：： CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)方法创建[Concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)对象。 此示例使用不同的计划策略，每次运行四个代理两次。

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

这两个策略生成的事件序列相同。 但是，在启动第二组中的代理之前，使用 `EnhanceScheduleGroupLocality` 的策略会启动属于第一个计划组的代理。 使用 `EnhanceForwardProgress` 的策略从第一个组中启动一个代理，然后启动第二个组中的第一个代理。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `scheduling-protocol.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc scheduling-protocol**

## <a name="see-also"></a>另请参阅

[计划组](../../parallel/concrt/schedule-groups.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)
