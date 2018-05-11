---
title: IExecutionResource 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
dev_langs:
- C++
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc69c30f30d25179427ee8e59c536bb7cb5b483d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="iexecutionresource-structure"></a>IExecutionResource 结构
硬件线程的抽象。  
  
## <a name="syntax"></a>语法  
  
```
struct IExecutionResource;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|返回数激活的虚拟处理器根和订阅当前与此执行资源表示的基础硬件线程关联的外部线程。|  
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|返回此执行资源表示的硬件线程的唯一标识符。|  
|[IExecutionResource::GetNodeId](#getnodeid)|返回此执行资源所属的处理器节点的唯一标识符。|  
|[IExecutionResource::Remove](#remove)|返回此执行资源到资源管理器。|  
  
## <a name="remarks"></a>备注  
 执行资源可以是独立或与虚拟处理器根。 你的应用程序中的线程创建的线程订阅时，将创建独立执行资源。 方法[ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread)和[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)创建线程订阅，并返回`IExecutionResource`接口表示订阅。 创建线程订阅是一种方法通知资源管理器的给定的线程将参与工作排队到计划程序，以及资源管理器将分配给计划程序的虚拟处理器根。 资源管理器使用的信息以避免超额订阅硬件线程，它可在其中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IExecutionResource`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="currentsubscriptionlevel"></a>  Iexecutionresource:: Currentsubscriptionlevel 方法  
 返回数激活的虚拟处理器根和订阅当前与此执行资源表示的基础硬件线程关联的外部线程。  
  
```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 当前订阅级别。  
  
### <a name="remarks"></a>备注  
 订阅级别告诉您多少正在运行的线程与硬件线程关联。 这只包括资源管理器是感知的订阅的线程和主动执行线程代理的虚拟处理器根的窗体中的线程。  
  
 调用方法[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)，或该方法[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)与参数`doSubscribeCurrentThread`设置为值`true`递增 1 硬件线程的订阅级别。 它们还返回`IExecutionResource`表示订阅的接口。 相应地调用[iexecutionresource:: Remove](#remove)递减 1 的硬件线程的订阅级别。  
  
 激活使用方法的虚拟处理器根的 act [ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)递增 1 硬件线程的订阅级别。 方法[ivirtualprocessorroot:: Deactivate](ivirtualprocessorroot-structure.md#deactivate)，或[iexecutionresource:: Remove](#remove)逐个激活的虚拟处理器根上调用时递减订阅级别。  
  
 资源管理器使用作为一种用于确定何时要计划程序之间移动资源的订阅级别的信息。  
  
##  <a name="getexecutionresourceid"></a>  Iexecutionresource:: Getexecutionresourceid 方法  
 返回此执行资源表示的硬件线程的唯一标识符。  
  
```
virtual unsigned int GetExecutionResourceId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 基础此执行资源的硬件线程的唯一标识符。  
  
### <a name="remarks"></a>备注  
 每个硬件线程由并发运行时分配的唯一标识符。 如果多个执行资源相关联的硬件线程，它们将具有相同的执行资源标识符。  
  
##  <a name="getnodeid"></a>  Iexecutionresource:: Getnodeid 方法  
 返回此执行资源所属的处理器节点的唯一标识符。  
  
```
virtual unsigned int GetNodeId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 处理器节点的唯一标识符。  
  
### <a name="remarks"></a>备注  
 并发运行时表示的处理器节点组中的系统上的硬件线程。 节点通常被派生自系统的硬件拓扑。 例如，特定的套接字或特定的 NUMA 节点上的所有处理器可能都属于同一处理器节点。 资源管理器将分配给从这些节点的唯一标识符`0`包括`nodeCount - 1`，其中`nodeCount`表示系统上的处理器节点的总数。  
  
 可以从函数获取节点的计数[GetProcessorNodeCount](concurrency-namespace-functions.md)。  
  
##  <a name="remove"></a>  Iexecutionresource:: Remove 方法  
 返回此执行资源到资源管理器。  
  
```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pScheduler`  
 到要发出请求以删除此执行资源的计划程序接口。  
  
### <a name="remarks"></a>备注  
 使用此方法返回独立执行资源，以及与虚拟处理器根到资源管理器关联的执行资源。  
  
 如果这是独立执行资源接收从两种方法之一[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)或[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)，则调用方法`Remove`将结束到创建该资源的线程订阅表示。 你需要在关闭计划程序代理之前，结束所有线程订阅并必须调用`Remove`从创建订阅的线程。  
  
 虚拟处理器根也可返回至资源管理器，通过调用 `Remove` 方法实现，因为接口 `IVirtualProcessorRoot` 继承自 `IExecutionResource` 接口。 你可能需要返回到调用的响应中的虚拟处理器根[ischeduler:: Removevirtualprocessors](ischeduler-structure.md#removevirtualprocessors)方法，或当你完成从获取超额订阅的虚拟处理器根[Ischedulerproxy:: Createoversubscriber](ischedulerproxy-structure.md#createoversubscriber)方法。 对于虚拟处理器根没有任何限制对哪个线程可以调用`Remove`方法。  
  
 `invalid_argument` 如果引发参数`pScheduler`设置为`NULL`。  
  
 `invalid_operation` 如果引发参数`pScheduler`不同于创建线程订阅线程当前线程是否是不同于此执行资源是否已创建，或与独立执行资源，计划程序。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)
