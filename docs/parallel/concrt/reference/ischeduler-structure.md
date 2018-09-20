---
title: IScheduler 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c926589165cbf93bd517612514bc27c88f28e15
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378860"
---
# <a name="ischeduler-structure"></a>IScheduler 结构

工作计划程序的抽象的接口。 并发运行时的资源管理器使用此接口与工作计划程序进行通信。

## <a name="syntax"></a>语法

```
struct IScheduler;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Ischeduler:: Addvirtualprocessors](#addvirtualprocessors)|供其使用计划程序提供一组虚拟处理器根。 每个`IVirtualProcessorRoot`接口表示执行可执行工作计划程序代表的单线程的权限。|
|[IScheduler::GetId](#getid)|返回计划程序的唯一标识符。|
|[IScheduler::GetPolicy](#getpolicy)|返回计划程序的策略的一个副本。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|通知此计划程序的数组中的虚拟处理器根集所表示的硬件线程`ppVirtualProcessorRoots`现在正在使用的其他计划程序。|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|通知此计划程序的数组中的虚拟处理器根集所表示的硬件线程`ppVirtualProcessorRoots`未正在使用的其他计划程序。|
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|启动删除的以前分配给此计划程序的虚拟处理器根。|
|[Ischeduler:: Statistics](#statistics)|提供了与任务到达和完成费用，以及适用于计划程序队列长度的变化相关的信息。|

## <a name="remarks"></a>备注

如果要实现的自定义计划程序与资源管理器进行通信，则应提供的实现`IScheduler`接口。 此接口是通信的一种计划程序和资源管理器之间的双向通道的一端。 表示另一端`IResourceManager`和`ISchedulerProxy`实现由资源管理器的接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IScheduler`

## <a name="requirements"></a>要求

**标头：** concrtrm.h

**命名空间：** 并发

##  <a name="addvirtualprocessors"></a>  Ischeduler:: Addvirtualprocessors 方法

供其使用计划程序提供一组虚拟处理器根。 每个`IVirtualProcessorRoot`接口表示执行可执行工作计划程序代表的单线程的权限。

```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*ppVirtualProcessorRoots*<br/>
一个数组`IVirtualProcessorRoot`接口表示虚拟处理器根添加到计划程序。

*count*<br/>
数`IVirtualProcessorRoot`数组中的接口。

### <a name="remarks"></a>备注

资源管理器将调用`AddVirtualProcessor`方法以向计划程序授予一组初始的虚拟处理器根。 它还可以调用方法时重新平衡计划程序之间的资源添加到计划程序的虚拟处理器根。

##  <a name="getid"></a>  Ischeduler:: Getid 方法

返回计划程序的唯一标识符。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

一个唯一整数标识符。

### <a name="remarks"></a>备注

应使用[GetSchedulerId](concurrency-namespace-functions.md)函数获取实现的对象的唯一标识符`IScheduler`接口，然后作为方法的参数使用该接口提供由资源管理器。 应该会返回相同的标识符时`GetId`调用函数。

从不同源中获取的标识符可能导致未定义的行为。

##  <a name="getpolicy"></a>  Ischeduler:: Getpolicy 方法

返回计划程序的策略的一个副本。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。

```
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>返回值

计划程序的策略的副本。

##  <a name="notifyresourcesexternallybusy"></a>  Ischeduler:: Notifyresourcesexternallybusy 方法

通知此计划程序的数组中的虚拟处理器根集所表示的硬件线程`ppVirtualProcessorRoots`现在正在使用的其他计划程序。

```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*ppVirtualProcessorRoots*<br/>
一个数组`IVirtualProcessorRoot`与其他计划程序已成为繁忙的硬件线程关联的接口。

*count*<br/>
数`IVirtualProcessorRoot`数组中的接口。

### <a name="remarks"></a>备注

就可以在同一时间要分配给多个计划程序的特定硬件线程。 这一原因可能是系统以满足最小并发的所有计划程序，而无需共享资源上没有足够的硬件线程。 另一种可能性是将资源暂时分配到其他计划程序所属的计划程序不使用时，通过在停用该硬件线程上的所有虚拟处理器根。

订阅级别的硬件线程的已订阅的线程数表示，并激活与该硬件线程相关联的虚拟处理器根。 从特定计划程序的角度来看，硬件线程的外部订阅级别是订阅的参与其他计划程序的一部分。 当硬件线程的外部订阅级别将从零到正范围的资源是外部繁忙的通知发送到计划程序。

通过此方法通知只发送到计划程序策略的位置的值`MinConcurrency`策略的注册表项是否等于的值为`MaxConcurrency`策略密钥。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。

享有以下产品的通知的计划程序获取一组初始通知后，通知它只是分配的资源从外部正忙还是空闲。

##  <a name="notifyresourcesexternallyidle"></a>  Ischeduler:: Notifyresourcesexternallyidle 方法

通知此计划程序的数组中的虚拟处理器根集所表示的硬件线程`ppVirtualProcessorRoots`未正在使用的其他计划程序。

```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*ppVirtualProcessorRoots*<br/>
一个数组`IVirtualProcessorRoot`与其他计划程序已进入空闲状态的硬件线程关联的接口。

