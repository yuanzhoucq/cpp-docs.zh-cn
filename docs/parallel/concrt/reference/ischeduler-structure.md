---
title: IScheduler 结构
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854117"
---
# <a name="ischeduler-structure"></a>IScheduler 结构

工作计划程序的抽象的接口。 并发运行时的资源管理器使用此接口与工作计划程序进行通信。

## <a name="syntax"></a>语法

```cpp
struct IScheduler;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IScheduler：： AddVirtualProcessors](#addvirtualprocessors)|为计划程序提供一组虚拟处理器根供其使用。 每个 `IVirtualProcessorRoot` 接口都表示执行可以代表计划程序执行工作的单个线程的权限。|
|[IScheduler：： GetId](#getid)|返回计划程序的唯一标识符。|
|[IScheduler：： GetPolicy](#getpolicy)|返回计划程序策略的副本。 有关计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。|
|[IScheduler：： NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|通知此计划程序 `ppVirtualProcessorRoots` 当前正在由其他计划程序使用数组中的虚拟处理器根集表示的硬件线程。|
|[IScheduler：： NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|通知此计划程序：由数组中的虚拟处理器根集表示的硬件线程 `ppVirtualProcessorRoots` 未被其他计划程序使用。|
|[IScheduler：： RemoveVirtualProcessors](#removevirtualprocessors)|开始删除以前分配给此计划程序的虚拟处理器根。|
|[IScheduler：： Statistics](#statistics)|提供与任务到达和完成率相关的信息以及计划程序的队列长度更改。|

## <a name="remarks"></a>备注

如果要实现与资源管理器通信的自定义计划程序，应提供 `IScheduler` 接口的实现。 此接口是计划程序与资源管理器之间的双向通信通道的一端。 另一端由资源管理器实现的 `IResourceManager` 和 `ISchedulerProxy` 接口表示。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IScheduler`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="addvirtualprocessors"></a>IScheduler：： AddVirtualProcessors 方法

为计划程序提供一组虚拟处理器根供其使用。 每个 `IVirtualProcessorRoot` 接口都表示执行可以代表计划程序执行工作的单个线程的权限。

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>parameters

*ppVirtualProcessorRoots*<br/>
`IVirtualProcessorRoot` 接口的数组，表示要添加到计划程序中的虚拟处理器根。

*计数*<br/>
数组中 `IVirtualProcessorRoot` 接口的数目。

### <a name="remarks"></a>备注

资源管理器调用 `AddVirtualProcessor` 方法来向计划程序授予一组初始虚拟处理器根。 它还可以调用方法，在计划程序中间重新平衡资源时，将虚拟处理器根添加到计划程序中。

## <a name="getid"></a>IScheduler：： GetId 方法

返回计划程序的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

唯一整数标识符。

### <a name="remarks"></a>备注

你应使用[GetSchedulerId](concurrency-namespace-functions.md)函数来获取实现 `IScheduler` 接口的对象的唯一标识符，然后将接口用作资源管理器提供的方法的参数。 调用 `GetId` 函数时，应返回相同的标识符。

从不同的源获取的标识符可能会导致未定义的行为。

## <a name="getpolicy"></a>IScheduler：： GetPolicy 方法

返回计划程序策略的副本。 有关计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>返回值

计划程序策略的副本。

## <a name="notifyresourcesexternallybusy"></a>IScheduler：： NotifyResourcesExternallyBusy 方法

通知此计划程序 `ppVirtualProcessorRoots` 当前正在由其他计划程序使用数组中的虚拟处理器根集表示的硬件线程。

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>parameters

*ppVirtualProcessorRoots*<br/>
与其他计划程序处于繁忙状态的硬件线程关联的 `IVirtualProcessorRoot` 接口的数组。

*计数*<br/>
数组中 `IVirtualProcessorRoot` 接口的数目。

### <a name="remarks"></a>备注

可以同时向多个计划程序分配特定硬件线程。 导致这种情况的原因之一是系统上没有足够的硬件线程来满足所有计划程序的最小并发性，而不共享资源。 另一种可能的情况是，当资源的计划程序不使用资源时，这些资源被暂时分配给其他计划程序，而该硬件线程上的所有虚拟处理器根将被停用。

硬件线程的订阅级别表示为与该硬件线程关联的已订阅线程数和激活的虚拟处理器根。 从特定计划程序的角度来看，硬件线程的外部订阅级别是其他计划程序所参与的订阅的一部分。 当硬件线程的外部订阅级别从零移到正面区域时，将向计划程序发送资源处于外部忙碌状态的通知。

