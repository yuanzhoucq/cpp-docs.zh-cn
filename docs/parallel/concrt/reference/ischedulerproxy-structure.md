---
title: "ISchedulerProxy 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 3dd95150022ad94f50b456c84f7dacd2d3cef7c5
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 结构
计划程序用来与并发运行时的资源管理器进行通信以协商资源分配的接口。  
  
## <a name="syntax"></a>语法  
  
```
struct ISchedulerProxy;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Ischedulerproxy:: Bindcontext](#bindcontext)|如果尚未与之一相关联，则可以将线程代理，与关联的执行上下文。|  
|[Ischedulerproxy:: Createoversubscriber](#createoversubscriber)|在与现有的执行资源相关联的硬件线程上创建新的虚拟处理器根。|  
|[Ischedulerproxy:: Requestinitialvirtualprocessors](#requestinitialvirtualprocessors)|请求的虚拟处理器根的初始分配。 每个虚拟处理器根表示执行可执行工作计划程序的一个线程的能力。|  
|[Ischedulerproxy:: Shutdown](#shutdown)|通知资源管理器计划程序正在关闭。 这将导致资源管理器，以立即回收所有资源授予计划程序。|  
|[Ischedulerproxy:: Subscribecurrentthread](#subscribecurrentthread)|注册当前线程使用资源管理器，将其与此计划程序关联。|  
|[Ischedulerproxy:: Unbindcontext](#unbindcontext)|解除关联的线程代理从通过指定的执行上下文`pContext`参数并将其返回到线程代理工厂的可用池。 此方法仅调用通过绑定的执行上下文[ischedulerproxy:: Bindcontext](#bindcontext)方法和尚未开始通过正在`pContext`参数[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法调用。|  
  
## <a name="remarks"></a>备注  
 资源管理器将传递`ISchedulerProxy`注册使用其每个计划程序接口[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="bindcontext"></a>Ischedulerproxy:: Bindcontext 方法  
 如果尚未与之一相关联，则可以将线程代理，与关联的执行上下文。  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 执行上下文将与线程代理相关联的接口。  
  
### <a name="remarks"></a>备注  
 通常情况下， [ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法将绑定到按需执行上下文的线程代理。 有，但是，必须事先以确保将上下文绑定的情况下`SwitchTo`方法转换为已绑定上下文。 这是 UMS 调度上下文，因为其无法调用方法分配内存，在这种情况，绑定的线程代理可能涉及内存分配，如果线程代理工厂的可用池处于不随时可用的线程代理。  
  
 `invalid_argument`如果该参数`pContext`具有值`NULL`。  
  
##  <a name="createoversubscriber"></a>Ischedulerproxy:: Createoversubscriber 方法  
 在与现有的执行资源相关联的硬件线程上创建新的虚拟处理器根。  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pExecutionResource`  
 `IExecutionResource`表示过度订阅所需的硬件线程的接口。  
  
### <a name="return-value"></a>返回值  
 一个 `IVirtualProcessorRoot` 接口。  
  
