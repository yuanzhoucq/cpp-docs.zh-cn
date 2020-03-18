---
title: IExecutionResource 结构
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 40799d1ed6e21e6932f1adfbad117c436918b792
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424259"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource 结构

硬件线程的抽象。

## <a name="syntax"></a>语法

```cpp
struct IExecutionResource;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IExecutionResource：： CurrentSubscriptionLevel](#currentsubscriptionlevel)|返回已激活的虚拟处理器根和当前与此执行资源所表示的基础硬件线程关联的已订阅外部线程的数目。|
|[IExecutionResource：： GetExecutionResourceId](#getexecutionresourceid)|返回此执行资源所表示的硬件线程的唯一标识符。|
|[IExecutionResource：： GetNodeId](#getnodeid)|返回此执行资源所属的处理器节点的唯一标识符。|
|[IExecutionResource：： Remove](#remove)|将此执行资源返回到资源管理器。|

## <a name="remarks"></a>备注

执行资源可以是独立的，也可以与虚拟处理器根关联。 当应用程序中的线程创建线程订阅时，将创建独立的执行资源。 方法[ISchedulerProxy：： SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread)和[ISchedulerProxy：： RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)创建线程订阅，并返回表示订阅的 `IExecutionResource` 接口。 创建线程订阅是一种通知资源管理器给定线程将参与排队等候计划程序的工作的方法，并资源管理器分配给计划程序的虚拟处理器根。 资源管理器使用该信息来避免需要超额订阅硬件线程。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IExecutionResource`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="currentsubscriptionlevel"></a>IExecutionResource：： CurrentSubscriptionLevel 方法

返回已激活的虚拟处理器根和当前与此执行资源所表示的基础硬件线程关联的已订阅外部线程的数目。

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>返回值

当前订阅级别。

### <a name="remarks"></a>备注

订阅级别告诉你正在运行的线程数与硬件线程关联。 这仅包括资源管理器可以识别的线程，其中包含已订阅线程的形式，以及主动执行线程代理的虚拟处理器根。

如果调用方法[ISchedulerProxy：： SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)或方法[ISchedulerProxy：： RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)的参数 `doSubscribeCurrentThread` 设置为值**true，则**会将硬件线程的订阅级别递增1。 它们还返回表示订阅的 `IExecutionResource` 接口。 对应于[IExecutionResource：： Remove](#remove)的调用会将硬件线程的订阅级别减一。

使用[IVirtualProcessorRoot：： Activate](ivirtualprocessorroot-structure.md#activate)方法激活虚拟处理器根的操作将硬件线程的订阅级别增加1。 方法[IVirtualProcessorRoot:D：](ivirtualprocessorroot-structure.md#deactivate)在激活的虚拟处理器根上调用时，Eactivate 或[IExecutionResource：： Remove](#remove)会将订阅级别减一。

资源管理器使用订阅级信息作为确定何时在计划程序之间移动资源的一种方式。

## <a name="getexecutionresourceid"></a>IExecutionResource：： GetExecutionResourceId 方法

返回此执行资源所表示的硬件线程的唯一标识符。

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>返回值

此执行资源基础的硬件线程的唯一标识符。

### <a name="remarks"></a>备注

并发运行时为每个硬件线程分配一个唯一标识符。 如果多个执行资源与硬件线程关联，则它们将具有相同的执行资源标识符。

## <a name="getnodeid"></a>IExecutionResource：： GetNodeId 方法

返回此执行资源所属的处理器节点的唯一标识符。

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>返回值

处理器节点的唯一标识符。

### <a name="remarks"></a>备注

并发运行时表示处理器节点组中系统上的硬件线程。 节点通常派生自系统的硬件拓扑。 例如，特定套接字或特定 NUMA 节点上的所有处理器可能属于同一处理器节点。 资源管理器将唯一标识符分配到这些节点，从 `0` 到（包括 `nodeCount - 1`）开始，其中 `nodeCount` 表示系统上的处理器节点的总数。

可以从函数[GetProcessorNodeCount](concurrency-namespace-functions.md)获取节点计数。

## <a name="remove"></a>IExecutionResource：： Remove 方法

将此执行资源返回到资源管理器。

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>parameters

*pScheduler*<br/>
向计划程序发出请求以删除此执行资源的接口。

### <a name="remarks"></a>备注

使用此方法将独立的执行资源以及与虚拟处理器根关联的执行资源返回到资源管理器。

如果这是从[ISchedulerProxy：： SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)或[ISchedulerProxy：： RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)的任一方法接收到的独立执行资源，则调用方法 `Remove` 将结束创建该资源所表示的线程订阅。 需要先结束所有线程订阅，然后才能关闭计划程序代理，并且必须从创建该订阅的线程调用 `Remove`。

虚拟处理器根也可返回至资源管理器，通过调用 `Remove` 方法实现，因为接口 `IVirtualProcessorRoot` 继承自 `IExecutionResource` 接口。 你可能需要返回虚拟处理器根，以响应对[IScheduler：： RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors)方法的调用，或在你完成从[ISchedulerProxy：： CreateOversubscriber](ischedulerproxy-structure.md#createoversubscriber)方法获取的超额订阅虚拟处理器根时返回。 对于虚拟处理器根，对哪个线程可以调用 `Remove` 方法没有任何限制。

如果参数 `pScheduler` 设置为 `NULL`，则会引发 `invalid_argument`。

如果参数 `pScheduler` 不同于为其创建此执行资源的计划程序，则会引发 `invalid_operation`; 如果当前线程与创建线程订阅的线程不同，则会引发。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)
