---
title: 并行诊断工具（并发运行时）
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 2af1898312a4f448d618fcfc4e43ea93f5f0bc76
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346314"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>并行诊断工具（并发运行时）

Visual Studio 为调试和分析多线程应用程序提供了广泛的支持。

## <a name="debugging"></a>调试

Visual Studio 调试器包括**并行堆栈**窗口中，**并行任务**窗口中，并且**并行监视**窗口。 有关详细信息，请参见[演练：调试并行应用程序](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)和[如何：使用并行监视窗口](/visualstudio/debugger/how-to-use-the-parallel-watch-window)。

## <a name="profiling"></a>分析

分析工具提供了三个数据视图用于显示有关多线程应用程序与自身和其他程序的交互的图形、 表格和数字信息。 视图使你能够快速确定方面的问题，并导航从上到调用堆栈，该图形显示的点调用站点和源代码。 有关详细信息，请参阅[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)。

## <a name="event-tracing"></a>事件跟踪

并发运行时使用[Windows 的事件跟踪](/windows/desktop/ETW/event-tracing-portal)(ETW) 以在发生各种事件时通知检测工具，探查器，如。 这些事件包括当激活或停用计划程序时，上下文开始、 结束、 阻止、 取消阻止，或生成时, 和并行算法开始或结束时。

这样的工具[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)利用此功能; 因此，您通常不必直接使用这些事件。 但是，这些事件很有用的当你正在开发自定义探查器，或者在使用事件跟踪工具如[Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628)。

并发运行时引发这些事件仅在启用跟踪时。 调用[concurrency:: enabletracing](reference/concurrency-namespace-functions.md#enabletracing)函数来启用事件跟踪和[concurrency:: disabletracing](reference/concurrency-namespace-functions.md#disabletracing)函数表示禁用跟踪。

下表描述运行时将引发启用事件跟踪的事件：

|Event|描述|“值”|
|-----------|-----------------|-----------|
|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|并发运行时的 ETW 提供程序标识符。|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|将标记与上下文相关的事件。|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|将标记入口和出口调用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|将标记入口和出口调用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法。|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|将标记入口和出口调用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法。|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|将标记与相关的事件[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|将标记与虚拟处理器相关的事件。|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

并发运行时定义，但目前不引发，以下事件。 在运行时保留供将来使用这些事件：

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

[Concurrency:: concrt_eventtype](reference/concurrency-namespace-enums.md#concrt_eventtype)枚举指定可能的操作事件跟踪。 例如，在的 entrance`parallel_for`算法，运行时将引发`PPLParallelForEventGuid`事件，并提供`CONCRT_EVENT_START`的操作。 之前`parallel_for`算法返回，则运行时再次引发`PPLParallelForEventGuid`事件，并提供`CONCRT_EVENT_END`的操作。

下面的示例演示如何启用跟踪对的调用`parallel_for`。 在运行时不会跟踪对的第一个调用`parallel_for`因为它没有启用跟踪。 在调用`EnableTracing`运行时将能够跟踪对的第二个调用`parallel_for`。

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

在运行时跟踪的调用次数`EnableTracing`和`DisableTracing`。 因此，如果您调用`EnableTracing`多次，则必须调用`DisableTracing`相同数量的次数才能禁用跟踪。

## <a name="see-also"></a>请参阅

[并发运行时](../../parallel/concrt/concurrency-runtime.md)
