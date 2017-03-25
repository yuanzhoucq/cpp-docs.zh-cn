---
title: "IScheduler 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 24305fbdded1709ec51270b3a29a239b345a5679
ms.lasthandoff: 03/17/2017

---
# <a name="ischeduler-structure"></a>IScheduler 结构
工作计划程序的抽象的接口。 并发运行时的资源管理器使用此接口与工作计划程序进行通信。  
  
## <a name="syntax"></a>语法  
  
```
struct IScheduler;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Ischeduler:: Addvirtualprocessors](#addvirtualprocessors)|为计划程序供其使用提供的虚拟处理器根的一组中。 每个`IVirtualProcessorRoot`接口表示执行单个线程可以执行代表计划程序作业的权限。|  
|[Ischeduler:: Getid](#getid)|返回计划程序的唯一标识符。|  
|[Ischeduler:: Getpolicy](#getpolicy)|返回计划程序的策略的副本。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。|  
|[Ischeduler:: Notifyresourcesexternallybusy](#notifyresourcesexternallybusy)|通知此计划程序的数组中的虚拟处理器根的集所表示的硬件线程`ppVirtualProcessorRoots`现在正在使用的其他计划程序。|  
|[Ischeduler:: Notifyresourcesexternallyidle](#notifyresourcesexternallyidle)|通知此计划程序的数组中的虚拟处理器根的集所表示的硬件线程`ppVirtualProcessorRoots`未正在由其他计划程序。|  
|[Ischeduler:: Removevirtualprocessors](#removevirtualprocessors)|启动之前分配给此计划程序的虚拟处理器根的删除。|  
|[Ischeduler:: Statistics](#statistics)|提供与任务到达和完成率和队列长度更改的计划程序相关的信息。|  
  
## <a name="remarks"></a>备注  
 如果要实现与资源管理器进行通信的自定义计划，则应提供的实现`IScheduler`接口。 此接口是通信的一个计划程序和资源管理器之间的双向通道的一端。 另一端都由`IResourceManager`和`ISchedulerProxy`实现资源管理器的接口。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IScheduler`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="addvirtualprocessors"></a>Ischeduler:: Addvirtualprocessors 方法  
 为计划程序供其使用提供的虚拟处理器根的一组中。 每个`IVirtualProcessorRoot`接口表示执行单个线程可以执行代表计划程序作业的权限。  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 一个数组`IVirtualProcessorRoot`接口表示虚拟处理器根添加到计划程序。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 资源管理器时，将调用`AddVirtualProcessor`方法到一个计划程序授予一组初始虚拟处理器根。 它还可以调用该方法时重新平衡计划之间的资源添加到计划程序的虚拟处理器根。  
  
##  <a name="getid"></a>Ischeduler:: Getid 方法  
 返回计划程序的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个唯一整数标识符。  
  
### <a name="remarks"></a>备注  
 应使用[GetSchedulerId](concurrency-namespace-functions.md)函数来获取实现的对象的唯一标识符`IScheduler`接口，然后以参数形式向方法使用该接口提供由资源管理器。 您应返回相同的标识符时`GetId`调用函数。  
  
 获取从不同源的标识符可能导致未定义的行为。  
  
##  <a name="getpolicy"></a>Ischeduler:: Getpolicy 方法  
 返回计划程序的策略的副本。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 计划程序的策略的副本。  
  
##  <a name="notifyresourcesexternallybusy"></a>Ischeduler:: Notifyresourcesexternallybusy 方法  
 通知此计划程序的数组中的虚拟处理器根的集所表示的硬件线程`ppVirtualProcessorRoots`现在正在使用的其他计划程序。  
  
