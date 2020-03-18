---
title: 并发命名空间枚举
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: 716c2d03e6d1ff67566bd28e5931996ea2d400af
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427451"
---
# <a name="concurrency-namespace-enums"></a>并发命名空间枚举

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status"></a>agent_status 枚举

`agent` 的有效状态。

```cpp
enum agent_status;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`agent_canceled`|已取消 `agent`。|
|`agent_created`|`agent` 已创建但尚未启动。|
|`agent_done`|`agent` 完成，但未取消。|
|`agent_runnable`|`agent` 已启动，但未进入其 `run` 方法。|
|`agent_started`|已开始 `agent`。|

### <a name="remarks"></a>备注

有关详细信息，请参阅[异步代理](../../../parallel/concrt/asynchronous-agents.md)。

### <a name="requirements"></a>要求

**标头：** concrt

## <a name="agents_eventtype"></a>Agents_EventType 枚举

可以使用代理库提供的跟踪功能进行跟踪的事件的类型

```cpp
enum Agents_EventType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|表示对象创建的事件类型|
|`AGENTS_EVENT_DESTROY`|表示对象删除的事件类型|
|`AGENTS_EVENT_END`|表示某些处理过程结束的事件类型|
|`AGENTS_EVENT_LINK`|表示消息块链接的事件类型|
|`AGENTS_EVENT_NAME`|表示对象名称的类型事件|
|`AGENTS_EVENT_SCHEDULE`|表示进程计划的事件类型|
|`AGENTS_EVENT_START`|表示某些处理过程启动的事件类型|
|`AGENTS_EVENT_UNLINK`|表示取消消息块链接的事件类型|

### <a name="requirements"></a>要求

**标头：** concrt

## <a name="concrt_eventtype"></a>ConcRT_EventType 枚举

可以使用并发运行时提供的跟踪功能进行跟踪的事件的类型。

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|表示附加到计划程序的操作的事件类型。|
|`CONCRT_EVENT_BLOCK`|表示上下文阻塞行为的事件类型。|
|`CONCRT_EVENT_DETACH`|表示从计划程序分离的行为的事件类型。|
|`CONCRT_EVENT_END`|标记开始/结束事件对开头的事件类型。|
|`CONCRT_EVENT_GENERIC`|用于杂项事件的事件类型。|
|`CONCRT_EVENT_IDLE`|表示上下文变为空闲状态的行为的事件类型。|
|`CONCRT_EVENT_START`|标记开始/结束事件对开头的事件类型。|
|`CONCRT_EVENT_UNBLOCK`|表示取消阻塞上下文操作的事件类型。|
|`CONCRT_EVENT_YIELD`|表示上下文生成行为的事件类型。|

### <a name="requirements"></a>要求

**标头：** Concrt**命名空间：** 并发

## <a name="concrt_traceflags"></a>Concrt_TraceFlags 枚举

事件类型的跟踪标志

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>要求

**标头：** concrt

## <a name="criticalregiontype"></a>CriticalRegionType 枚举

上下文位于其中的关键区域的类型。

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`InsideCriticalRegion`|指示上下文位于关键区域内。 在关键区域内部，将对计划程序隐藏异步挂起。 如果发生这种挂起，资源管理器将等待线程变为可运行，并直接恢复，而不是重新调用计划程序。 在此类区域中执行的任何锁都必须特别小心。|
|`InsideHyperCriticalRegion`|指示上下文位于超关键区域内。 在超关键区域内，同步和异步挂起都将隐藏在计划程序中。 如果发生此类挂起或阻塞，资源管理器将等待线程变为可运行，并直接恢复，而不是重新调用计划程序。 在此类区域中执行的锁定不得与在此类区域外部运行的代码共享。 这样做将导致不可预知的死锁。|
|`OutsideCriticalRegion`|指示上下文超出任何关键区域。|

### <a name="requirements"></a>要求

**标头：** concrtrm。h

## <a name="dynamicprogressfeedbacktype"></a>DynamicProgressFeedbackType 枚举

由 `DynamicProgressFeedback` 策略用于描述重新平衡计划程序资源的依据是从计划程序收集的统计信息，还是通过对 `Activate` 接口上的 `Deactivate` 和 `IVirtualProcessorRoot` 方法进行调用以进出空闲状态的虚拟处理器。 有关可用计划程序策略的详细信息，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`ProgressFeedbackDisabled`|计划程序不收集进度信息。 重新平衡只是根据基础硬件线程的订阅级别进行的。 有关订阅级别的详细信息，请参阅[IExecutionResource：： CurrentSubscriptionLevel](IExecutionResource-structure.md)。<br /><br /> 此值保留供运行时使用。|
|`ProgressFeedbackEnabled`|计划程序收集进度信息，并将其传递给资源管理器。 资源管理器将利用这一统计信息，代表计划程序以及基础硬件线程的订阅级别重新平衡资源。 有关订阅级别的详细信息，请参阅[IExecutionResource：： CurrentSubscriptionLevel](IExecutionResource-structure.md)。|

