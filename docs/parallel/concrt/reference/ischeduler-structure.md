---
title: IScheduler 结构 |Microsoft 文档
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
ms.openlocfilehash: 9c78d02ccd5639369ad8b4d0183458da2ba85269
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
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
|[Ischeduler:: Addvirtualprocessors](#addvirtualprocessors)|供其使用计划程序提供一组虚拟处理器根。 每个`IVirtualProcessorRoot`接口表示有权执行可执行代表计划程序的工作的单个线程。|  
|[IScheduler::GetId](#getid)|返回计划程序的唯一标识符。|  
|[IScheduler::GetPolicy](#getpolicy)|返回计划程序的策略的副本。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。|  
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|通知此计划程序的硬件线程所表示的一套数组中的虚拟处理器根`ppVirtualProcessorRoots`现在正在使用的其他计划程序。|  
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|通知此计划程序的硬件线程所表示的一套数组中的虚拟处理器根`ppVirtualProcessorRoots`不正由其他计划程序。|  
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|启动的以前分配给此计划程序的虚拟处理器根的删除操作。|  
|[Ischeduler:: Statistics](#statistics)|提供与任务到达和完成率和计划程序的队列长度更改相关的信息。|  
  
## <a name="remarks"></a>备注  
 如果你要实现的自定义计划程序与资源管理器进行通信，则应提供的实现`IScheduler`接口。 此接口是通道的双向通信的计划程序和资源管理器之间的一个 end。 由表示另一端`IResourceManager`和`ISchedulerProxy`都实现资源管理器的接口。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IScheduler`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="addvirtualprocessors"></a>  Ischeduler:: Addvirtualprocessors 方法  
 供其使用计划程序提供一组虚拟处理器根。 每个`IVirtualProcessorRoot`接口表示有权执行可执行代表计划程序的工作的单个线程。  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 数组`IVirtualProcessorRoot`接口表示虚拟处理器根添加到计划程序。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 资源管理器时，将调用`AddVirtualProcessor`方法授予对计划程序的虚拟处理器根的初始集。 它还可以调用的方法时重新平衡计划程序之间的资源添加到调度器的虚拟处理器根。  
  
##  <a name="getid"></a>  Ischeduler:: Getid 方法  
 返回计划程序的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 唯一的整数标识符。  
  
### <a name="remarks"></a>备注  
 应使用[GetSchedulerId](concurrency-namespace-functions.md)函数来获取实现的对象的唯一标识符`IScheduler`接口，然后作为参数传递给方法使用该接口提供由资源管理器。 你都应该返回相同的标识符时`GetId`调用函数。  
  
 获取从不同源的标识符可能导致未定义的行为。  
  
##  <a name="getpolicy"></a>  Ischeduler:: Getpolicy 方法  
 返回计划程序的策略的副本。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 计划程序的策略的副本。  
  
##  <a name="notifyresourcesexternallybusy"></a>  Ischeduler:: Notifyresourcesexternallybusy 方法  
 通知此计划程序的硬件线程所表示的一套数组中的虚拟处理器根`ppVirtualProcessorRoots`现在正在使用的其他计划程序。  
  
```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 数组`IVirtualProcessorRoot`与在其的其他计划程序已变得繁忙的硬件线程关联的接口。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 很可能在同一时间要分配给多个计划程序的特定的硬件线程。 此的一个原因可能是为了满足最小并发有关的所有计划程序，而不用共享资源系统上没有足够的硬件线程。 另一种可能性是，资源临时分配给其他计划程序所属的计划程序不使用时，通过正在停用该硬件线程上的所有虚拟处理器根。  
  
 硬件线程的订阅级别激活与该硬件线程关联的虚拟处理器根和由订阅的线程数表示。 从特定计划程序的角度来看，外部订阅级别的硬件线程是的订阅的其他计划程序贡献的部分。 当硬件线程的外部订阅级别将从零到正范围，资源是外部繁忙的通知会发送到计划程序。  
  
 通过此方法通知仅发送到计划程序有一个策略，其中的值`MinConcurrency`策略密钥等于的值`MaxConcurrency`策略密钥。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 限定通知的计划获取一的组初始的通知时创建，告知其刚分配的资源的外部正忙还是空闲。  
  
##  <a name="notifyresourcesexternallyidle"></a>  Ischeduler:: Notifyresourcesexternallyidle 方法  
 通知此计划程序的硬件线程所表示的一套数组中的虚拟处理器根`ppVirtualProcessorRoots`不正由其他计划程序。  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 数组`IVirtualProcessorRoot`硬件线程的其他计划程序已进入空闲状态与关联的接口。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 很可能在同一时间要分配给多个计划程序的特定的硬件线程。 此的一个原因可能是为了满足最小并发有关的所有计划程序，而不用共享资源系统上没有足够的硬件线程。 另一种可能性是，资源临时分配给其他计划程序所属的计划程序不使用时，通过正在停用该硬件线程上的所有虚拟处理器根。  
  
 硬件线程的订阅级别激活与该硬件线程关联的虚拟处理器根和由订阅的线程数表示。 从特定计划程序的角度来看，外部订阅级别的硬件线程是的订阅的其他计划程序贡献的部分。 硬件线程的外部订阅级别下降到零从先前的正数值时，资源是外部繁忙的通知会发送到计划程序。  
  
 通过此方法通知仅发送到计划程序有一个策略，其中的值`MinConcurrency`策略密钥等于的值`MaxConcurrency`策略密钥。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 限定通知的计划获取一的组初始的通知时创建，告知其刚分配的资源的外部正忙还是空闲。  
  
##  <a name="removevirtualprocessors"></a>  Ischeduler:: Removevirtualprocessors 方法  
 启动的以前分配给此计划程序的虚拟处理器根的删除操作。  
  
```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 数组`IVirtualProcessorRoot`表示要删除的虚拟处理器根的接口。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 资源管理器时，将调用`RemoveVirtualProcessors`方法，如果要从计划程序收回一组虚拟处理器根。 计划程序需要调用[删除](iexecutionresource-structure.md#remove)上完成虚拟处理器根与每个接口的方法。 不要使用`IVirtualProcessorRoot`接口一旦已经调用`Remove`方法。  
  
 参数`ppVirtualProcessorRoots`指向的接口的数组。 组中的要删除的虚拟处理器根，，永远不会被激活的根可以立即使用返回`Remove`方法。 应以异步方式返回已激活和是任一正在执行的工作或已停用，正在等待任务到达的根目录。 计划程序必须进行每次尝试以尽可能快地删除虚拟处理器根。 延迟删除的虚拟处理器根，则可能会导致无意过度订阅的计划程序中。  
  
##  <a name="statistics"></a>  Ischeduler:: Statistics 方法  
 提供与任务到达和完成率和计划程序的队列长度更改相关的信息。  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pTaskCompletionRate`  
 自上次调用此方法以来已由调度器中完成的任务数。  
  
 `pTaskArrivalRate`  
 已到达自上次调用此方法在计划程序中的任务数。  
  
 `pNumberOfTasksEnqueued`  
 所有计划程序队列中的任务总数。  
  
### <a name="remarks"></a>备注  
 调用此方法以计划程序收集统计信息由资源管理器。 此处收集的统计信息将用于驱动动态反馈算法来确定何时需要将更多资源分配给计划程序，以及何时占用资源。 计划程序提供的值可以是开放式，并不一定需要准确地反映当前的计数。  
  
 如果希望资源管理器使用有关任务到达等的反馈来确定如何平衡您的计划程序和向资源管理器注册的其他计划程序之间的资源，则应实现此方法。 如果你选择不收集统计信息，则可以设置的策略键`DynamicProgressFeedback`为值`DynamicProgressFeedbackDisabled`中您的计划程序策略和资源管理器将不会调用此方法在你计划程序上的。  
  
 在没有的统计信息的情况下，资源管理器将使用硬件线程订阅级别来决定资源分配和迁移。 在订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [SchedulerPolicy 类](schedulerpolicy-class.md)   
 [IExecutionContext 结构](iexecutioncontext-structure.md)   
 [IThreadProxy 结构](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)   
 [IResourceManager 结构](iresourcemanager-structure.md)
