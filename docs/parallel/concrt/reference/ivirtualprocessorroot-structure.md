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
ms.openlocfilehash: f642a29d0a80568f7a5f2a5e89f6951d4819243e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364259"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 结构

线程代理可在其中执行的硬件线程的抽象。

## <a name="syntax"></a>语法

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I虚拟处理器根：激活](#activate)|使与执行上下文接口`pContext`关联的线程代理开始在此虚拟处理器根上执行。|
|[I虚拟处理器根：:D激活](#deactivate)|导致当前在此虚拟处理器根上执行的线程代理停止调度执行上下文。 线程代理将在调用`Activate`方法时继续执行。|
|[I虚拟处理器根：：确保所有任务可见](#ensurealltasksvisible)|使存储在各个处理器的内存层次结构中的数据对系统上的所有处理器都可见。 它可确保在方法返回之前在所有处理器上执行完整的内存围栏。|
|[I虚拟处理器根：GetId](#getid)|返回虚拟处理器根的唯一标识符。|

## <a name="remarks"></a>备注

每个虚拟处理器根都有关联的执行资源。 接口`IVirtualProcessorRoot`从[I 执行资源](iexecutionresource-structure.md)接口继承。 多个虚拟处理器根可能对应于同一基础硬件线程。

资源管理器将虚拟处理器根授予计划程序以响应资源请求。 计划程序可以使用虚拟处理器根通过使用执行上下文激活它来执行工作。

## <a name="inheritance-hierarchy"></a>继承层次结构

[I 执行资源](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>I虚拟处理器根：激活方法

使与执行上下文接口`pContext`关联的线程代理开始在此虚拟处理器根上执行。

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
将在此虚拟处理器根上调度的执行上下文的接口。

### <a name="remarks"></a>备注

如果线程代理未与执行上下文接口关联，资源管理器将提供线程代理`pContext`

该方法`Activate`可用于开始执行资源管理器返回的新虚拟处理器根的工作，或恢复已停用或即将停用的虚拟处理器根上的线程代理。 有关停用的详细信息，请参阅[IVirtualProcessorRoot：:D激活](#deactivate)。 恢复停用的虚拟处理器根时，参数`pContext`必须与用于停用虚拟处理器根的参数相同。

首次激活虚拟处理器根后，后续对调用`Deactivate`可能会`Activate`相互竞争。 这意味着资源管理器在收到其应为的`Activate``Deactivate`呼叫之前可以收到呼叫。

激活虚拟处理器根时，会向资源管理器发出信号，表明此虚拟处理器根当前正忙于工作。 如果计划程序找不到在此根上执行的任何工作，则应调用方法，`Deactivate`通知资源管理器虚拟处理器根处于空闲状态。 资源管理器使用此数据来负载平衡系统。

`invalid_argument`如果参数`pContext`具有 值`NULL`，则引发 。

`invalid_operation`如果参数`pContext`不表示此虚拟处理器根最近调度的执行上下文，则引发该参数。

激活虚拟处理器根的行为将基础硬件线程的订阅级别增加一个。 有关订阅级别的详细信息，请参阅[I 执行资源：：当前订阅级别](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>I虚拟处理器Root：:D激活方法

导致当前在此虚拟处理器根上执行的线程代理停止调度执行上下文。 线程代理将在调用`Activate`方法时继续执行。

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
当前由此根调度的上下文。

### <a name="return-value"></a>返回值

布尔值。 **值 true**表示线程代理从`Deactivate`方法返回以响应对方法的`Activate`调用。 的值`false`指示线程代理从 方法返回以响应资源管理器中的通知事件。 在用户模式可分排 （UMS） 线程计划程序上，这表示项目已出现在计划程序的完成列表中，并且计划程序需要处理它们。

### <a name="remarks"></a>备注

当在计划程序中找不到任何工作时，使用此方法可以暂时停止执行虚拟处理器根。 对方法的`Deactivate`调用必须源自上次激活虚拟处理器`Dispatch`根的执行上下文的方法。 换句话说，调用该方法的`Deactivate`线程代理必须是当前在虚拟处理器根上执行的代理。 在未执行的虚拟处理器根上调用方法可能会导致未定义的行为。

停用的虚拟处理器根可能通过调用方法唤醒，`Activate`其参数与传递给`Deactivate`该方法的参数相同。 计划程序负责确保对 和`Activate`方法`Deactivate`的调用是配对的，但不需要按特定顺序接收它们。 资源管理器可以在收到对`Activate`该方法的调用之前处理对该方法的调用。 `Deactivate`

如果虚拟处理器根唤醒`Deactivate`，并且方法的返回值为**false**值，则计划程序应通过`IUMSCompletionList::GetUnblockNotifications`该方法查询 UMS 完成列表，对该信息执行操作，然后再次调用`Deactivate`该方法。 应重复这一点，`Deactivate`直到方法返回值`true`为止。

`invalid_argument`如果参数的值为`pContext`NULL，则引发该参数。

`invalid_operation`如果虚拟处理器根从未激活，或者参数`pContext`不表示此虚拟处理器根最近调度的执行上下文，则引发该参数。

停用虚拟处理器根的行为将基础硬件线程的订阅级别降低一个。 有关订阅级别的详细信息，请参阅[I 执行资源：：当前订阅级别](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>I虚拟处理器根：：确保所有任务可见方法

使存储在各个处理器的内存层次结构中的数据对系统上的所有处理器都可见。 它可确保在方法返回之前在所有处理器上执行完整的内存围栏。

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
当前由此虚拟处理器根调度的上下文。

### <a name="remarks"></a>备注

当您要同步虚拟处理器根的停用以及向计划程序添加新工作时，您可能会发现此方法很有用。 出于性能原因，您可能决定在不执行内存障碍的情况下将工作项添加到计划程序，这意味着在一个处理器上执行的线程添加的工作项对所有其他处理器都无法立即看到。 通过将此方法与`Deactivate`方法结合使用，可以确保计划程序不会在计划程序集合中存在工作项时停用其所有虚拟处理器根。

对方法的`EnsureAllTasksVisibleThe`调用必须源自上次激活虚拟处理器`Dispatch`根的执行上下文的方法。 换句话说，调用该方法的`EnsureAllTasksVisible`线程代理必须是当前在虚拟处理器根上执行的代理。 在未执行的虚拟处理器根上调用方法可能会导致未定义的行为。

`invalid_argument`如果参数`pContext`具有 值`NULL`，则引发 。

`invalid_operation`如果虚拟处理器根从未激活，或者参数`pContext`不表示此虚拟处理器根最近调度的执行上下文，则引发该参数。

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>I虚拟处理器根：GetId 方法

返回虚拟处理器根的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

整数标识符。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)