```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 一个数组`IVirtualProcessorRoot`与在其的其他计划程序已变得繁忙的硬件线程关联的接口。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 就可以为特定的硬件线程同时要分配给多个计划程序。 一种的原因可能是为了满足最小并发的所有计划程序，而不共享资源系统上没有足够的硬件线程。 另一种可能性是将资源暂时分配到其他计划程序拥有的计划程序不使用时，通过正被停用该硬件线程上的所有虚拟处理器根。  
  
 硬件线程的订阅级别为由已订阅的线程数和激活与该硬件线程相关联的虚拟处理器根。 从特定计划程序的角度来看，硬件线程的外部订阅级别是的订阅的其他计划程序贡献的部分。 当硬件线程的外部订阅级别将从零到正范围移到一个计划程序发送通知的资源是外部繁忙。  
  
 通过此方法通知只发送到计划程序有一个策略，其中的值为`MinConcurrency`策略的注册表项是否等于的值`MaxConcurrency`策略的注册表项。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 有资格获得通知的计划获取一的组初始通知时创建它时，通知它刚分配的资源外部正忙还是空闲。  
  
##  <a name="notifyresourcesexternallyidle"></a>Ischeduler:: Notifyresourcesexternallyidle 方法  
 通知此计划程序的数组中的虚拟处理器根的集所表示的硬件线程`ppVirtualProcessorRoots`未正在由其他计划程序。  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 一个数组`IVirtualProcessorRoot`硬件线程的其他计划程序已进入空闲状态与关联的接口。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 就可以为特定的硬件线程同时要分配给多个计划程序。 一种的原因可能是为了满足最小并发的所有计划程序，而不共享资源系统上没有足够的硬件线程。 另一种可能性是将资源暂时分配到其他计划程序拥有的计划程序不使用时，通过正被停用该硬件线程上的所有虚拟处理器根。  
  
 硬件线程的订阅级别为由已订阅的线程数和激活与该硬件线程相关联的虚拟处理器根。 从特定计划程序的角度来看，硬件线程的外部订阅级别是的订阅的其他计划程序贡献的部分。 资源是外部繁忙发送通知到一个计划程序的硬件线程的外部订阅级别降到零时从先前的正数值。  
  
 通过此方法通知只发送到计划程序有一个策略，其中的值为`MinConcurrency`策略的注册表项是否等于的值`MaxConcurrency`策略的注册表项。 计划程序策略的详细信息，请参阅[SchedulerPolicy](schedulerpolicy-class.md)。  
  
 有资格获得通知的计划获取一的组初始通知时创建它时，通知它刚分配的资源外部正忙还是空闲。  
  
##  <a name="removevirtualprocessors"></a>Ischeduler:: Removevirtualprocessors 方法  
 启动之前分配给此计划程序的虚拟处理器根的删除。  
  
```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>参数  
 `ppVirtualProcessorRoots`  
 一个数组`IVirtualProcessorRoot`表示要删除的虚拟处理器根的接口。  
  
 `count`  
 数`IVirtualProcessorRoot`数组中的接口。  
  
### <a name="remarks"></a>备注  
 资源管理器时，将调用`RemoveVirtualProcessors`方法，以从计划程序带回虚拟处理器根的一组。 计划程序则应调用[删除](iexecutionresource-structure.md#remove)完成与虚拟处理器根的每个接口上的方法。 请不要使用`IVirtualProcessorRoot`接口一旦已经调用`Remove`在其上的方法。  
  
 该参数`ppVirtualProcessorRoots`指向的接口的数组。 在虚拟处理器根，要删除的组，之间，永远不会被激活的根可以立即使用返回`Remove`方法。 应以异步方式返回已激活，并任一正在执行的工作或已被停用、 等待工作到达时，这些根。 计划程序必须进行每次尝试尽可能快地删除的虚拟处理器根。 延迟删除的虚拟处理器根的可能会导致意外的过度订阅的计划程序中。  
  
##  <a name="statistics"></a>Ischeduler:: Statistics 方法  
 提供与任务到达和完成率和队列长度更改的计划程序相关的信息。  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pTaskCompletionRate`  
 自上次调用此方法由计划程序完成的任务数。  
  
 `pTaskArrivalRate`  
 自上次对此方法调用到达在计划程序中的任务数。  
  
 `pNumberOfTasksEnqueued`  
 所有计划程序队列中的任务的总数。  
  
### <a name="remarks"></a>备注  
 为了收集计划程序的统计信息由资源管理器中调用此方法。 在此处收集的统计信息将用于驱动动态反馈算法来确定适合的计划程序分配更多资源，以及何时拿走资源。 计划程序所提供的值可以是开放式的并不一定需要准确地反映当前的计数。  
  
 如果希望资源管理器使用有关任务到达等的反馈来确定如何平衡您的计划程序和向资源管理器注册的其他计划程序之间的资源，则应实现此方法。 如果您选择不收集统计信息，则可以设置的策略键`DynamicProgressFeedback`为值`DynamicProgressFeedbackDisabled`在您的计划程序策略，并将资源管理器将不会调用您的计划程序上的此方法。  
  
 在缺少统计信息的情况下，资源管理器将使用硬件线程订阅级别若要使资源分配和迁移决策。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [SchedulerPolicy 类](schedulerpolicy-class.md)   
 [IExecutionContext 结构](iexecutioncontext-structure.md)   
 [IThreadProxy 结构](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)   
 [IResourceManager 结构](iresourcemanager-structure.md)