*count*<br/>
数`IVirtualProcessorRoot`数组中的接口。

### <a name="remarks"></a>备注

就可以在同一时间要分配给多个计划程序的特定硬件线程。 这一原因可能是系统以满足最小并发的所有计划程序，而无需共享资源上没有足够的硬件线程。 另一种可能性是将资源暂时分配到其他计划程序所属的计划程序不使用时，通过在停用该硬件线程上的所有虚拟处理器根。

订阅级别的硬件线程的已订阅的线程数表示，并激活与该硬件线程相关联的虚拟处理器根。 从特定计划程序的角度来看，硬件线程的外部订阅级别是订阅的参与其他计划程序的一部分。 资源是外部繁忙的通知发送到计划程序时的硬件线程的外部订阅级别降到零时从先前的正数值。

通过此方法通知只发送到计划程序策略的位置的值`MinConcurrency`策略的注册表项是否等于的值为`MaxConcurrency`策略密钥。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。

享有以下产品的通知的计划程序获取一组初始通知后，通知它只是分配的资源从外部正忙还是空闲。

##  <a name="removevirtualprocessors"></a>  Ischeduler:: Removevirtualprocessors 方法

启动删除的以前分配给此计划程序的虚拟处理器根。

```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>参数

*ppVirtualProcessorRoots*<br/>
一个数组`IVirtualProcessorRoot`表示要删除的虚拟处理器根的接口。

*count*<br/>
数`IVirtualProcessorRoot`数组中的接口。

### <a name="remarks"></a>备注

资源管理器将调用`RemoveVirtualProcessors`方法以从计划程序需要返回一组虚拟处理器根。 计划程序应调用[删除](iexecutionresource-structure.md#remove)上完成虚拟处理器根与每个接口的方法。 不要使用`IVirtualProcessorRoot`接口具有调用后`Remove`方法。

参数`ppVirtualProcessorRoots`指向接口的数组。 在要删除的虚拟处理器根的集，，永远不会被激活根可以立即使用返回`Remove`方法。 根已激活，并执行工作，或已停用、 等待工作到达时，应以异步方式返回。 计划程序必须进行每次尝试尽可能快地删除虚拟处理器根。 延迟删除的虚拟处理器根，则可能会导致无意过度订阅的计划程序中。

##  <a name="statistics"></a>  Ischeduler:: Statistics 方法

提供了与任务到达和完成费用，以及适用于计划程序队列长度的变化相关的信息。

```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>参数

*pTaskCompletionRate*<br/>
自上次调用此方法由计划程序完成的任务数。

*pTaskArrivalRate*<br/>
已到达自上次调用此方法在计划程序中的任务数。

*pNumberOfTasksEnqueued*<br/>
所有计划程序队列中任务的总数。

### <a name="remarks"></a>备注

调用此方法才能收集计划程序统计信息由资源管理器。 此处收集的统计信息将用于驱动动态反馈算法来确定何时适合要分配给计划程序的更多资源，以及何时需要注意的资源。 由计划程序提供的值可以是开放式的并不一定需要准确地反映当前的计数。

如果希望资源管理器使用有关任务到达等的反馈来确定如何平衡您的计划程序和向资源管理器注册的其他计划程序之间的资源，则应实现此方法。 如果您选择不收集统计信息，则可以设置策略密钥`DynamicProgressFeedback`的值`DynamicProgressFeedbackDisabled`中您的计划程序策略和资源管理器将不会调用你的计划程序上的此方法。

缺少的统计信息的情况下，资源管理器将使用硬件线程的订阅级别进行资源分配和迁移决策。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy 类](schedulerpolicy-class.md)<br/>
[IExecutionContext 结构](iexecutioncontext-structure.md)<br/>
[IThreadProxy 结构](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 结构](iresourcemanager-structure.md)
