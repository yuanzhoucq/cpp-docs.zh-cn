---
title: ISchedulerProxy 结构
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: f4a9e79c2da56406610ad6da08fb438e2f92923d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368161"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy 结构

计划程序用来与并发运行时的资源管理器进行通信以协商资源分配的接口。

## <a name="syntax"></a>语法

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I计划代理：：绑定上下文](#bindcontext)|如果执行上下文尚未与线程代理关联，则将其关联为线程代理。|
|[I计划代理：：创建超额订阅者](#createoversubscriber)|在与现有执行资源关联的硬件线程上创建新的虚拟处理器根。|
|[I计划代理：：请求初始虚拟处理器](#requestinitialvirtualprocessors)|请求初始分配虚拟处理器根。 每个虚拟处理器根表示能够执行一个线程，该线程可以执行计划程序的工作。|
|[I计划代理：：关闭](#shutdown)|通知资源管理器计划程序正在关闭。 这将导致资源管理器立即回收授予计划程序的所有资源。|
|[I计划代理：：订阅当前线程](#subscribecurrentthread)|将当前线程注册到资源管理器，将其与此计划程序关联。|
|[I计划代理：：取消绑定上下文](#unbindcontext)|将线程代理与参数指定的执行上下文分离，`pContext`并将其返回到线程代理工厂的可用池。 此方法只能在通过[I-计划代理：：绑定上下文](#bindcontext)绑定的执行上下文中调用，并且尚未通过[IThreadProxy：：：switchto](ithreadproxy-structure.md#switchto)方法调用的`pContext`参数启动。|

## <a name="remarks"></a>备注

资源管理器使用`ISchedulerProxy`[IResourceManager ：：注册计划器](iresourcemanager-structure.md#registerscheduler)方法将接给与其一起注册的每个计划程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ISchedulerProxy`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>I计划代理：：绑定上下文方法

如果执行上下文尚未与线程代理关联，则将其关联为线程代理。

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
要与线程代理关联的执行上下文的接口。

### <a name="remarks"></a>备注

通常[，IThreadProxy：：SwitchTo](ithreadproxy-structure.md#switchto)方法将按需将线程代理绑定到执行上下文。 但是，在某些情况下，需要提前绑定上下文，以确保`SwitchTo`方法切换到已绑定的上下文。 UMS 调度上下文中就是这种情况，因为它无法调用分配内存的方法，如果线程代理在线程代理工厂的可用池中不容易可用，则绑定线程代理可能涉及内存分配。

`invalid_argument`如果参数`pContext`具有 值`NULL`，则引发 。

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>I计划代理：：创建超额订阅者方法

在与现有执行资源关联的硬件线程上创建新的虚拟处理器根。

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>参数

*p 执行资源*<br/>
表示`IExecutionResource`要超额订阅的硬件线程的接口。

### <a name="return-value"></a>返回值

一个 `IVirtualProcessorRoot` 接口。

### <a name="remarks"></a>备注

当您的计划程序想要在有限的时间内超额订阅特定硬件线程时，请使用此方法。 使用虚拟处理器根后，应通过在`IVirtualProcessorRoot`接口上调用[Remove](iexecutionresource-structure.md#remove)方法将其返回到资源管理器。

您甚至可以过度订阅现有虚拟处理器根，因为 `IVirtualProcessorRoot` 接口继承自 `IExecutionResource` 接口。

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>I计划代理：：请求初始虚拟处理器方法

请求初始分配虚拟处理器根。 每个虚拟处理器根表示能够执行一个线程，该线程可以执行计划程序的工作。

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>参数

*完成订阅当前线程*<br/>
是否订阅当前线程并在资源分配期间对它进行帐户处理。

### <a name="return-value"></a>返回值

如果`IExecutionResource`参数`doSubscribeCurrentThread`的值**为 true**，则当前线程的接口。 如果值为**false，** 则 该方法将返回 NULL。

### <a name="remarks"></a>备注

在计划程序执行任何工作之前，它应该使用此方法从资源管理器请求虚拟处理器根。 资源管理器将使用[I-计划器：：getPolicy](ischeduler-structure.md#getpolicy)访问计划程序的策略，并使用策略键`MinConcurrency`的值，`MaxConcurrency`并确定`TargetOversubscriptionFactor`最初要分配给计划程序的硬件线程数以及为每个硬件线程创建多少个虚拟处理器根。 有关如何使用计划程序策略来确定计划程序的初始分配的详细信息，请参阅[策略元素键](concurrency-namespace-enums.md)。

资源管理器通过调用方法[I-计划器：：添加](ischeduler-structure.md#addvirtualprocessors)具有虚拟处理器根的列表，将资源授予计划程序。 在此方法返回之前，将该方法作为回调调用到计划程序。

如果计划程序通过将参数`doSubscribeCurrentThread`设置为**true**请求当前线程的订阅，则该方法将返回一个`IExecutionResource`接口。 必须使用[I 执行资源：：删除](iexecutionresource-structure.md#remove)方法在稍后某个点终止订阅。

确定选择哪些硬件线程时，资源管理器将尝试优化处理器节点相关性。 如果为当前线程请求订阅，则表示当前线程打算参与分配给此计划程序的工作。 在这种情况下，分配的虚拟处理器根位于当前线程执行的处理器节点上（如果可能）。

订阅线程的行为将基础硬件线程的订阅级别增加一个。 终止订阅时，订阅级别将降低 1。 有关订阅级别的详细信息，请参阅[I 执行资源：：当前订阅级别](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>I计划代理：：关闭方法

通知资源管理器计划程序正在关闭。 这将导致资源管理器立即回收授予计划程序的所有资源。

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>备注

计划`IExecutionContext`程序使用方法`ISchedulerProxy::RequestInitialVirtualProcessors`订阅外部线程后收到的所有接口，或者`ISchedulerProxy::SubscribeCurrentThread`必须在计划程序关闭之前使用`IExecutionResource::Remove`返回到资源管理器。

如果计划程序具有任何已停用的虚拟处理器根，则必须使用[IVirtualProcessorRoot：：：activate](ivirtualprocessorroot-structure.md#activate)激活它们激活它们，并且让线程代理在它们上执行，`Dispatch`在调用`Shutdown`计划程序代理之前，将离开它们正在调度的执行上下文的方法。

计划程序不需要通过调用 `Remove` 方法分别返回资源管理器授予它的所有虚拟处理器根，因为关机时所有虚拟处理器根都将返回到资源管理器。

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>I计划代理：：订阅电流线程方法

将当前线程注册到资源管理器，将其与此计划程序关联。

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>返回值

在`IExecutionResource`运行时表示当前线程的接口。

### <a name="remarks"></a>备注

如果希望资源管理器在将资源分配给计划程序和其他计划程序时考虑当前线程，请使用此方法。 当线程计划参与排队到计划程序的工作以及计划程序从资源管理器接收的虚拟处理器根时，它特别有用。 资源管理器使用信息来防止系统上硬件线程的不必要的过度订阅。

应使用[I执行资源：：删除](iexecutionresource-structure.md#remove)方法将通过此方法接收的执行资源返回到资源管理器。 调用方法的`Remove`线程必须与以前调用`SubscribeCurrentThread`该方法的线程相同。

订阅线程的行为将基础硬件线程的订阅级别增加一个。 终止订阅时，订阅级别将降低 1。 有关订阅级别的详细信息，请参阅[I 执行资源：：当前订阅级别](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>I计划代理：：取消绑定上下文方法

将线程代理与参数指定的执行上下文分离，`pContext`并将其返回到线程代理工厂的可用池。 此方法只能在通过[I-计划代理：：绑定上下文](#bindcontext)绑定的执行上下文中调用，并且尚未通过[IThreadProxy：：：switchto](ithreadproxy-structure.md#switchto)方法调用的`pContext`参数启动。

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
要与其线程代理取消关联的执行上下文。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[IScheduler 结构](ischeduler-structure.md)<br/>
[IThreadProxy 结构](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 结构](iresourcemanager-structure.md)
