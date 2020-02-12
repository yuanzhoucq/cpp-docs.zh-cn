---
title: IVirtualProcessorRoot 结构
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: 60757b0edea6b60d080c2175d4df4830ffec0cc3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139883"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 结构

线程代理可在其中执行的硬件线程的抽象。

## <a name="syntax"></a>语法

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IVirtualProcessorRoot：： Activate](#activate)|使与执行上下文接口相关联的线程代理 `pContext` 开始在此虚拟处理器根上执行。|
|[IVirtualProcessorRoot：:D eactivate](#deactivate)|导致线程代理当前正在此虚拟处理器根上执行以停止调度执行上下文。 线程代理将继续在调用 `Activate` 方法时继续执行。|
|[IVirtualProcessorRoot：： EnsureAllTasksVisible](#ensurealltasksvisible)|导致存储在单个处理器的内存层次结构中的数据对系统上的所有处理器都可见。 它可确保在该方法返回之前已在所有处理器上执行了完整内存隔离。|
|[IVirtualProcessorRoot：： GetId](#getid)|返回虚拟处理器根的唯一标识符。|

## <a name="remarks"></a>备注

每个虚拟处理器根都具有关联的执行资源。 `IVirtualProcessorRoot` 接口继承自[IExecutionResource](iexecutionresource-structure.md)接口。 多个虚拟处理器根可能对应于同一个基础硬件线程。

资源管理器将虚拟处理器根向计划程序授予对资源的请求的响应。 计划程序可以通过使用执行上下文激活虚拟处理器根来执行工作。

## <a name="inheritance-hierarchy"></a>继承层次结构

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="activate"></a>IVirtualProcessorRoot：： Activate 方法

使与执行上下文接口相关联的线程代理 `pContext` 开始在此虚拟处理器根上执行。

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
将在此虚拟处理器根上调度的执行上下文的接口。

### <a name="remarks"></a>备注

如果某个线程代理与执行上下文接口无关，则资源管理器将提供该线程代理 `pContext`

`Activate` 方法可用于开始在资源管理器返回的新虚拟处理器根上执行工作，或在停用或即将停用的虚拟处理器根上恢复线程代理。 有关停用的详细信息，请参阅[IVirtualProcessorRoot：:D eactivate](#deactivate) 。 恢复停用的虚拟处理器根时，参数 `pContext` 必须与用于停用虚拟处理器根的参数相同。

第一次激活虚拟处理器根后，对 `Deactivate` 和 `Activate` 的后续调用将可能相互争用。 这意味着，资源管理器可以在 `Deactivate` 接收到 `Activate` 之前接收对的调用。

激活虚拟处理器根时，会向资源管理器发出信号，指示此虚拟处理器根当前正在忙于工作。 如果计划程序找不到任何要在此根上执行的工作，则应调用 `Deactivate` 方法，通知资源管理器虚拟处理器根处于空闲状态。 资源管理器使用此数据对系统进行负载平衡。

如果参数 `pContext` 具有值 `NULL`，则会引发 `invalid_argument`。

如果参数 `pContext` 不表示此虚拟处理器根最近调度的执行上下文，则会引发 `invalid_operation`。

激活虚拟处理器根的操作会将基础硬件线程的订阅级别增加1。 有关订阅级别的详细信息，请参阅[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="deactivate"></a>IVirtualProcessorRoot：:D eactivate 方法

导致线程代理当前正在此虚拟处理器根上执行以停止调度执行上下文。 线程代理将继续在调用 `Activate` 方法时继续执行。

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
此根当前正在调度的上下文。

### <a name="return-value"></a>返回值

一个布尔值。 如果值为**true** ，则指示线程代理从 `Deactivate` 方法返回，以响应对 `Activate` 方法的调用。 值 `false` 指示从方法返回的线程代理，以响应资源管理器中的通知事件。 在用户模式计划（UMS）线程计划程序中，这指示项已显示在计划程序的完成列表中，并且需要计划程序来处理这些项。

### <a name="remarks"></a>备注

如果在计划程序中找不到任何工作，请使用此方法来暂时停止执行虚拟处理器根。 对 `Deactivate` 方法的调用必须源自上次激活虚拟处理器根的执行上下文的 `Dispatch` 方法。 换句话说，调用 `Deactivate` 方法的线程代理必须是当前在虚拟处理器根上执行的方法。 在不执行的虚拟处理器根上调用方法可能会导致未定义的行为。

已停用的虚拟处理器根可能会唤醒调用 `Activate` 方法，并具有传入 `Deactivate` 方法的相同参数。 计划程序负责确保对 `Activate` 和 `Deactivate` 方法的调用配对，但不要求按特定顺序接收它们。 资源管理器可以在接收对 `Activate` 方法的调用 `Deactivate` 之前处理对该方法的调用。

如果虚拟处理器根 awakens 和 `Deactivate` 方法的返回值为**false**，则计划程序应通过 `IUMSCompletionList::GetUnblockNotifications` 方法查询 UMS 完成列表，对该信息执行操作，然后再次调用 `Deactivate` 方法。 应重复此方法，直至 `Deactivate` 方法返回 `true`的值。

如果参数 `pContext` 的值为 NULL，则会引发 `invalid_argument`。

如果从未激活虚拟处理器根，或者参数 `pContext` 不表示此虚拟处理器根最近调度的执行上下文，则会引发 `invalid_operation`。

停用虚拟处理器根的操作会将基础硬件线程的订阅级别减少1。 有关订阅级别的详细信息，请参阅[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot：： EnsureAllTasksVisible 方法

导致存储在单个处理器的内存层次结构中的数据对系统上的所有处理器都可见。 它可确保在该方法返回之前已在所有处理器上执行了完整内存隔离。

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
此虚拟处理器根当前正在调度的上下文。

### <a name="remarks"></a>备注

如果要将虚拟处理器根的停用添加到计划程序中，你可能会发现此方法非常有用。 出于性能原因，你可能会决定向计划程序添加工作项而不执行内存屏障，这意味着在一个处理器上执行的线程添加的工作项不会立即对所有其他处理器可见。 通过将此方法与 `Deactivate` 方法结合使用，可以确保计划程序在工作项存在于计划程序集合中时不会停用其所有虚拟处理器根。

对 `EnsureAllTasksVisibleThe` 方法的调用必须源自上次激活虚拟处理器根的执行上下文的 `Dispatch` 方法。 换句话说，调用 `EnsureAllTasksVisible` 方法的线程代理必须是当前在虚拟处理器根上执行的方法。 在不执行的虚拟处理器根上调用方法可能会导致未定义的行为。

如果参数 `pContext` 具有值 `NULL`，则会引发 `invalid_argument`。

如果从未激活虚拟处理器根，或者参数 `pContext` 不表示此虚拟处理器根最近调度的执行上下文，则会引发 `invalid_operation`。

## <a name="getid"></a>IVirtualProcessorRoot：： GetId 方法

返回虚拟处理器根的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

整数标识符。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
