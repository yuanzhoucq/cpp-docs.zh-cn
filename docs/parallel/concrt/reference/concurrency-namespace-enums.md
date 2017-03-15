---
title: "并发命名空间枚举 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 8f7488ff07c9789e2d5f35056de390a5bc464f56
ms.openlocfilehash: ff187e827b2dd979466b746eee297235e6a6c0ca
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-enums"></a>并发命名空间枚举
||||  
|-|-|-|  
|[Agents_EventType 枚举](#agents_eventtype)|[ConcRT_EventType 枚举](#concrt_eventtype)|[Concrt_TraceFlags 枚举](#concrt_traceflags)|  
|[CriticalRegionType 枚举](#criticalregiontype)|[DynamicProgressFeedbackType 枚举](#dynamicprogressfeedbacktype)|[PolicyElementKey 枚举](#policyelementkey)|  
|[SchedulerType 枚举](#schedulertype)|[SchedulingProtocolType 枚举](#schedulingprotocoltype)|[SwitchingProxyState 枚举](#switchingproxystate)|  
|[WinRTInitializationType 枚举](#winrtinitializationtype)|[agent_status 枚举](#agent_status)|[join_type 枚举](#join_type)|  
|[message_status 枚举](#message_status)|[task_group_status 枚举](#task_group_status)|  
  
##  <a name="a-nameagentstatusa--agentstatus-enumeration"></a><a name="agent_status"></a>agent_status 枚举  
 `agent` 的有效状态。  
  
```
enum agent_status;
```  
### <a name="values"></a>值  
  
|名称|说明|  
|----------|-----------------|  
|`agent_canceled`|已取消 `agent`。|  
|`agent_created`|`agent`已创建但尚未开始。|  
|`agent_done`|`agent`完成而未被取消。|  
|`agent_runnable`|`agent`已启动，但未输入其`run`方法。|  
|`agent_started`|`agent`已启动。|  

### <a name="remarks"></a>备注  
 有关详细信息，请参阅[异步代理](../../../parallel/concrt/asynchronous-agents.md)。  

### <a name="requirements"></a>要求  
 **标头︰** concrt.h

##  <a name="a-nameagentseventtypea--agentseventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType 枚举  
 可以使用代理库提供的跟踪功能进行跟踪的事件的类型  
  
```
enum Agents_EventType;
```  

### <a name="values"></a>值  
  
|名称|描述|  
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
 **标头︰** concrt.h

##  <a name="a-nameconcrteventtypea--concrteventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType 枚举  
 可以使用并发运行时提供的跟踪功能进行跟踪的事件的类型。  
  
```
enum ConcRT_EventType;
```  
### <a name="values"></a>值  
  
|名称|说明|  
|----------|-----------------|  
|`CONCRT_EVENT_ATTACH`|事件类型表示附加到一个计划程序的行为。|  
|`CONCRT_EVENT_BLOCK`|事件类型表示的上下文阻塞行为。|  
|`CONCRT_EVENT_DETACH`|事件类型表示与调度程序分离的行为。|  
|`CONCRT_EVENT_END`|标记开始的开始/结束事件对事件类型。|  
|`CONCRT_EVENT_GENERIC`|用于其他事件的事件类型。|  
|`CONCRT_EVENT_IDLE`|事件类型表示处于空闲状态的上下文行为。|  
|`CONCRT_EVENT_START`|标记开始的开始/结束事件对事件类型。|  
|`CONCRT_EVENT_UNBLOCK`|事件类型表示取消阻止上下文的行为。|  
|`CONCRT_EVENT_YIELD`|事件类型表示的上下文生成行为。|  
  
### <a name="requirements"></a>要求  
 **标头︰** concrt.h

##  <a name="a-nameconcrttraceflagsa--concrttraceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags 枚举  
 事件类型的跟踪标志  
  
```
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
 **标头︰** concrt.h

##  <a name="a-namecriticalregiontypea--criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>CriticalRegionType 枚举  
 上下文位于其中的关键区域的类型。  
  
```
enum CriticalRegionType;
```  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`InsideCriticalRegion`|指示上下文是关键的区域内。 关键的区域内时计划程序中隐藏异步挂起。 如果发生此类挂起，资源管理器将等待线程变为可运行，并只使其继续而不是再次调用计划程序。 任何此类区域内获取的锁必须格外小心地使用。|  
|`InsideHyperCriticalRegion`|指示上下文是超关键的区域内。 当超关键的区域内，在计划程序中隐藏同步和异步挂起。 此类挂起或阻塞发生这种情况，资源管理器将等待线程变为可运行，并只使其继续而不是再次调用计划程序。 此类区域内获取的锁永远不会必须与此类区域外运行的代码共享。 这样做将导致不可预知的死锁。|  
|`OutsideCriticalRegion`|指示上下文是所有关键区域外。|  
  
### <a name="requirements"></a>要求  
 **标头︰** concrtrm.h 

##  <a name="a-namedynamicprogressfeedbacktypea--dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>DynamicProgressFeedbackType 枚举  
 由 `DynamicProgressFeedback` 策略用于描述重新平衡计划程序资源的依据是从计划程序收集的统计信息，还是通过对 `IVirtualProcessorRoot` 接口上的 `Activate` 和 `Deactivate` 方法进行调用以进出空闲状态的虚拟处理器。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md)。  
  
```
enum DynamicProgressFeedbackType;
```  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`ProgressFeedbackDisabled`|计划程序不会收集进度信息。 重新平衡是基于完成仅取决于基础硬件线程的订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](IExecutionResource-structure.md)。<br /><br /> 由运行时情况下，此值保留供使用。|  
|`ProgressFeedbackEnabled`|计划程序收集进度信息，并将其传递给资源管理器。 资源管理器将利用这些统计信息来代表计划程序除了基础硬件线程的订阅级别重新平衡资源。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](IExecutionResource-structure.md)。|  
##  <a name="a-namejointypea--jointype-enumeration"></a><a name="join_type"></a>join_type 枚举  
 `join` 消息块的类型。  
  
```
enum join_type;
```  
### <a name="values"></a>值  
  
|名称|说明|  
|----------|-----------------|  
|`greedy`|贪婪`join`消息块立即接受一条消息在传播时。 这是更加有效，但具有实时锁定，具体取决于网络配置的可能性。|  
|`non_greedy`|非贪婪`join`消息传递块推迟消息并尝试使用它们全部都到达后。 可保证这些工作，但是速度更慢。|  
  
### <a name="requirements"></a>要求  
 **标头：** agents.h  

##  <a name="a-namemessagestatusa--messagestatus-enumeration"></a><a name="message_status"></a>message_status 枚举  
 `message` 对象的内容到块的有效响应。  
  
```
enum message_status;
```  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`accepted`|目标接受消息。|  
|`declined`|目标不接受该消息。|  
|`missed`|目标尝试接受消息，但已不再可用。|  
|`postponed`|目标已推迟消息。|  
  
### <a name="requirements"></a>要求  
 **标头：** agents.h  

##  <a name="a-namepolicyelementkeya--policyelementkey-enumeration"></a><a name="policyelementkey"></a>PolicyElementKey 枚举  
 描述计划程序行为各个方面的策略键。 每个策略元素由一个键值对描述。 有关计划程序策略和它们的影响计划程序的详细信息，请参阅[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
```
enum PolicyElementKey;
```  
### <a name="values"></a>值  
  
|名称|说明|  
|----------|-----------------|  
|`ContextPriority`|计划程序中的每个上下文的操作系统线程优先级。 如果此项设置为值`INHERIT_THREAD_PRIORITY`计划程序中的上下文将继承创建该计划的线程的优先级。<br /><br /> 有效值︰ 任何有效的值适用于 Windows`SetThreadPriority`函数以及特殊值`INHERIT_THREAD_PRIORITY`<br /><br /> 默认值︰`THREAD_PRIORITY_NORMAL`|  
|`ContextStackSize`|每个上下文中千字节为单位的计划程序中保留的堆栈大小。<br /><br /> 有效值︰ 正整数<br /><br /> 默认值︰ `0`，指出必须使用进程的默认值为堆栈大小。|  
|`DynamicProgressFeedback`|确定是否根据统计信息收集从计划程序还是仅基于基础硬件线程的订阅级别，将重新平衡计划程序的资源。 有关详细信息，请参阅[DynamicProgressFeedbackType 枚举](#dynamicprogressfeedbacktype)。<br /><br /> 有效值︰ 属于`DynamicProgressFeedbackType`枚举、 任一`ProgressFeedbackEnabled`或`ProgressFeedbackDisabled`<br /><br /> 默认值︰`ProgressFeedbackEnabled`|  
|`LocalContextCacheSize`|当`SchedulingProtocol`策略的注册表项设置为值`EnhanceScheduleGroupLocality`，它指定可运行的上下文允许缓存在每个虚拟处理器本地队列的最大数目。 此类上下文通常将按先出 (LIFO) 顺序导致它们变为可运行的虚拟处理器上运行。 请注意，此策略注册表项有任何意义时`SchedulingProtocol`键设置为值`EnhanceForwardProgress`。<br /><br /> 有效值︰ 非负整数<br /><br /> 默认值︰`8`|  
|`MaxConcurrency`|最大并发级别所需的计划程序。 资源管理器将尝试最初分配这么多虚拟处理器。 特殊值[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)指示所需的并发级别是相同的计算机上的硬件线程数。 如果指定的值`MinConcurrency`大于计算机上的硬件线程的数量和`MaxConcurrency`被指定为`MaxExecutionResources`，值`MaxConcurrency`引发以匹配设置为`MinConcurrency`。<br /><br /> 有效值︰ 正整数以及特殊值`MaxExecutionResources`<br /><br /> 默认值︰`MaxExecutionResources`|  
|`MaxPolicyElementKey`|最大策略元素键。 不是有效的元素键。|  
|`MinConcurrency`|必须通过资源管理器提供的计划程序最小并发级别。 分配给计划程序的虚拟处理器的数量将永远不会低于最小值。 特殊值[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)指示最小并发级别是相同的计算机上的硬件线程数。 如果指定的值`MaxConcurrency`小于在计算机上的硬件线程的数量和`MinConcurrency`被指定为`MaxExecutionResources`的值为`MinConcurrency`降低以匹配设置为`MaxConcurrency`。<br /><br /> 有效值︰ 非负整数和特殊值`MaxExecutionResources`。 请注意，对于用于并发运行时计划程序构造的计划程序策略，值 `0` 无效。<br /><br /> 默认值︰`1`|  
|`SchedulerKind`|计划程序都将使用的基础的执行上下文的线程的类型。 有关详细信息，请参阅[SchedulerType 枚举](#schedulertype)。<br /><br /> 有效值：枚举 `SchedulerType` 的成员，例如 `ThreadScheduler`<br /><br /> 默认值︰ `ThreadScheduler`。 这相当于所有操作系统上的 Win32 线程。|  
|`SchedulingProtocol`|描述计划程序将使用的计划算法。 有关详细信息，请参阅[SchedulingProtocolType 枚举](#schedulingprotocoltype)。<br /><br /> 有效值︰ 属于`SchedulingProtocolType`枚举、 任一`EnhanceScheduleGroupLocality`或`EnhanceForwardProgress`<br /><br /> 默认值︰`EnhanceScheduleGroupLocality`|  
|`TargetOversubscriptionFactor`|暂定每个硬件线程的虚拟处理器数。 如果必要，资源管理器可以增加目标过度订阅因素，以满足计算机上硬件线程的 `MaxConcurrency`。<br /><br /> 有效值︰ 正整数<br /><br /> 默认值︰`1`|  
|`WinRTInitialization`||  
  
### <a name="requirements"></a>要求  
 **标头︰** concrt.h  

##  <a name="a-nameschedulertypea--schedulertype-enumeration"></a><a name="schedulertype"></a>SchedulerType 枚举  
 由 `SchedulerKind` 策略用于描述应由计划程序用于基础执行上下文的线程的类型。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md)。  
  
```
enum SchedulerType;
``` 

### <a name="values"></a>值  
  
|名称|说明|  
|----------|-----------------|  
|`ThreadScheduler`|表示显式请求的常规 Win32 线程。|  
|`UmsThreadDefault`|在 Visual Studio 2013 中并发运行时中不支持用户模式计划 (UMS) 线程。 使用 `UmsThreadDefault` 作为 `SchedulerType` 策略的一个值不会导致错误。 不过，通过此策略创建的计划程序将默认使用 Win32 线程。|  
  
### <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
##  <a name="a-nameschedulingprotocoltypea--schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>SchedulingProtocolType 枚举  
 由 `SchedulingProtocol` 策略用于描述将哪个计划算法用于计划程序。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md)。  
  
```
enum SchedulingProtocolType;
```  
### <a name="values"></a>值  
  
|名称|说明|  
|----------|-----------------|  
|`EnhanceForwardProgress`|在执行每项任务后，计划程序首选到通过计划组的轮循机制。 取消阻止的上下文通常安排在第一个中先出 (FIFO) 的方式。 虚拟处理器不缓存解锁的上下文。|  
|`EnhanceScheduleGroupLocality`|计划程序首选继续处理当前的计划组中的任务后才能将移动到另一个计划组。 解锁的上下文缓存每个虚拟处理器，通常按计划先出 (LIFO) 方式通过解除阻止它们的虚拟处理器。|  
  
### <a name="requirements"></a>要求  
 **标头︰** concrt.h  
 
##  <a name="a-nameswitchingproxystatea--switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>SwitchingProxyState 枚举  
 用于表示线程代理在执行另一个线程代理的协作上下文切换时所处的状态。  
  
```
enum SwitchingProxyState;
```  
### <a name="values"></a>值  
  
|名称|说明|  
|----------|-----------------|  
|`Blocking`|指示调用线程以协作方式阻止，并且应以独占方式拥有由调用方之前以后再次运行并执行其他操作。|  
|`Idle`|指示调用线程不再需要计划程序，并返回到资源管理器。 正被调度上下文不再能够使用资源管理器。|  
|`Nesting`|表示调用线程正在嵌套子计划程序，需要由调用方，以便将附加到不同的计划程序。|  

### <a name="remarks"></a>备注  
 类型的参数`SwitchingProxyState`中传递给该方法`IThreadProxy::SwitchTo`以指示资源管理器如何处理进行调用的线程代理。  
  
 有关如何使用此类型的详细信息，请参阅[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)。  
  
##  <a name="a-nametaskgroupstatusa--taskgroupstatus-enumeration"></a><a name="task_group_status"></a>task_group_status 枚举  
 描述 `task_group` 或 `structured_task_group` 对象的执行状态。 此类型的值是由很多等待安排到一个任务组中的任务完成的方法返回的。  
  
```
enum task_group_status;
```  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`canceled`|`task_group` 或 `structured_task_group` 对象已取消。 一个或多个任务可能未执行。|  
|`completed`|排入 `task_group` 或 `structured_task_group` 对象的任务已成功完成。|  
|`not_complete`|排入 `task_group` 对象的任务尚未完成。 请注意，此值目前不是由并发运行时返回的。|  
  
### <a name="requirements"></a>要求  
 **标头︰** pplinterface.h  

##  <a name="a-namewinrtinitializationtypea--winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>WinRTInitializationType 枚举  
 由 `WinRTInitialization` 策略用于描述，对于在 Windows 8 或更高版本的操作系统上运行的应用程序，是否以及如何在计划程序的线程上初始化 Windows 运行时。 有关可用的计划程序策略的详细信息，请参阅[PolicyElementKey 枚举](concurrency-namespace-enums.md)。  
  
```
enum WinRTInitializationType;
```  
### <a name="values"></a>值  
  
|名称|描述|  
|----------|-----------------|  
|`DoNotInitializeWinRT`|当应用程序在 Windows 8 或更高版本的操作系统上运行时，计划程序中的线程不会初始化 Windows 运行时。|  
|`InitializeWinRTAsMTA`|当应用程序在 Windows 8 或更高版本的操作系统上运行时，计划程序中的每个线程都将初始化 Windows 运行时并声明它是多线程单元的一部分。|  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  

## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

