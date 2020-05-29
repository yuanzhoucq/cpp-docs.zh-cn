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
ms.openlocfilehash: ccd82b5c5112bc322717f2b58d79d4c8f34f5bbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368174"
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
|[I计划：：添加虚拟处理器](#addvirtualprocessors)|提供一组带有一组虚拟处理器根的调度程序，供其使用。 每个`IVirtualProcessorRoot`接口表示执行单个线程的权利，该线程可以代表计划程序执行工作。|
|[I时间表：：获取 Id](#getid)|返回计划程序的唯一标识符。|
|[I计划：：获取策略](#getpolicy)|返回计划程序策略的副本。 有关计划程序策略的详细信息，请参阅[计划程序策略](schedulerpolicy-class.md)。|
|[I计划：：通知资源外部忙](#notifyresourcesexternallybusy)|通知此计划程序，数组`ppVirtualProcessorRoots`中虚拟处理器根集表示的硬件线程现在正由其他计划程序使用。|
|[I计划：：通知资源外部空闲](#notifyresourcesexternallyidle)|通知此计划程序，数组`ppVirtualProcessorRoots`中虚拟处理器根集表示的硬件线程不由其他计划程序使用。|
|[I计划：：删除虚拟处理器](#removevirtualprocessors)|启动删除以前分配给此计划程序的虚拟处理器根。|
|[I时间表：：统计](#statistics)|提供与任务到达率和完成率以及计划程序队列长度更改相关的信息。|

## <a name="remarks"></a>备注

如果要实现与资源管理器通信的自定义计划程序，则应提供接口的`IScheduler`实现。 此接口是调度程序与资源管理器之间的双向通信通道的一端。 另一端由资源管理器实现的`IResourceManager`和`ISchedulerProxy`接口表示。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IScheduler`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>I计划：：添加虚拟处理器方法

提供一组带有一组虚拟处理器根的调度程序，供其使用。 每个`IVirtualProcessorRoot`接口表示执行单个线程的权利，该线程可以代表计划程序执行工作。

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*pp 虚拟处理器根*<br/>
表示要添加到`IVirtualProcessorRoot`计划程序的虚拟处理器根的接口数组。

*count*<br/>
数组中的`IVirtualProcessorRoot`接口数。

### <a name="remarks"></a>备注

资源管理器调用 方法`AddVirtualProcessor`将一组初始的虚拟处理器根授予计划程序。 当计划程序之间重新平衡资源时，它还可以调用方法将虚拟处理器根添加到计划程序。

## <a name="ischedulergetid-method"></a><a name="getid"></a>I计划：：GetId 方法

返回计划程序的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

唯一的整数标识符。

### <a name="remarks"></a>备注

在将接口用作资源管理器提供的方法的参数之前，应使用[Get-计划rId](concurrency-namespace-functions.md) `IScheduler`函数为实现接口的对象获取唯一标识符。 调用`GetId`函数时，应返回相同的标识符。

从其他源获取的标识符可能会导致未定义的行为。

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a>I计划：：获取策略方法

返回计划程序策略的副本。 有关计划程序策略的详细信息，请参阅[计划程序策略](schedulerpolicy-class.md)。

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>返回值

计划程序策略的副本。

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>I计划：：通知资源外部忙法

通知此计划程序，数组`ppVirtualProcessorRoots`中虚拟处理器根集表示的硬件线程现在正由其他计划程序使用。

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*pp 虚拟处理器根*<br/>
与其他计划程序`IVirtualProcessorRoot`已忙的硬件线程关联的接口数组。

*count*<br/>
数组中的`IVirtualProcessorRoot`接口数。

### <a name="remarks"></a>备注

可以将特定硬件线程同时分配给多个计划程序。 原因之一可能是系统上没有足够的硬件线程来满足所有计划程序的最低并发性，而无需共享资源。 另一种可能性是，当拥有的计划程序不使用资源时，资源会临时分配给其他计划程序，方法是通过停用该硬件线程上的所有虚拟处理器根。

硬件线程的订阅级别由与该硬件线程关联的订阅线程数和激活的虚拟处理器根表示。 从特定计划程序的角度来看，硬件线程的外部订阅级别是其他计划程序贡献的订阅部分。 当硬件线程的外部订阅级别从零移动到正区域时，资源在外部忙的通知将发送到计划程序。

通过此方法发送的通知仅发送到具有策略的调度程序，其中`MinConcurrency`策略键的值等于`MaxConcurrency`策略键的值。 有关计划程序策略的详细信息，请参阅[计划程序策略](schedulerpolicy-class.md)。

符合通知条件的计划程序会在创建通知时获取一组初始通知，通知它刚刚分配的资源是外部忙还是空闲。

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>I计划：：通知资源外部空闲方法

通知此计划程序，数组`ppVirtualProcessorRoots`中虚拟处理器根集表示的硬件线程不由其他计划程序使用。

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*pp 虚拟处理器根*<br/>
与硬件线程`IVirtualProcessorRoot`关联的接口数组，其他计划程序已处于空闲状态。

*count*<br/>
数组中的`IVirtualProcessorRoot`接口数。

### <a name="remarks"></a>备注

可以将特定硬件线程同时分配给多个计划程序。 原因之一可能是系统上没有足够的硬件线程来满足所有计划程序的最低并发性，而无需共享资源。 另一种可能性是，当拥有的计划程序不使用资源时，资源会临时分配给其他计划程序，方法是通过停用该硬件线程上的所有虚拟处理器根。

硬件线程的订阅级别由与该硬件线程关联的订阅线程数和激活的虚拟处理器根表示。 从特定计划程序的角度来看，硬件线程的外部订阅级别是其他计划程序贡献的订阅部分。 当硬件线程的外部订阅级别从以前的正值降至零时，资源在外部忙的通知将发送到计划程序。

通过此方法发送的通知仅发送到具有策略的调度程序，其中`MinConcurrency`策略键的值等于`MaxConcurrency`策略键的值。 有关计划程序策略的详细信息，请参阅[计划程序策略](schedulerpolicy-class.md)。

符合通知条件的计划程序会在创建通知时获取一组初始通知，通知它刚刚分配的资源是外部忙还是空闲。

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>I计划时间：：删除虚拟处理器方法

启动删除以前分配给此计划程序的虚拟处理器根。

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*pp 虚拟处理器根*<br/>
表示要删除`IVirtualProcessorRoot`的虚拟处理器根的接口数组。

*count*<br/>
数组中的`IVirtualProcessorRoot`接口数。

### <a name="remarks"></a>备注

资源管理器调用`RemoveVirtualProcessors`方法从计划程序收回一组虚拟处理器根。 当使用虚拟处理器根时，计划程序应调用每个接口上的[Remove](iexecutionresource-structure.md#remove)方法。 调用接口上的方法`IVirtualProcessorRoot`后，`Remove`请勿使用接口。

该参数`ppVirtualProcessorRoots`指向接口数组。 在要删除的虚拟处理器根集中，从未激活过根，可以使用 该方法`Remove`立即返回。 已激活且正在执行工作或已停用并正在等待工作到达的根应异步返回。 计划程序必须进行每一次尝试，以尽快删除虚拟处理器根。 延迟删除虚拟处理器根可能会导致计划程序内意外过度订阅。

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a>I计划：：统计方法

提供与任务到达率和完成率以及计划程序队列长度更改相关的信息。

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>参数

*p任务完成率*<br/>
自上次调用此方法以来，计划程序已完成的任务数。

*p任务到达率*<br/>
自上次调用此方法以来到达计划程序的任务数。

*已排队的任务编号*<br/>
所有计划程序队列中的任务总数。

### <a name="remarks"></a>备注

资源管理器调用此方法以收集计划程序的统计信息。 此处收集的统计信息将用于驱动动态反馈算法，以确定何时适合为计划程序分配更多资源以及何时获取资源。 计划程序提供的值可以是乐观的，不一定必须准确反映当前计数。

如果希望资源管理器使用有关任务到达等的反馈来确定如何平衡您的计划程序和向资源管理器注册的其他计划程序之间的资源，则应实现此方法。 如果选择不收集统计信息，则可以将策略键`DynamicProgressFeedback`设置为计划程序策略中的值`DynamicProgressFeedbackDisabled`，并且资源管理器不会在计划程序上调用此方法。

在没有统计信息的情况下，资源管理器将使用硬件线程订阅级别来做出资源分配和迁移决策。 有关订阅级别的详细信息，请参阅[I 执行资源：：当前订阅级别](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[策略元素键](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)<br/>
[IExecutionContext 结构](iexecutioncontext-structure.md)<br/>
[IThreadProxy 结构](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 结构](iresourcemanager-structure.md)