### <a name="remarks"></a>备注  
 当您的计划程序想要的有限时间内过度订阅特定硬件线程，请使用此方法。 一旦完成虚拟处理器根，您将返回该资源管理器通过调用[删除](iexecutionresource-structure.md#remove)方法`IVirtualProcessorRoot`接口。  
  
 您甚至可以过度订阅现有虚拟处理器根，因为 `IVirtualProcessorRoot` 接口继承自 `IExecutionResource` 接口。  
  
##  <a name="requestinitialvirtualprocessors"></a>Ischedulerproxy:: Requestinitialvirtualprocessors 方法  
 请求的虚拟处理器根的初始分配。 每个虚拟处理器根表示执行可执行工作计划程序的一个线程的能力。  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>参数  
 `doSubscribeCurrentThread`  
 是否订阅当前线程并在资源分配期间考虑。  
  
### <a name="return-value"></a>返回值  
 `IExecutionResource`接口对于当前线程，如果该参数`doSubscribeCurrentThread`具有值`true`。 如果值为`false`，该方法返回`NULL`。  
  
### <a name="remarks"></a>备注  
 在计划程序执行任何工作之前，它应使用此方法来请求从资源管理器中的虚拟处理器根。 资源管理器将访问计划程序的策略使用[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)的策略键使用的值和`MinConcurrency`，`MaxConcurrency`和`TargetOversubscriptionFactor`来确定要分配给计划程序最初的硬件线程数和多少虚拟处理器根，若要创建针对每个硬件线程。 有关如何使用计划程序策略来确定计划程序的初始分配的详细信息，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。  
  
 资源管理器通过调用方法，将资源授予一个计划程序[ischeduler:: Addvirtualprocessors](ischeduler-structure.md#addvirtualprocessors)的虚拟处理器根的列表。 方法是为以回调形式对计划程序之前调用此方法返回。  
  
 如果计划程序通过将参数设置请求订阅的当前线程`doSubscribeCurrentThread`到`true`，该方法返回`IExecutionResource`接口。 订阅必须通过使用终止以后[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。  
  
 在确定选择哪些硬件线程，资源管理器将尝试为处理器节点关系优化。 如果当前线程的请求订阅，则指示当前线程想要参与的工作分配给此计划程序。 在这种情况下，已分配的虚拟处理器根位于当前线程在其执行，如有可能的处理器节点上。  
  
 订阅一个线程会增加一个基础硬件线程的订阅级别。 终止订阅时，将通过一个减少的订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="shutdown"></a>Ischedulerproxy:: Shutdown 方法  
 通知资源管理器计划程序正在关闭。 这将导致资源管理器，以立即回收所有资源授予计划程序。  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>备注  
 所有`IExecutionContext`接口接收作为订阅外部线程使用的方法结果的计划程序`ISchedulerProxy::RequestInitialVirtualProcessors`或`ISchedulerProxy::SubscribeCurrentThread`必须返回到资源管理器使用`IExecutionResource::Remove`计划程序自动关闭之前。  
  
 如果您的计划程序有任何已停用的虚拟处理器根，你必须激活它们使用[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)，并且具有对它们执行的线程代理将保留`Dispatch`它们调度之前调用的执行上下文的方法`Shutdown`计划程序代理服务器上。  
  
 计划程序不需要通过调用 `Remove` 方法分别返回资源管理器授予它的所有虚拟处理器根，因为关机时所有虚拟处理器根都将返回到资源管理器。  
  
##  <a name="subscribecurrentthread"></a>Ischedulerproxy:: Subscribecurrentthread 方法  
 注册当前线程使用资源管理器，将其与此计划程序关联。  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>返回值  
 `IExecutionResource`表示当前线程在运行时与之交互。  
  
### <a name="remarks"></a>备注  
 如果您希望资源管理器在将资源分配至您的计划程序和其他计划程序时考虑当前线程，请使用此方法。 它在参与到工作线程计划排队发送至您的计划程序，以及计划程序接收来自资源管理器中的虚拟处理器根时特别有用。 资源管理器使用的信息来防止不必要的系统上的硬件线程的过度订阅。  
  
 通过此方法接收到的执行资源应返回到资源管理器使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。 调用的线程`Remove`方法必须是以前调用过的同一线程`SubscribeCurrentThread`方法。  
  
 订阅一个线程会增加一个基础硬件线程的订阅级别。 终止订阅时，将通过一个减少的订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="unbindcontext"></a>Ischedulerproxy:: Unbindcontext 方法  
 解除关联的线程代理从通过指定的执行上下文`pContext`参数并将其返回到线程代理工厂的可用池。 此方法仅调用通过绑定的执行上下文[ischedulerproxy:: Bindcontext](#bindcontext)方法和尚未开始通过正在`pContext`参数[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法调用。  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 若要从其线程代理解除关联的执行上下文。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IThreadProxy 结构](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)   
 [IResourceManager 结构](iresourcemanager-structure.md)

