---
title: 并行诊断工具（并发运行时）
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 34b2421dfc53deeb35dcc659a8d555983e583737
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510499"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>并行诊断工具（并发运行时）

Visual Studio 为调试和分析多线程应用程序提供了广泛的支持。

## <a name="debugging"></a>调试

Visual Studio 调试器包括 "**并行堆栈**" 窗口、"**并行任务**" 窗口和 "**并行监视**" 窗口。 有关详细信息，请参见[演练：调试并行应用程序](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)和[如何:使用 "并行监视"](/visualstudio/debugger/how-to-use-the-parallel-watch-window)窗口。

## <a name="profiling"></a>分析

分析工具提供了三个数据视图, 可显示有关多线程应用程序如何与自身交互以及与其他程序交互的图形、表格和数字信息。 利用这些视图, 您可以快速确定需要关注的区域, 并从图形显示器上的点导航到调用堆栈、调用站点和源代码。 有关详细信息，请参阅[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)。

## <a name="event-tracing"></a>事件跟踪

并发运行时使用[Windows 事件跟踪](/windows/win32/ETW/event-tracing-portal)(ETW) 在发生各种事件时通知检测工具 (如探查器)。 这些事件包括当激活或停用计划程序、上下文开始、结束、阻止、取消阻止或生成时, 以及并行算法开始或结束的时间。

[并发可视化](/visualstudio/profiling/concurrency-visualizer)工具等工具利用此功能;因此, 您通常不需要直接处理这些事件。 但是, 当你在开发自定义探查器时, 或使用事件跟踪工具 (如[Xperf](https://go.microsoft.com/fwlink/p/?linkid=160628)) 时, 这些事件非常有用。

仅当启用跟踪时, 并发运行时才会引发这些事件。 调用[concurrency:: EnableTracing](reference/concurrency-namespace-functions.md#enabletracing)函数可启用事件跟踪, 使用[Concurrency::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing)函数来禁用跟踪。

下表介绍了启用事件跟踪时运行时引发的事件:

|Event|描述|值|
|-----------|-----------------|-----------|
|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|并发运行时的 ETW 提供程序标识符。|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|标记与上下文相关的事件。|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|标记进入和退出以调用[concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|标记进入和退出以调用[concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法。|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|标记进入和退出以调用[concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法。|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|标记与[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)相关的事件。|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|标记与虚拟处理器相关的事件。|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

并发运行时定义但目前并未引发以下事件。 运行时保留这些事件以供将来使用:

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

[Concurrency:: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype)枚举指定事件跟踪的可能操作。 例如, 在`parallel_for`算法进入时, 运行时将`PPLParallelForEventGuid`引发事件, 并以操作的`CONCRT_EVENT_START`形式提供。 在算法返回之前, 运行时会再次`PPLParallelForEventGuid`引发事件, 并将`CONCRT_EVENT_END`其提供为操作。 `parallel_for`

下面的示例演示如何为对的调用`parallel_for`启用跟踪。 运行时不跟踪对的第一次`parallel_for`调用, 因为未启用跟踪。 对的调用`EnableTracing`使运行时能够跟踪对`parallel_for`的第二次调用。

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

运行时跟踪调用`EnableTracing`和`DisableTracing`的次数。 因此, 如果多次调用`EnableTracing` , 则必须调用`DisableTracing`相同的次数才能禁用跟踪。

## <a name="see-also"></a>请参阅

[并发运行时](../../parallel/concrt/concurrency-runtime.md)
