---
title: "并行诊断工具 （并发运行时） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a7c6aa769faaacd128bb51a422227230fa4a851
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>并行诊断工具（并发运行时）
[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 为调试和分析多线程应用程序提供了广泛的支持。  
  
## <a name="debugging"></a>调试  
 Visual Studio 调试器包括**并行堆栈**窗口中，**并行任务**窗口中，和**并行监视**窗口。 有关详细信息，请参阅[演练： 调试并行应用程序](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)和[如何： 使用并行监视窗口](/visualstudio/debugger/how-to-use-the-parallel-watch-window)。  
  
## <a name="profiling"></a>分析  
 分析工具提供三个数据视图，用于显示有关多线程应用程序如何与自身和其他程序交互的图形、 表格和数字信息。 视图使你能够快速识别问题的区域和从上到调用堆栈，该图形显示点导航调用站点和源代码。 有关详细信息，请参阅[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)。  
  
## <a name="event-tracing"></a>事件跟踪  
 并发运行时使用[Windows 事件跟踪](http://msdn.microsoft.com/library/windows/desktop/bb968803)(ETW) 以各种事件发生时通知检测工具，例如探查器。 这些事件包括时计划程序是激活或停用、 时上下文开始、 结束、 阻止、 取消阻止，或生成，和并行算法开始或结束时。  
  
 这样的工具[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)利用此功能; 因此，你通常不必直接使用这些事件。 但是，这些事件非常有用的当你正在开发自定义的探查器，或者在使用事件的跟踪工具如[Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628)。  
  
 并发运行时引发这些事件仅在启用跟踪时。 调用[concurrency:: enabletracing](reference/concurrency-namespace-functions.md#enabletracing)函数可启用事件跟踪和[concurrency:: disabletracing](reference/concurrency-namespace-functions.md#disabletracing)函数可禁用跟踪。  
  
 下表说明的事件，当启用事件跟踪时，会引发运行时：  
  
|事件|描述|“值”|  
|-----------|-----------------|-----------|  

|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|并发运行时的 ETW 提供程序标识符。 |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|标记与上下文相关的事件。 |`5727a00f-50be-4519-8256-f7699871fecb`|  
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|将标记入口和出口调用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。 |`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|将标记入口和出口调用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法。 |`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|将标记入口和出口调用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法。 |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|标记与相关的事件[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|标记与虚拟处理器相关的事件。 |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 并发运行时定义，但目前不引发，以下事件。 运行时保留供将来使用这些事件：  
  
-   [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)  
  
-   [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)  
  
-   [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)  
  
-   [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)  
  
-   [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)  
  
 [Concurrency:: concrt_eventtype](reference/concurrency-namespace-enums.md#concrt_eventtype)枚举指定事件跟踪的可能操作。 例如，在的入口`parallel_for`算法，则运行时引发`PPLParallelForEventGuid`事件，并提供`CONCRT_EVENT_START`作为该操作。 之前`parallel_for`算法返回，则运行时再次引发`PPLParallelForEventGuid`事件，并提供`CONCRT_EVENT_END`作为该操作。  
  
 下面的示例演示如何启用针对调用的跟踪`parallel_for`。 运行时不会跟踪首次调用`parallel_for`因为它没有启用跟踪。 调用`EnableTracing`运行时将能够跟踪到第二个调用`parallel_for`。  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 运行时跟踪的调用的次数`EnableTracing`和`DisableTracing`。 因此，如果调用`EnableTracing`多次，必须调用`DisableTracing`为了禁用跟踪相同次数。  
  
## <a name="see-also"></a>请参阅  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)

