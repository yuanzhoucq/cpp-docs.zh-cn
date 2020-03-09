---
title: IThreadProxy 结构
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854122"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy 结构

执行线程的抽象。 根据你创建的计划程序的 `SchedulerType` 策略键，资源管理器将授予你由普通的 Win32 线程或用户模式计划 (UMS) 线程支持的线程代理。 UMS 线程在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。

## <a name="syntax"></a>语法

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IThreadProxy：： GetId](#getid)|返回线程代理的唯一标识符。|
|[IThreadProxy：： SwitchOut](#switchout)|解除上下文与基础虚拟处理器根的关联。|
|[IThreadProxy：： SwitchTo](#switchto)|从当前执行的上下文切换到另一个上下文切换。|
|[IThreadProxy：： YieldToSystem](#yieldtosystem)|导致调用线程执行准备好在当前处理器上运行的另一个线程。 操作系统将选择要执行的下一个线程。|

## <a name="remarks"></a>备注

线程代理与接口 `IExecutionContext` 表示的执行上下文耦合，作为一种调度工作方式。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IThreadProxy`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="getid"></a>IThreadProxy：： GetId 方法

返回线程代理的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

唯一整数标识符。

## <a name="switchout"></a>IThreadProxy：： SwitchOut 方法

解除上下文与基础虚拟处理器根的关联。

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>参数

*switchState*<br/>
指示正在执行切换的线程代理的状态。 参数的类型为 `SwitchingProxyState`。

### <a name="remarks"></a>备注

如果由于某种原因需要解除上下文与执行它的虚拟处理器根的关联，请使用 `SwitchOut`。 根据传入参数 `switchState`的值，以及它是否在虚拟处理器根上执行，此调用将立即返回或阻塞与上下文关联的线程代理。 调用将参数设置为 `SwitchOut` 的 `Idle` 是错误的。 这样做会导致[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

当您因资源管理器指示或是请求了临时过度订阅的虚拟处理器根，而要减少计划程序所拥有的虚拟处理器根的数量，并且已完成时，`SwitchOut` 很有用。 在这种情况下，应在调用 `SwitchOut` 并将参数 `switchState` 设置为 `Blocking`之前，对虚拟处理器根调用方法[IVirtualProcessorRoot：： Remove](iexecutionresource-structure.md#remove) 。 这将阻塞线程代理，并且当计划程序中不同的虚拟处理器根可用来执行它时，线程代理将继续执行。 可以通过调用函数 `SwitchTo` 来恢复阻塞线程代理，以切换到此线程代理的执行上下文。 还可以通过使用其关联上下文激活虚拟处理器根来恢复线程代理。 有关如何执行此操作的详细信息，请参阅[IVirtualProcessorRoot：： Activate](ivirtualprocessorroot-structure.md#activate)。

如果您希望重新初始化虚拟处理器，也可以使用 `SwitchOut`，这样在将来阻塞线程代理或从运行它的虚拟处理器根和它进行调度工作的计划程序暂时分离该线程代理时，可以将虚拟处理器激活。 如果您希望阻塞线程代理，请使用 `SwitchOut` 并将参数 `switchState` 设置为 `Blocking`。 如上所示，稍后可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 将其恢复。 当您想要将该线程代理从运行它的虚拟处理器根和与虚拟处理器关联的计划程序暂时分离时，请使用 `SwitchOut` 并将参数设置为 `Nesting`。 当线程代理在虚拟处理器根上执行时，调用 `SwitchOut` 并将参数 `switchState` 设置为 `Nesting` 将导致根重新初始化，而当前线程代理无需虚拟处理器根也会继续执行。 线程代理被视为已离开计划程序，直到它在以后的某个时间点调用[IThreadProxy：： SwitchOut](#switchout) `Blocking` 方法。 对将参数设置为 `SwitchOut` 的 `Blocking` 的第二次调用旨在使上下文返回已阻止状态，以便通过 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 在之前与其分离的计划程序中恢复它。 由于它不是在虚拟处理器根上执行的，因此不会发生重新初始化。

重新初始化后的虚拟处理器根与资源管理器授予您的计划程序的全新虚拟处理器根没有任何不同。 您可以使用 `IVirtualProcessorRoot::Activate`，通过一个执行上下文来激活它，将其用于执行。

必须对表示当前正在执行的线程的 `IThreadProxy` 接口调用 `SwitchOut`，否则结果是不确定的。

在随 Visual Studio 2010 一同提供的库和标头中，此方法未采用参数，而且没有重新初始化虚拟处理器根。 为了保留旧行为，提供 `Blocking` 的默认参数值。

## <a name="switchto"></a>IThreadProxy：： SwitchTo 方法

从当前执行的上下文切换到另一个上下文切换。

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
要以协作方式切换到的执行上下文。

*switchState*<br/>
指示正在执行切换的线程代理的状态。 参数的类型为 `SwitchingProxyState`。

### <a name="remarks"></a>备注

使用此方法，从第一个执行上下文的[IExecutionContext：:D ispatch](iexecutioncontext-structure.md#dispatch)方法，从一个执行上下文切换到另一个执行上下文。 方法将执行上下文 `pContext` 与线程代理关联（如果尚未关联）。 当前线程代理的所有权由您为 `switchState` 参数指定的值确定。

如果要将当前正在执行的线程代理返回到资源管理器，请使用值 `Idle`。 如果将参数 `switchState` 设置为 `Idle`，则调用 `SwitchTo` 将导致执行上下文 `pContext` 开始在基础执行资源上执行。 此线程代理的所有权会传输到资源管理器，因此，在 `SwitchTo` 返回后，你预计会立即从执行上下文的 `Dispatch` 方法返回，以完成传输。 线程代理正在分派的执行上下文与线程代理解除关联，计划程序可随意重复使用它，或在认为合适的情况下销毁。

如果希望此线程代理进入 "已阻止" 状态，请使用值 `Blocking`。 将 `switchState` 设置为 `Blocking` 的参数调用 `SwitchTo` 将导致执行 `pContext` 上下文开始执行，并阻止当前线程代理直到它恢复。 当线程代理处于 `Blocking` 状态时，计划程序将保留线程代理的所有权。 可以通过调用函数 `SwitchTo` 来恢复阻塞线程代理，以切换到此线程代理的执行上下文。 还可以通过使用其关联上下文激活虚拟处理器根来恢复线程代理。 有关如何执行此操作的详细信息，请参阅[IVirtualProcessorRoot：： Activate](ivirtualprocessorroot-structure.md#activate)。

如果要从运行该线程代理的虚拟处理器根上暂时将此线程代理与正在其上运行的计划程序进行分离，请使用值 `Nesting`。 使用参数 `switchState` 设置为 `Nesting` 调用 `SwitchTo` 将导致执行 `pContext` 上下文开始执行，而当前线程代理也会继续执行，而不需要虚拟处理器根。 线程代理被视为已离开计划程序，直到它在稍后的某个时间点调用[IThreadProxy：： SwitchOut](#switchout)方法。 `IThreadProxy::SwitchOut` 方法可能会阻塞线程代理，直到虚拟处理器根可用于重新计划。

必须对表示当前正在执行的线程的 `IThreadProxy` 接口调用 `SwitchTo`，否则结果是不确定的。 如果参数 `pContext` 设置为 `NULL`，则函数将引发 `invalid_argument`。

## <a name="yieldtosystem"></a>IThreadProxy：： YieldToSystem 方法

导致调用线程执行准备好在当前处理器上运行的另一个线程。 操作系统将选择要执行的下一个线程。

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>备注

由常规 Windows 线程支持的线程代理调用时，`YieldToSystem` 的行为与 Windows 函数 `SwitchToThread`完全相同。 但是，当从用户模式计划（UMS）线程调用时，`SwitchToThread` 函数将选取要运行的下一个线程的任务委托给用户模式计划程序，而不是操作系统。 若要实现切换到系统中的其他可用线程所需的效果，请使用 `YieldToSystem`。

必须对表示当前正在执行的线程的 `IThreadProxy` 接口调用 `YieldToSystem`，否则结果是不确定的。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[IExecutionContext 结构](iexecutioncontext-structure.md)<br/>
[IScheduler 结构](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)
