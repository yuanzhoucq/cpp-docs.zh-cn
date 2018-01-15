---
title: "ISchedulerProxy 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b151e68c9cce0113c46f0eaffff8e19ed4d5c896
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[Ischedulerproxy:: Bindcontext](#bindcontext)|执行上下文将与相关联的线程代理，如果尚未与一个相关联。|  
|[Ischedulerproxy:: Createoversubscriber](#createoversubscriber)|在与现有的执行资源相关的硬件线程上创建新的虚拟处理器根。|  
|[Ischedulerproxy:: Requestinitialvirtualprocessors](#requestinitialvirtualprocessors)|请求的虚拟处理器根的初始分配。 每个虚拟处理器根表示执行可执行工作计划程序的一个线程的功能。|  
|[Ischedulerproxy:: Shutdown](#shutdown)|通知资源管理器调度器正在关闭。 这将导致要立即回收授予到调度器的所有资源的资源管理器。|  
|[Ischedulerproxy:: Subscribecurrentthread](#subscribecurrentthread)|注册当前线程使用资源管理器，将它与此计划程序相关联。|  
|[Ischedulerproxy:: Unbindcontext](#unbindcontext)|解除关联从指定的执行上下文的线程代理`pContext`参数并将其返回到的线程代理工厂可用池。 可能仅在通过绑定的执行上下文中调用此方法[ischedulerproxy:: Bindcontext](#bindcontext)方法尚未启动通过正在`pContext`参数[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法调用。|  
  
## <a name="remarks"></a>备注  
 资源管理器将传递`ISchedulerProxy`注册使用每个计划程序接口[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ISchedulerProxy`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="bindcontext"></a>Ischedulerproxy:: Bindcontext 方法  
 执行上下文将与相关联的线程代理，如果尚未与一个相关联。  
  
```
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 一个接口到执行上下文，以将与线程代理相关联。  
  
### <a name="remarks"></a>备注  
 通常情况下， [ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法将对按需执行上下文绑定的线程代理。 有，但是，需要将绑定的上下文提前以确保其所在的情况下`SwitchTo`方法转换为已绑定上下文。 这是上 UMS 计划上下文，因为其无法调用方法，以分配内存，这种情况，而绑定的线程代理可能会涉及内存分配，如果线程代理不在可用池的线程代理工厂尚不可用。  
  
 `invalid_argument`如果引发参数`pContext`具有值`NULL`。  
  
##  <a name="createoversubscriber"></a>Ischedulerproxy:: Createoversubscriber 方法  
 在与现有的执行资源相关的硬件线程上创建新的虚拟处理器根。  
  
```
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pExecutionResource`  
 `IExecutionResource`表示所需资源的硬件线程的接口。  
  
### <a name="return-value"></a>返回值  
 一个 `IVirtualProcessorRoot` 接口。  
  
### <a name="remarks"></a>备注  
 当您的计划程序想要为有限的时间内资源的特定硬件线程，请使用此方法。 一旦完成虚拟处理器根，则应返回其与资源管理器通过调用[删除](iexecutionresource-structure.md#remove)方法`IVirtualProcessorRoot`接口。  
  
 您甚至可以过度订阅现有虚拟处理器根，因为 `IVirtualProcessorRoot` 接口继承自 `IExecutionResource` 接口。  
  
##  <a name="requestinitialvirtualprocessors"></a>Ischedulerproxy:: Requestinitialvirtualprocessors 方法  
 请求的虚拟处理器根的初始分配。 每个虚拟处理器根表示执行可执行工作计划程序的一个线程的功能。  
  
```
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```  
  
### <a name="parameters"></a>参数  
 `doSubscribeCurrentThread`  
 是否要订阅的当前线程并在资源分配期间考虑。  
  
### <a name="return-value"></a>返回值  
 `IExecutionResource`接口当前线程中，如果参数`doSubscribeCurrentThread`具有值`true`。 如果值为`false`，该方法返回`NULL`。  
  
### <a name="remarks"></a>备注  
 在计划程序执行任何工作之前，它应使用此方法来请求来自资源管理器中的虚拟处理器根。 资源管理器将访问计划程序的策略使用[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)的策略键使用的值和`MinConcurrency`，`MaxConcurrency`和`TargetOversubscriptionFactor`来确定要分配给的硬件线程数计划程序最初和多少虚拟处理器根，以创建针对每个硬件线程。 有关如何使用计划程序策略来确定计划程序的初始分配的详细信息，请参阅[PolicyElementKey](concurrency-namespace-enums.md)。  
  
 资源管理器通过调用方法，将资源授予计划程序[ischeduler:: Addvirtualprocessors](ischeduler-structure.md#addvirtualprocessors)的虚拟处理器根的列表。 方法是为回调到调度器之前调用此方法返回。  
  
 如果计划程序将当前线程的订阅请求通过将参数设置`doSubscribeCurrentThread`到`true`，该方法返回`IExecutionResource`接口。 订阅必须通过使用终止稍后[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。  
  
 在确定选择哪个硬件线程，资源管理器将尝试针对处理器节点关联进行优化。 如果当前线程请求订阅，则它是指示当前线程计划参与分配给此计划程序的工作。 在这种情况下，分配的虚拟处理器根都位于当前线程在其执行，如有可能的处理器节点。  
  
 订阅一个线程都将使基础硬件线程的订阅级别加一。 当终止订阅时，将通过一个减少订阅级别。 在订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="shutdown"></a>Ischedulerproxy:: Shutdown 方法  
 通知资源管理器调度器正在关闭。 这将导致要立即回收授予到调度器的所有资源的资源管理器。  
  
```
virtual void Shutdown() = 0;
```  
  
### <a name="remarks"></a>备注  
 所有`IExecutionContext`接口接收由于订阅使用的方法的外部线程计划程序`ISchedulerProxy::RequestInitialVirtualProcessors`或`ISchedulerProxy::SubscribeCurrentThread`必须返回到资源管理器使用`IExecutionResource::Remove`计划程序本身关闭之前。  
  
 如果您的计划程序有任何停用的虚拟处理器根，你必须激活它们使用[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)，并且具有在其上执行的线程代理将保留`Dispatch`执行的方法它们调度之前调用的上下文`Shutdown`计划程序代理服务器上。  
  
 计划程序不需要通过调用 `Remove` 方法分别返回资源管理器授予它的所有虚拟处理器根，因为关机时所有虚拟处理器根都将返回到资源管理器。  
  
##  <a name="subscribecurrentthread"></a>Ischedulerproxy:: Subscribecurrentthread 方法  
 注册当前线程使用资源管理器，将它与此计划程序相关联。  
  
```
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```  
  
### <a name="return-value"></a>返回值  
 `IExecutionResource`交互表示当前线程在运行时中。  
  
### <a name="remarks"></a>备注  
 如果你想要将资源分配给您的计划程序和其他计划程序时考虑当前线程的资源管理器，请使用此方法。 它在线程计划参与工作排队到你计划程序，以及计划程序接收来自资源管理器中的虚拟处理器根时特别有用。 资源管理器使用的信息来防止不必要的系统上的硬件线程的过度订阅。  
  
 通过此方法接收的执行资源应返回到资源管理器使用[iexecutionresource:: Remove](iexecutionresource-structure.md#remove)方法。 调用的线程`Remove`方法必须是之前调用的相同线程`SubscribeCurrentThread`方法。  
  
 订阅一个线程都将使基础硬件线程的订阅级别加一。 当终止订阅时，将通过一个减少订阅级别。 在订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="unbindcontext"></a>Ischedulerproxy:: Unbindcontext 方法  
 解除关联从指定的执行上下文的线程代理`pContext`参数并将其返回到的线程代理工厂可用池。 可能仅在通过绑定的执行上下文中调用此方法[ischedulerproxy:: Bindcontext](#bindcontext)方法尚未启动通过正在`pContext`参数[ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)方法调用。  
  
```
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 若要从其线程代理解除关联执行上下文。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IThreadProxy 结构](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)   
 [IResourceManager 结构](iresourcemanager-structure.md)
