---
title: ISchedulerProxy 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
dev_langs:
- C++
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 189d4b4084958c2572a0a3165509acd3be6e8d23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028293"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 结构
计划程序用来与并发运行时的资源管理器进行通信以协商资源分配的接口。  
  
## <a name="syntax"></a>语法  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ISchedulerProxy::BindContext](#bindcontext)|执行上下文将与相关联的线程代理，如果尚未与一个相关联。|  
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|与现有的执行资源相关联的硬件线程上创建新的虚拟处理器根。|  
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|请求虚拟处理器根的初始分配。 每个虚拟处理器根表示执行一个线程，可以对计划程序执行工作的能力。|  
|[ISchedulerProxy::Shutdown](#shutdown)|通知资源管理器计划程序正在关闭。 这会导致要立即回收所有资源授予对计划程序的资源管理器。|  
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|注册当前线程使用资源管理器中，将它与此计划程序相关联。|  
|[ISchedulerProxy::UnbindContext](#unbindcontext)|取消关联从指定的执行上下文的线程代理`pContext`参数并将其返回到线程代理工厂的可用池。 此方法只能调用通过绑定的执行上下文[ischedulerproxy:: Bindcontext](#bindcontext)方法尚未启动通过正在`pContext`参数的[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法调用。|  
  
## <a name="remarks"></a>备注  
 资源管理器将传递`ISchedulerProxy`接口的每个计划程序将使用其注册[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="bindcontext"></a>  Ischedulerproxy:: Bindcontext 方法  
 执行上下文将与相关联的线程代理，如果尚未与一个相关联。  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
*pContext*<br/>
一个要将与线程代理相关联的执行上下文的接口。  
  
### <a name="remarks"></a>备注  
 通常情况下， [ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法将绑定到按需的执行上下文的线程代理。 但是，存在一些绑定上下文预先以确保所需的情况`SwitchTo`方法切换到已绑定上下文。 这是在 UMS 调度上下文，因为它不能调用方法分配内存，这种情况，绑定的线程代理可能涉及内存分配，如果线程代理不在可用池的线程代理工厂随时可用。  
  
 `invalid_argument` 如果引发参数`pContext`具有值`NULL`。  
  
##  <a name="createoversubscriber"></a>  Ischedulerproxy:: Createoversubscriber 方法  
 与现有的执行资源相关联的硬件线程上创建新的虚拟处理器根。  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>参数  
*pExecutionResource*<br/>
`IExecutionResource`表示你想要过度订阅的硬件线程的接口。  
  
### <a name="return-value"></a>返回值  
 一个 `IVirtualProcessorRoot` 接口。  
  
### <a name="remarks"></a>备注  
 当你的计划程序想要在有限时间超额订阅特定的硬件线程时，请使用此方法。 一旦完成虚拟处理器根，则应返回到资源管理器通过调用[删除](iexecutionresource-structure.md#remove)方法`IVirtualProcessorRoot`接口。  
  
 您甚至可以过度订阅现有虚拟处理器根，因为 `IVirtualProcessorRoot` 接口继承自 `IExecutionResource` 接口。  
  
##  <a name="requestinitialvirtualprocessors"></a>  Ischedulerproxy:: Requestinitialvirtualprocessors 方法  
 请求虚拟处理器根的初始分配。 每个虚拟处理器根表示执行一个线程，可以对计划程序执行工作的能力。  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>参数  
*doSubscribeCurrentThread*<br/>
是否要订阅的当前线程，并在资源分配期间考虑。  
  
### <a name="return-value"></a>返回值  
 `IExecutionResource`接口对于当前线程，如果将参数`doSubscribeCurrentThread`具有值`true`。 如果值为`false`，该方法将返回`NULL`。  
  
### <a name="remarks"></a>备注  
 计划程序执行任何工作之前，它应使用此方法来请求从资源管理器的虚拟处理器根。 资源管理器将访问计划程序的策略使用[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)的策略键使用的值`MinConcurrency`，`MaxConcurrency`和`TargetOversubscriptionFactor`来确定要将分配到的硬件线程数计划程序最初和多少虚拟处理器根，若要创建的每个硬件线程。 有关如何使用计划程序策略来确定计划程序的初始分配的详细信息，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。  
  
 资源管理器资源授予到计划程序通过调用方法[ischeduler:: Addvirtualprocessors](ischeduler-structure.md#addvirtualprocessors)虚拟处理器根的列表。 该方法为以回调形式对计划程序之前调用此方法返回。  
  
 如果计划程序通过将参数设置请求订阅的当前线程`doSubscribeCurrentThread`到`true`，该方法将返回`IExecutionResource`接口。 订阅必须通过使用终止在以后[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。  
  
 在确定哪些硬件线程选择时，资源管理器将尝试优化的处理器节点关联。 如果当前线程的请求订阅，则表示当前线程要参与分配给此计划程序的工作。 在这种情况下，已分配的虚拟处理器根位于当前线程在其执行，如有可能的处理器节点上。  
  
 订阅一个线程都将使基础硬件线程的订阅级别增加 1。 订阅终止时，由一个减少订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="shutdown"></a>  Ischedulerproxy:: Shutdown 方法  
 通知资源管理器计划程序正在关闭。 这会导致要立即回收所有资源授予对计划程序的资源管理器。  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>备注  
 所有`IExecutionContext`接口的计划程序收到订阅使用的方法外部线程`ISchedulerProxy::RequestInitialVirtualProcessors`或`ISchedulerProxy::SubscribeCurrentThread`必须返回到资源管理器使用`IExecutionResource::Remove`计划程序本身关闭之前。  
  
 如果你的计划程序有任何停用虚拟处理器根，则必须激活它们使用[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)，并且具有对其执行的线程代理保留`Dispatch`执行的方法它们调度之前调用的上下文`Shutdown`计划程序代理服务器上。  
  
 计划程序不需要通过调用 `Remove` 方法分别返回资源管理器授予它的所有虚拟处理器根，因为关机时所有虚拟处理器根都将返回到资源管理器。  
  
##  <a name="subscribecurrentthread"></a>  Ischedulerproxy:: Subscribecurrentthread 方法  
 注册当前线程使用资源管理器中，将它与此计划程序相关联。  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>返回值  
 `IExecutionResource`表示当前线程在运行时进行交互。  
  
### <a name="remarks"></a>备注  
 如果你想要资源分配到你的计划程序和其他计划程序时考虑当前线程的资源管理器，请使用此方法。 当线程计划以参与到工作排队到计划程序中，以及计划程序接收来自资源管理器的虚拟处理器根，它是特别有用。 资源管理器使用的信息来防止不必要的系统上的硬件线程的过度订阅。  
  
 通过此方法接收的执行资源应返回到资源管理器中使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。 调用的线程`Remove`方法必须是以前调用过的同一线程`SubscribeCurrentThread`方法。  
  
 订阅一个线程都将使基础硬件线程的订阅级别增加 1。 订阅终止时，由一个减少订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="unbindcontext"></a>  Ischedulerproxy:: Unbindcontext 方法  
 取消关联从指定的执行上下文的线程代理`pContext`参数并将其返回到线程代理工厂的可用池。 此方法只能调用通过绑定的执行上下文[ischedulerproxy:: Bindcontext](#bindcontext)方法尚未启动通过正在`pContext`参数的[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法调用。  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
*pContext*<br/>
要从其线程代理取消关联的执行上下文。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IThreadProxy 结构](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)   
 [IResourceManager 结构](iresourcemanager-structure.md)