## <a name="join_type"></a>join_type 枚举

`join` 消息块的类型。

```cpp
enum join_type;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`greedy`|贪婪 `join` 消息块在传播时立即接受消息。 这种做法更为有效，但根据网络配置的不同，可能会发生实时锁定。|
|`non_greedy`|非贪婪 `join` 消息传送块推迟消息，并在所有消息都到达后尝试使用它们。 这些保证可以正常工作，但速度更慢。|

### <a name="requirements"></a>要求

**标头：** agents.h

## <a name="message_status"></a>message_status 枚举

`message` 对象的内容到块的有效响应。

```cpp
enum message_status;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`accepted`|目标已接受消息。|
|`declined`|目标不接受消息。|
|`missed`|目标尝试接受该消息，但该消息不再可用。|
|`postponed`|目标已推迟消息。|

### <a name="requirements"></a>要求

**标头：** agents.h

## <a name="policyelementkey"></a>PolicyElementKey 枚举

描述计划程序行为各个方面的策略键。 每个策略元素由一个键值对描述。 有关计划程序策略及其对计划程序的影响的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`ContextPriority`|计划程序中每个上下文的操作系统线程的优先级。 如果将此项设置为值 `INHERIT_THREAD_PRIORITY` 则计划程序中的上下文将继承创建计划程序的线程的优先级。<br /><br /> 有效值： Windows `SetThreadPriority` 函数和特殊值的任何有效值 `INHERIT_THREAD_PRIORITY`<br /><br /> 默认值： `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|计划程序中每个上下文的保留堆栈大小（kb）。<br /><br /> 有效值：正整数<br /><br /> 默认值： `0`，指示使用进程的堆栈大小默认值。|
|`DynamicProgressFeedback`|确定计划程序的资源是根据从计划程序收集的统计信息重新平衡，还是仅基于基础硬件线程的订阅级别。 有关详细信息，请参阅[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)。<br /><br /> 有效值： `DynamicProgressFeedbackType` 枚举的成员（`ProgressFeedbackEnabled` 或 `ProgressFeedbackDisabled`<br /><br /> 默认值： `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|将 `SchedulingProtocol` 策略密钥设置为 `EnhanceScheduleGroupLocality`值时，这将指定允许在每个虚拟处理器本地队列中缓存的可运行上下文的最大数目。 此类上下文通常会在导致它们变为可运行的虚拟处理器上按后进先出（LIFO）顺序运行。 请注意，当 `SchedulingProtocol` 项设置为 `EnhanceForwardProgress`值时，此策略项没有任何意义。<br /><br /> 有效值：非负整数<br /><br /> 默认值： `8`|
|`MaxConcurrency`|计划程序所需的最大并发级别。 资源管理器将首先尝试分配此多个虚拟处理器。 特殊值[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)指示所需的并发级别与计算机上的硬件线程数相同。 如果为 `MinConcurrency` 指定的值大于计算机上的硬件线程数，并且 `MaxConcurrency` 指定为 `MaxExecutionResources`，则将引发 `MaxConcurrency` 的值以匹配为 `MinConcurrency`设置的值。<br /><br /> 有效值：正整数和特殊值 `MaxExecutionResources`<br /><br /> 默认值： `MaxExecutionResources`|
|`MaxPolicyElementKey`|最大策略元素键。 不是有效的元素键。|
|`MinConcurrency`|资源管理器必须向计划程序提供的最低并发级别。 分配给计划程序的虚拟处理器的数目永远不会低于最小值。 特殊值[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)指示最低并发级别与计算机上的硬件线程数相同。 如果为 `MaxConcurrency` 指定的值小于计算机上的硬件线程数，并且 `MinConcurrency` 指定为 `MaxExecutionResources`，则 `MinConcurrency` 的值会降低，以匹配为 `MaxConcurrency`设置的值。<br /><br /> 有效值：非负整数和特殊值 `MaxExecutionResources`。 请注意，对于用于并发运行时计划程序构造的计划程序策略，值 `0` 无效。<br /><br /> 默认值： `1`|
|`SchedulerKind`|计划程序将对基础执行上下文使用的线程类型。 有关详细信息，请参阅[SchedulerType](#schedulertype)。<br /><br /> 有效值：枚举 `SchedulerType` 的成员，例如 `ThreadScheduler`<br /><br /> 默认值： `ThreadScheduler`。 这会在所有操作系统上转换为 Win32 线程。|
|`SchedulingProtocol`|描述计划程序将使用的计划算法。 有关详细信息，请参阅[SchedulingProtocolType](#schedulingprotocoltype)。<br /><br /> 有效值： `SchedulingProtocolType` 枚举的成员（`EnhanceScheduleGroupLocality` 或 `EnhanceForwardProgress`<br /><br /> 默认值： `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|暂定每个硬件线程的虚拟处理器数。 如果必要，资源管理器可以增加目标过度订阅因素，以满足计算机上硬件线程的 `MaxConcurrency`。<br /><br /> 有效值：正整数<br /><br /> 默认值： `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>要求

**标头：** concrt

## <a name="schedulertype"></a>SchedulerType 枚举

由 `SchedulerKind` 策略用于描述应由计划程序用于基础执行上下文的线程的类型。 有关可用计划程序策略的详细信息，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum SchedulerType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`ThreadScheduler`|指示常规 Win32 线程的显式请求。|
|`UmsThreadDefault`|Visual Studio 2013 中的并发运行时不支持用户模式计划（UMS）线程。 使用 `UmsThreadDefault` 作为 `SchedulerType` 策略的一个值不会导致错误。 不过，通过此策略创建的计划程序将默认使用 Win32 线程。|

### <a name="requirements"></a>要求

**标头：** concrt

## <a name="schedulingprotocoltype"></a>SchedulingProtocolType 枚举

由 `SchedulingProtocol` 策略用于描述将哪个计划算法用于计划程序。 有关可用计划程序策略的详细信息，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`EnhanceForwardProgress`|计划程序优先于执行每个任务后通过计划组执行循环。 未阻止的上下文通常按先进先出（FIFO）方式计划。 虚拟处理器不缓存未阻止的上下文。|
|`EnhanceScheduleGroupLocality`|计划程序在移动到另一个计划组之前，更倾向于继续处理当前计划组中的任务。 不受阻止的上下文按虚拟处理器进行缓存，并且通常按其解除阻止的虚拟处理器按后进先出（LIFO）方式计划。|

### <a name="requirements"></a>要求

**标头：** concrt

## <a name="switchingproxystate"></a>SwitchingProxyState 枚举

用于表示线程代理在执行另一个线程代理的协作上下文切换时所处的状态。

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`Blocking`|指示调用线程以协作方式阻止，应以独占方式由调用方拥有，直到再次运行并执行其他操作。|
|`Idle`|指示计划程序不再需要调用线程，并且该线程正在返回到资源管理器。 资源管理器无法再利用正在调度的上下文。|
|`Nesting`|指示调用线程嵌套子计划程序并需要调用方，以便附加到不同的计划程序。|

### <a name="remarks"></a>备注

`SwitchingProxyState` 的类型的参数传递给方法 `IThreadProxy::SwitchTo`，指示资源管理器如何处理正在进行调用的线程代理。

有关如何使用此类型的详细信息，请参阅[IThreadProxy：： SwitchTo](ithreadproxy-structure.md#switchto)。

## <a name="task_group_status"></a>task_group_status 枚举

描述 `task_group` 或 `structured_task_group` 对象的执行状态。 此类型的值是由很多等待安排到一个任务组中的任务完成的方法返回的。

```cpp
enum task_group_status;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`canceled`|`task_group` 或 `structured_task_group` 对象已取消。 一个或多个任务可能未执行。|
|`completed`|排入 `task_group` 或 `structured_task_group` 对象的任务已成功完成。|
|`not_complete`|排入 `task_group` 对象的任务尚未完成。 请注意，此值目前不是由并发运行时返回的。|

### <a name="requirements"></a>要求

**标头：** pplinterface。h

## <a name="winrtinitializationtype"></a>WinRTInitializationType 枚举

由 `WinRTInitialization` 策略用于描述，对于在 Windows 8 或更高版本的操作系统上运行的应用程序，是否以及如何在计划程序的线程上初始化 Windows 运行时。 有关可用计划程序策略的详细信息，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`DoNotInitializeWinRT`|当应用程序在 Windows 8 或更高版本的操作系统上运行时，计划程序中的线程不会初始化 Windows 运行时。|
|`InitializeWinRTAsMTA`|当应用程序在 Windows 8 或更高版本的操作系统上运行时，计划程序中的每个线程都将初始化 Windows 运行时并声明它是多线程单元的一部分。|

## <a name="requirements"></a>要求

**标头：** concrt

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
