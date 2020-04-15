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
ms.openlocfilehash: 4305948aa4e5da36023c1d4fe8b0b84aa4d59e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377317"
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
|[I 执行资源：当前订阅级别](#currentsubscriptionlevel)|返回当前与此执行资源表示的基础硬件线程关联的已激活的虚拟处理器根和已订阅的外部线程的数量。|
|[I 执行资源：获取执行资源 ID](#getexecutionresourceid)|返回此执行资源表示的硬件线程的唯一标识符。|
|[I 执行资源：：获取NodeId](#getnodeid)|返回此执行资源所属的处理器节点的唯一标识符。|
|[I 执行资源：删除](#remove)|将此执行资源返回到资源管理器。|

## <a name="remarks"></a>备注

执行资源可以是独立的或与虚拟处理器根关联的。 当应用程序中的线程创建线程订阅时，将创建独立的执行资源。 方法[I计划代理：订阅线程](ischedulerproxy-structure.md#subscribecurrentthread)和[I计划代理：请求初始虚拟处理器](ischedulerproxy-structure.md#requestinitialvirtualprocessors)创建线程订阅，并返回表示订阅的`IExecutionResource`接口。 创建线程订阅是通知资源管理器给定线程将参与排队到计划程序的工作以及分配给计划程序的虚拟处理器根资源管理器的一种方式。 资源管理器使用这些信息来避免在可以的地方过度订阅硬件线程。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IExecutionResource`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a>I 执行资源：：当前订阅级别方法

返回当前与此执行资源表示的基础硬件线程关联的已激活的虚拟处理器根和已订阅的外部线程的数量。

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>返回值

当前订阅级别。

### <a name="remarks"></a>备注

订阅级别告诉您与硬件线程关联的正在运行的线程数。 这仅包括资源管理器以订阅线程的形式知道的线程，以及正在积极执行线程代理的虚拟处理器根。

调用方法[I-计划代理：：订阅CurrentThread](ischedulerproxy-structure.md#subscribecurrentthread)，或方法[I-计划代理：请求初始虚拟处理器](ischedulerproxy-structure.md#requestinitialvirtualprocessors)，参数`doSubscribeCurrentThread`设置为值**true**将硬件线程的订阅级别增加一个。 它们还会返回表示`IExecutionResource`订阅的接口。 对[I 执行资源：：将](#remove)硬件线程的订阅级别除以一次。

使用[IVirtualProcessorRoot：：激活](ivirtualprocessorroot-structure.md#activate)虚拟处理器根的行为将硬件线程的订阅级别增加一个。 当在激活的虚拟处理器根目录上调用时，方法[IVirtualProcessorRoot：:Deeactivate，](ivirtualprocessorroot-structure.md#deactivate)[或 I执行资源：在](#remove)激活的虚拟处理器根上调用时，将订阅级别除以一。

资源管理器使用订阅级别信息作为确定何时在计划程序之间移动资源的方法之一。

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a>I 执行资源：获取执行资源 Id 方法

返回此执行资源表示的硬件线程的唯一标识符。

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>返回值

此执行资源的基础硬件线程的唯一标识符。

### <a name="remarks"></a>备注

每个硬件线程由并发运行时分配一个唯一标识符。 如果多个执行资源是关联的硬件线程，则它们都将具有相同的执行资源标识符。

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a>I 执行资源：getNodeId 方法

返回此执行资源所属的处理器节点的唯一标识符。

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>返回值

处理器节点的唯一标识符。

### <a name="remarks"></a>备注

并发运行时以处理器节点组表示系统上的硬件线程。 节点通常派生自系统的硬件拓扑。 例如，特定套接字或特定 NUMA 节点上的所有处理器可能属于同一处理器节点。 资源管理器为这些节点分配唯一标识符，从`0`最多和包括`nodeCount - 1`开始，其中`nodeCount`表示系统上的处理器节点总数。

节点计数可以从函数[GetProcessorNodeCount](concurrency-namespace-functions.md)获得。

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a>I 执行资源：：删除方法

将此执行资源返回到资源管理器。

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>参数

*p时间*<br/>
向计划程序发出删除此执行资源的请求的接口。

### <a name="remarks"></a>备注

使用此方法将独立执行资源以及与虚拟处理器根关联的执行资源返回到资源管理器。

如果这是从其中一种方法[I-计划代理：：订阅电流线程](ischedulerproxy-structure.md#subscribecurrentthread)或[I-计划代理：请求初始虚拟处理器](ischedulerproxy-structure.md#requestinitialvirtualprocessors)接收的独立执行资源，则调用该方法`Remove`将结束创建资源表示的线程订阅。 您需要在关闭计划程序代理之前结束所有线程订阅，并且必须从创建订阅的线程调用`Remove`。

虚拟处理器根也可返回至资源管理器，通过调用 `Remove` 方法实现，因为接口 `IVirtualProcessorRoot` 继承自 `IExecutionResource` 接口。 您可能需要返回虚拟处理器根，以响应对[I-计划器：：：删除虚拟处理器](ischeduler-structure.md#removevirtualprocessors)方法的调用，或者当您使用从[I-计划代理代理：create 超额订阅方法](ischedulerproxy-structure.md#createoversubscriber)获取的超额订阅虚拟处理器根时。 对于虚拟处理器根，没有限制哪个线程可以调用该方法`Remove`。

`invalid_argument`如果参数`pScheduler`设置为`NULL`，则引发 。

`invalid_operation`如果参数`pScheduler`不同于为此执行资源创建的计划程序，或者使用独立执行资源（如果当前线程与创建线程订阅的线程不同），则引发该参数。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)
