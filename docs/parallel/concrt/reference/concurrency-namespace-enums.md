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
ms.openlocfilehash: e3a943ed52ce9653086203713bb98331f809314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372722"
---
# <a name="concurrency-namespace-enums"></a>并发命名空间枚举

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[临界区域类型](#criticalregiontype)|[动态进度反馈类型](#dynamicprogressfeedbacktype)|[策略元素键](#policyelementkey)|
|[计划类型](#schedulertype)|[计划协议类型](#schedulingprotocoltype)|[切换代理状态](#switchingproxystate)|
|[WinRT 初始化类型](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status-enumeration"></a><a name="agent_status"></a>agent_status枚举

`agent` 的有效状态。

```cpp
enum agent_status;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`agent_canceled`|已取消 `agent`。|
|`agent_created`|`agent`已创建但未启动。|
|`agent_done`|完成`agent`而不被取消。|
|`agent_runnable`|`agent`已启动，但未输入其`run`方法。|
|`agent_started`|已`agent`启动。|

### <a name="remarks"></a>备注

有关详细信息，请参阅[异步代理](../../../parallel/concrt/asynchronous-agents.md)。

### <a name="requirements"></a>要求

**标题：** concrt.h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType枚举

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

**标题：** concrt.h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType枚举

可以使用并发运行时提供的跟踪功能进行跟踪的事件的类型。

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|表示附加到计划程序的行为的事件类型。|
|`CONCRT_EVENT_BLOCK`|表示上下文阻止行为的事件类型。|
|`CONCRT_EVENT_DETACH`|表示从计划程序分离的行为的事件类型。|
|`CONCRT_EVENT_END`|标记开始/结束事件对开头的事件类型。|
|`CONCRT_EVENT_GENERIC`|用于杂项事件的事件类型。|
|`CONCRT_EVENT_IDLE`|表示上下文变为空闲行为的事件类型。|
|`CONCRT_EVENT_START`|标记开始/结束事件对开头的事件类型。|
|`CONCRT_EVENT_UNBLOCK`|表示取消阻止上下文的行为的事件类型。|
|`CONCRT_EVENT_YIELD`|表示上下文产生行为的事件类型。|

### <a name="requirements"></a>要求

**标题：** concrt.h**命名空间：** 并发性

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags枚举

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

**标题：** concrt.h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>临界区域类型枚举

上下文位于其中的关键区域的类型。

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`InsideCriticalRegion`|指示上下文位于关键区域内。 在关键区域内时，异步挂起会隐藏在调度程序中。 如果发生此类挂起，资源管理器将等待线程变为可运行线程，然后简单地恢复该线程，而不是再次调用计划程序。 必须极其小心地在此类区域内取下任何锁。|
|`InsideHyperCriticalRegion`|指示上下文位于超临界区域内。 在超临界区域内时，同步和异步挂起都会从计划程序隐藏。 如果发生此类挂起或阻塞，资源管理器将等待线程变为可运行线程，然后简单地恢复该线程，而不是再次调用计划程序。 在此类区域内获取的锁绝不能与在此类区域之外运行的代码共享。 这样做将导致不可预知的僵局。|
|`OutsideCriticalRegion`|指示上下文在任何关键区域之外。|

### <a name="requirements"></a>要求

**标题：** concrtrm.h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>动态进度反馈类型枚举

由 `DynamicProgressFeedback` 策略用于描述重新平衡计划程序资源的依据是从计划程序收集的统计信息，还是通过对 `IVirtualProcessorRoot` 接口上的 `Activate` 和 `Deactivate` 方法进行调用以进出空闲状态的虚拟处理器。 有关可用计划程序策略的详细信息，请参阅[策略元素键](concurrency-namespace-enums.md)。

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`ProgressFeedbackDisabled`|计划程序不收集进度信息。 重新平衡仅基于基础硬件线程的订阅级别完成。 有关订阅级别的详细信息，请参阅[I 执行资源：：当前订阅级别](IExecutionResource-structure.md)。<br /><br /> 此值保留供运行时使用。|
|`ProgressFeedbackEnabled`|计划程序收集进度信息并将其传递给资源管理器。 资源管理器将使用此统计信息代表计划程序重新平衡资源，以及基础硬件线程的订阅级别。 有关订阅级别的详细信息，请参阅[I 执行资源：：当前订阅级别](IExecutionResource-structure.md)。|

## <a name="join_type-enumeration"></a><a name="join_type"></a>join_type枚举

`join` 消息块的类型。

```cpp
enum join_type;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`greedy`|贪`join`婪的消息块在传播时立即接受消息。 这更有效，但可以进行实时锁定，具体取决于网络配置。|
|`non_greedy`|非贪婪`join`的消息块推迟消息，并尝试使用它们后，所有到达。 这些保证工作，但速度较慢。|

### <a name="requirements"></a>要求

**标头：** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a>message_status枚举

`message` 对象的内容到块的有效响应。

```cpp
enum message_status;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`accepted`|目标接受消息。|
|`declined`|目标不接受该消息。|
|`missed`|目标尝试接受该消息，但它不再可用。|
|`postponed`|目标推迟了消息。|

### <a name="requirements"></a>要求

**标头：** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a>策略元素键枚举

描述计划程序行为各个方面的策略键。 每个策略元素由一个键值对描述。 有关计划程序策略及其对计划程序的影响的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`ContextPriority`|计划程序中每个上下文的操作系统线程优先级。 如果此键设置为值`INHERIT_THREAD_PRIORITY`，则计划程序中的上下文将继承创建计划程序的线程的优先级。<br /><br /> 有效值 ：Windows`SetThreadPriority`函数的任何有效值和特殊值`INHERIT_THREAD_PRIORITY`<br /><br /> 默认值 ：`THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|计划程序中每个上下文的保留堆栈大小（以千字节为单位）。<br /><br /> 有效值 ：正整数<br /><br /> 默认值 ：，`0`指示使用进程堆栈大小的默认值。|
|`DynamicProgressFeedback`|确定计划程序的资源是根据从计划程序收集的统计信息重新平衡，还是仅根据基础硬件线程的订阅级别进行重新平衡。 有关详细信息，请参阅[动态进度反馈类型](#dynamicprogressfeedbacktype)。<br /><br /> 有效值 ：`DynamicProgressFeedbackType`枚举的成员，或`ProgressFeedbackEnabled``ProgressFeedbackDisabled`<br /><br /> 默认值 ：`ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|当`SchedulingProtocol`策略键设置为 值`EnhanceScheduleGroupLocality`时，这将指定允许每个虚拟处理器本地队列中缓存的最大可运行上下文数。 此类上下文通常会在虚拟处理器上按最后一流 （LIFO） 顺序运行，从而使它们变得可运行。 请注意，当键设置为 值`SchedulingProtocol``EnhanceForwardProgress`时，此策略键没有意义。<br /><br /> 有效值 ：非负整数<br /><br /> 默认值 ：`8`|
|`MaxConcurrency`|计划程序所需的最大并发级别。 资源管理器将尝试最初分配此许多虚拟处理器。 特殊值[Max 执行资源](concurrency-namespace-constants1.md#maxexecutionresources)指示所需的并发级别与计算机上的硬件线程数相同。 如果 指定的`MinConcurrency``MaxConcurrency`值大于计算机上的硬件线程数，并且指定为`MaxExecutionResources`，`MaxConcurrency`则引发 的值以匹配 为`MinConcurrency`设置的值。<br /><br /> 有效值 ：正整数和特殊值`MaxExecutionResources`<br /><br /> 默认值 ：`MaxExecutionResources`|
|`MaxPolicyElementKey`|最大策略元素键。 不是有效的元素键。|
|`MinConcurrency`|资源管理器必须提供给计划程序的最小并发级别。 分配给计划程序的虚拟处理器数永远不会低于最小值。 特殊值[Max 执行资源](concurrency-namespace-constants1.md#maxexecutionresources)指示最小并发级别与计算机上的硬件线程数相同。 如果 为其`MaxConcurrency``MinConcurrency`指定的值小于计算机上的硬件线程数，并且指定为`MaxExecutionResources`， 则 将降低 的值`MinConcurrency`以匹配 为`MaxConcurrency`设置的值。<br /><br /> 有效值：非负整数和特殊值`MaxExecutionResources`。 请注意，对于用于并发运行时计划程序构造的计划程序策略，值 `0` 无效。<br /><br /> 默认值 ：`1`|
|`SchedulerKind`|计划程序将用于基础执行上下文的线程类型。 有关详细信息，请参阅[计划类型](#schedulertype)。<br /><br /> 有效值：枚举 `SchedulerType` 的成员，例如 `ThreadScheduler`<br /><br /> 默认值 ： `ThreadScheduler`. . 这转换为所有操作系统上的 Win32 线程。|
|`SchedulingProtocol`|描述计划程序将使用的调度算法。 有关详细信息，请参阅[计划协议类型](#schedulingprotocoltype)。<br /><br /> 有效值 ：`SchedulingProtocolType`枚举的成员，或`EnhanceScheduleGroupLocality``EnhanceForwardProgress`<br /><br /> 默认值 ：`EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|每个硬件线程的虚拟处理器的暂定数量。 如果必要，资源管理器可以增加目标过度订阅因素，以满足计算机上硬件线程的 `MaxConcurrency`。<br /><br /> 有效值 ：正整数<br /><br /> 默认值 ：`1`|
|`WinRTInitialization`||

### <a name="requirements"></a>要求

**标题：** concrt.h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a>计划器类型枚举

由 `SchedulerKind` 策略用于描述应由计划程序用于基础执行上下文的线程的类型。 有关可用计划程序策略的详细信息，请参阅[策略元素键](concurrency-namespace-enums.md)。

```cpp
enum SchedulerType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`ThreadScheduler`|指示常规 Win32 线程的显式请求。|
|`UmsThreadDefault`|在 Visual Studio 2013 中的并发运行时中不支持用户模式可分划 （UMS） 线程。 使用 `UmsThreadDefault` 作为 `SchedulerType` 策略的一个值不会导致错误。 不过，通过此策略创建的计划程序将默认使用 Win32 线程。|

### <a name="requirements"></a>要求

**标题：** concrt.h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>计划协议类型枚举

由 `SchedulingProtocol` 策略用于描述将哪个计划算法用于计划程序。 有关可用计划程序策略的详细信息，请参阅[策略元素键](concurrency-namespace-enums.md)。

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`EnhanceForwardProgress`|计划程序更喜欢在执行每个任务后循环访问计划组。 未阻止的上下文通常以先出先出 （FIFO） 的方式安排。 虚拟处理器不会缓存未阻止的上下文。|
|`EnhanceScheduleGroupLocality`|计划程序更喜欢在移动到另一个计划组之前继续处理当前计划组中的任务。 未阻止的上下文按虚拟处理器缓存，通常由取消阻止它们的虚拟处理器以最后一先出 （LIFO） 的方式安排。|

### <a name="requirements"></a>要求

**标题：** concrt.h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>切换代理状态枚举

用于表示线程代理在执行另一个线程代理的协作上下文切换时所处的状态。

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`Blocking`|指示调用线程是协同阻塞的，并且应由调用方独占，直到随后再次运行并执行其他操作。|
|`Idle`|指示计划程序不再需要调用线程，并且正在返回到资源管理器。 资源管理器不再能够使用正在调度的上下文。|
|`Nesting`|指示调用线程嵌套子计划程序，并且调用方需要调用线程，以便附加到其他计划程序。|

### <a name="remarks"></a>备注

类型`SwitchingProxyState`参数传入方法`IThreadProxy::SwitchTo`，以指示资源管理器如何处理进行调用的线程代理。

有关如何使用此类型的详细信息，请参阅[IThreadProxy：：Switchto](ithreadproxy-structure.md#switchto)。

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a>task_group_status枚举

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

**标题：** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>WinRT 初始化类型枚举

由 `WinRTInitialization` 策略用于描述，对于在 Windows 8 或更高版本的操作系统上运行的应用程序，是否以及如何在计划程序的线程上初始化 Windows 运行时。 有关可用计划程序策略的详细信息，请参阅[策略元素键](concurrency-namespace-enums.md)。

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`DoNotInitializeWinRT`|当应用程序在 Windows 8 或更高版本的操作系统上运行时，计划程序中的线程不会初始化 Windows 运行时。|
|`InitializeWinRTAsMTA`|当应用程序在 Windows 8 或更高版本的操作系统上运行时，计划程序中的每个线程都将初始化 Windows 运行时并声明它是多线程单元的一部分。|

## <a name="requirements"></a>要求

**标题：** concrt.h

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)
