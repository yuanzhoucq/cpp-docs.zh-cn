---
title: "并行诊断工具（并发运行时） | Microsoft Docs"
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
  - "并行诊断工具 [并发运行时]"
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 并行诊断工具（并发运行时）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 为调试和分析多线程应用程序提供了广泛的支持。  
  
## 调试  
 Visual Studio 调试器包括"并行堆栈"  窗口，"并行任务" 窗口和 "并行监视" 窗口。  有关更多信息，请参见[演练：调试并行应用程序](../Topic/Walkthrough:%20Debugging%20a%20Parallel%20Application.md)和[如何：使用“并行监视”窗口](../Topic/How%20to:%20Use%20the%20Parallel%20Watch%20Window.md)。  
  
## 分析  
 提供三种数据视图分析工具，用于显示有关多线程应用程序如何与自身和其他程序交互的图形、表格和数字信息。  利用这些视图，可以快速标识关注区域，并从图形显示上的点导航到调用堆栈、调用站点和源代码。  有关详细信息，请参阅[并发可视化工具](../Topic/Concurrency%20Visualizer.md)。  
  
## 事件跟踪  
 在发生各种事件时，并发运行时会使用 [Windows 事件跟踪](http://msdn.microsoft.com/library/windows/desktop/bb968803) \(ETW\) 来通知检测工具（如探查器）。  这些事件包括在激活或禁用计划程序时，在上下文开始、结束、停滞、恢复运行或让步时以及在并行算法开始或结束时。  
  
 [并发可视化工具](../Topic/Concurrency%20Visualizer.md)等工具利用了此功能；因此，您通常不必直接处理这些事件。  但是，如果您开发自定义探查器或使用事件跟踪工具，如 [Xperf](http://go.microsoft.com/fwlink/?LinkID=160628)，则这些事件很有用。  
  
 并发运行时仅在启用跟踪功能时才引发这些事件。  调用 [concurrency::EnableTracing](../Topic/EnableTracing%20Function.md) 函数可启用事件跟踪，调用 [concurrency::DisableTracing](../Topic/DisableTracing%20Function.md) 函数可禁用跟踪。  
  
 下表介绍了在启用事件跟踪时运行时引发的事件。  
  
|Event|说明|值|  
|-----------|--------|-------|  
|[concurrency::ConcRT\_ProviderGuid](../Topic/ConcRT_ProviderGuid%20Constant.md)|并发运行时的 ETW 提供程序标识符。|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[concurrency::ContextEventGuid](../Topic/ContextEventGuid%20Constant.md)|标记与上下文相关的事件。|`5727a00f-50be-4519-8256-f7699871fecb`|  
|[concurrency::PPLParallelForEventGuid](../Topic/PPLParallelForEventGuid%20Constant.md)|标记调用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法的入口和出口。|`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[concurrency::PPLParallelForeachEventGuid](../Topic/PPLParallelForeachEventGuid%20Constant.md)|标记调用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 算法的入口和出口。|`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[concurrency::PPLParallelInvokeEventGuid](../Topic/PPLParallelInvokeEventGuid%20Constant.md)|标记调用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 算法的入口和出口。|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[concurrency::SchedulerEventGuid](../Topic/SchedulerEventGuid%20Constant.md)|标记与[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)相关的事件。|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[concurrency::VirtualProcessorEventGuid](../Topic/VirtualProcessorEventGuid%20Constant.md)|标记与虚拟处理器相关的事件。|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 并发运行时定义但目前不引发以下事件。  运行时保留了这些事件以便将来使用：  
  
-   [concurrency::ConcRTEventGuid](../Topic/ConcRTEventGuid%20Constant.md)  
  
-   [concurrency::ScheduleGroupEventGuid](../Topic/SchedulerEventGuid%20Constant.md)  
  
-   [concurrency::ChoreEventGuid](../Topic/ChoreEventGuid%20Constant.md)  
  
-   [concurrency::LockEventGuid](../Topic/LockEventGuid%20Constant.md)  
  
-   [concurrency::ResourceManagerEventGuid](../Topic/ResourceManagerEventGuid%20Constant.md)  
  
 [concurrency::ConcRT\_EventType](../Topic/ConcRT_EventType%20Enumeration.md) 枚举指定事件跟踪的可能操作。  例如，在 `parallel_for` 算法的入口，运行时会引发 `PPLParallelForEventGuid` 事件并提供 `CONCRT_EVENT_START` 作为操作。  在 `parallel_for` 算法返回以前，运行时会再次引发 `PPLParallelForEventGuid` 事件并提供 `CONCRT_EVENT_END` 作为操作。  
  
 以下示例说明如何为针对 `parallel_for` 的调用启用跟踪。  运行时不跟踪对 `parallel_for` 的第一次调用，因为它没有启用跟踪。  调用 `EnableTracing` 可使运行时跟踪对 `parallel_for` 的第二次调用。  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/CPP/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 运行时会跟踪您调用 `EnableTracing` 和 `DisableTracing` 的次数。  因此，如果您多次调用 `EnableTracing`，则必须调用 `DisableTracing` 相同的次数才能禁用跟踪。  
  
## 请参阅  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)