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
ms.openlocfilehash: 869d51144b686dd684f62b337bb90eff8a9a5589
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193947"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 结构

线程代理可在其中执行的硬件线程的抽象。

## <a name="syntax"></a>语法

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[IVirtualProcessorRoot：： Activate](#activate)|导致与执行上下文接口相关联的线程代理 `pContext` 开始在此虚拟处理器根上执行。|
|[IVirtualProcessorRoot：:D eactivate](#deactivate)|导致线程代理当前正在此虚拟处理器根上执行以停止调度执行上下文。 线程代理将在调用方法时恢复执行 `Activate` 。|
|[IVirtualProcessorRoot：： EnsureAllTasksVisible](#ensurealltasksvisible)|导致存储在单个处理器的内存层次结构中的数据对系统上的所有处理器都可见。 它可确保在该方法返回之前已在所有处理器上执行了完整内存隔离。|
|[IVirtualProcessorRoot：： GetId](#getid)|返回虚拟处理器根的唯一标识符。|

## <a name="remarks"></a>备注

每个虚拟处理器根都具有关联的执行资源。 此 `IVirtualProcessorRoot` 接口继承自[IExecutionResource](iexecutionresource-structure.md)接口。 多个虚拟处理器根可能对应于同一个基础硬件线程。

资源管理器将虚拟处理器根向计划程序授予对资源的请求的响应。 计划程序可以通过使用执行上下文激活虚拟处理器根来执行工作。

## <a name="inheritance-hierarchy"></a>继承层次结构

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>IVirtualProcessorRoot：： Activate 方法

导致与执行上下文接口相关联的线程代理 `pContext` 开始在此虚拟处理器根上执行。

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
将在此虚拟处理器根上调度的执行上下文的接口。

### <a name="remarks"></a>备注

如果某个线程代理与执行上下文接口无关，则资源管理器将提供该代理`pContext`

`Activate`方法可用于开始在资源管理器返回的新虚拟处理器根上执行工作，或在停用或即将停用的虚拟处理器根上恢复线程代理。 有关停用的详细信息，请参阅[IVirtualProcessorRoot：:D eactivate](#deactivate) 。 恢复停用的虚拟处理器根时，该参数 `pContext` 必须与用于停用虚拟处理器根的参数相同。

第一次激活虚拟处理器根后，对和的后续调用对 `Deactivate` `Activate` 可能会相互争用。 这意味着，资源管理器可以在收到调用之前接收对的调用 `Activate` `Deactivate` 。

激活虚拟处理器根时，会向资源管理器发出信号，指示此虚拟处理器根当前正在忙于工作。 如果计划程序找不到任何要在此根上执行的工作，则应调用 `Deactivate` 方法，通知资源管理器虚拟处理器根处于空闲状态。 资源管理器使用此数据对系统进行负载平衡。

`invalid_argument`如果参数具有值，则引发 `pContext` `NULL` 。

`invalid_operation`如果参数 `pContext` 不表示此虚拟处理器根最近调度的执行上下文，则会引发。

激活虚拟处理器根的操作会将基础硬件线程的订阅级别增加1。 有关订阅级别的详细信息，请参阅[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>IVirtualProcessorRoot：:D eactivate 方法

导致线程代理当前正在此虚拟处理器根上执行以停止调度执行上下文。 线程代理将在调用方法时恢复执行 `Activate` 。

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
此根当前正在调度的上下文。

### <a name="return-value"></a>返回值

布尔值。 值为 **`true`** 指示线程代理从方法返回， `Deactivate` 以响应对方法的调用 `Activate` 。 值为 **`false`** 指示从方法返回的线程代理，以响应资源管理器中的通知事件。 在用户模式计划（UMS）线程计划程序中，这指示项已显示在计划程序的完成列表中，并且需要计划程序来处理这些项。

### <a name="remarks"></a>备注

如果在计划程序中找不到任何工作，请使用此方法来暂时停止执行虚拟处理器根。 对方法的调用 `Deactivate` 必须源自 `Dispatch` 上次激活虚拟处理器根的执行上下文的方法中。 换句话说，调用方法的线程代理 `Deactivate` 必须是当前在虚拟处理器根上执行的线程代理。 在不执行的虚拟处理器根上调用方法可能会导致未定义的行为。

已停用的虚拟处理器根可能会唤醒调用 `Activate` 方法，并且具有传入方法的相同参数 `Deactivate` 。 计划程序负责确保对 `Activate` 和方法的调用 `Deactivate` 配对，但不要求按特定顺序接收这些方法。 资源管理器可以在接收对方法的调用之前处理对该方法的调用 `Activate` `Deactivate` 。

如果虚拟处理器根 awakens 和方法的返回值 `Deactivate` 是值 **`false`** ，则计划程序应通过方法查询 UMS 完成列表 `IUMSCompletionList::GetUnblockNotifications` ，对该信息执行操作，然后 `Deactivate` 再次调用方法。 应重复此方法，直到 `Deactivate` 方法返回值 **`true`** 。

`invalid_argument`如果参数的值为 NULL，则会引发 `pContext` 。

`invalid_operation`如果从未激活虚拟处理器根，或者该参数 `pContext` 不表示此虚拟处理器根最近调度的执行上下文，则会引发。

停用虚拟处理器根的操作会将基础硬件线程的订阅级别减少1。 有关订阅级别的详细信息，请参阅[IExecutionResource：： CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>IVirtualProcessorRoot：： EnsureAllTasksVisible 方法

导致存储在单个处理器的内存层次结构中的数据对系统上的所有处理器都可见。 它可确保在该方法返回之前已在所有处理器上执行了完整内存隔离。

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
此虚拟处理器根当前正在调度的上下文。

### <a name="remarks"></a>备注

如果要将虚拟处理器根的停用添加到计划程序中，你可能会发现此方法非常有用。 出于性能原因，你可能会决定向计划程序添加工作项而不执行内存屏障，这意味着在一个处理器上执行的线程添加的工作项不会立即对所有其他处理器可见。 通过将此方法与方法结合使用 `Deactivate` ，可以确保计划程序在工作项存在于计划程序集合中时不会停用其所有虚拟处理器根。

对方法的调用 `EnsureAllTasksVisibleThe` 必须源自 `Dispatch` 上次激活虚拟处理器根的执行上下文的方法中。 换句话说，调用方法的线程代理 `EnsureAllTasksVisible` 必须是当前在虚拟处理器根上执行的线程代理。 在不执行的虚拟处理器根上调用方法可能会导致未定义的行为。

`invalid_argument`如果参数具有值，则引发 `pContext` `NULL` 。

`invalid_operation`如果从未激活虚拟处理器根，或者该参数 `pContext` 不表示此虚拟处理器根最近调度的执行上下文，则会引发。

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>IVirtualProcessorRoot：： GetId 方法

返回虚拟处理器根的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

整数标识符。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