通过此方法发出的通知只发送到策略计划程序，该策略中 `MinConcurrency` 策略密钥的值等于 `MaxConcurrency` 策略密钥的值。 有关计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。

限定通知的计划程序会在创建初始通知时获取一组初始通知，并通知其刚分配给它的资源是外部忙还是空闲。

## <a name="notifyresourcesexternallyidle"></a>IScheduler：： NotifyResourcesExternallyIdle 方法

通知此计划程序：由数组中的虚拟处理器根集表示的硬件线程 `ppVirtualProcessorRoots` 未被其他计划程序使用。

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>parameters

*ppVirtualProcessorRoots*<br/>
与其他计划程序处于空闲状态的硬件线程关联的 `IVirtualProcessorRoot` 接口的数组。

*计数*<br/>
数组中 `IVirtualProcessorRoot` 接口的数目。

### <a name="remarks"></a>备注

可以同时向多个计划程序分配特定硬件线程。 导致这种情况的原因之一是系统上没有足够的硬件线程来满足所有计划程序的最小并发性，而不共享资源。 另一种可能的情况是，当资源的计划程序不使用资源时，这些资源被暂时分配给其他计划程序，而该硬件线程上的所有虚拟处理器根将被停用。

硬件线程的订阅级别表示为与该硬件线程关联的已订阅线程数和激活的虚拟处理器根。 从特定计划程序的角度来看，硬件线程的外部订阅级别是其他计划程序所参与的订阅的一部分。 当硬件线程的外部订阅级别从以前的正值降为零时，将向计划程序发送资源处于外部忙碌状态的通知。

通过此方法发出的通知只发送到策略计划程序，该策略中 `MinConcurrency` 策略密钥的值等于 `MaxConcurrency` 策略密钥的值。 有关计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。

限定通知的计划程序会在创建初始通知时获取一组初始通知，并通知其刚分配给它的资源是外部忙还是空闲。

## <a name="removevirtualprocessors"></a>IScheduler：： RemoveVirtualProcessors 方法

开始删除以前分配给此计划程序的虚拟处理器根。

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>parameters

*ppVirtualProcessorRoots*<br/>
一个 `IVirtualProcessorRoot` 接口数组，表示要移除的虚拟处理器根。

*计数*<br/>
数组中 `IVirtualProcessorRoot` 接口的数目。

### <a name="remarks"></a>备注

资源管理器调用 `RemoveVirtualProcessors` 方法从计划程序中取回一组虚拟处理器根。 在虚拟处理器根上完成后，计划程序应在每个接口上调用[Remove](iexecutionresource-structure.md#remove)方法。 在对其调用了 `Remove` 方法后，请不要使用 `IVirtualProcessorRoot` 接口。

参数 `ppVirtualProcessorRoots` 指向接口的数组。 在要删除的虚拟处理器根集中，从未激活的根可以使用 `Remove` 方法立即返回。 应以异步方式返回已激活、正在执行工作或已停用并等待工作到达的根。 计划程序必须尽可能快地尝试删除虚拟处理器根。 延迟删除虚拟处理器根可能会导致计划程序中出现意外的过度订阅。

## <a name="statistics"></a>IScheduler：： Statistics 方法

提供与任务到达和完成率相关的信息以及计划程序的队列长度更改。

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>parameters

*pTaskCompletionRate*<br/>
自上次调用此方法后，计划程序已完成的任务数。

*pTaskArrivalRate*<br/>
自上次调用此方法后，在计划程序中到达的任务数。

*pNumberOfTasksEnqueued*<br/>
所有计划程序队列中的任务总数。

### <a name="remarks"></a>备注

此方法由资源管理器调用，以便收集计划程序的统计信息。 此处收集的统计信息将用于驱动动态反馈算法，以确定何时适合将更多资源分配给计划程序以及何时使用资源。 计划程序提供的值可以是开放式的，并且不必准确反映当前计数。

如果希望资源管理器使用有关任务到达等的反馈来确定如何平衡您的计划程序和向资源管理器注册的其他计划程序之间的资源，则应实现此方法。 如果选择不收集统计信息，则可以将策略密钥 `DynamicProgressFeedback` 设置为计划程序策略中的值 `DynamicProgressFeedbackDisabled`，资源管理器将不会在计划程序上调用此方法。

在缺少统计信息的情况下，资源管理器将使用硬件线程订阅级别来做出资源分配和迁移决策。 有关订阅级别的详细信息，请参阅[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)<br/>
[IExecutionContext 结构](iexecutioncontext-structure.md)<br/>
[IThreadProxy 结构](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 结构](iresourcemanager-structure.md)
