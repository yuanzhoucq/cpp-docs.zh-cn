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
ms.openlocfilehash: fc2fb2df06225a5c963fe39178c1b4a10f77953d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368131"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy 结构

执行线程的抽象。 根据你创建的计划程序的 `SchedulerType` 策略键，资源管理器将授予你由普通的 Win32 线程或用户模式计划 (UMS) 线程支持的线程代理。 UMS 线程在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。

## <a name="syntax"></a>语法

```cpp
struct IThreadProxy;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IThread 代理：：GetId](#getid)|返回线程代理的唯一标识符。|
|[IThreadProxy：：切换出](#switchout)|解除上下文与基础虚拟处理器根的关联。|
|[IThreadProxy：：切换到](#switchto)|执行协作上下文从当前执行的上下文切换到其他上下文。|
|[IThreadProxy：：屈服到系统](#yieldtosystem)|导致调用线程执行准备好在当前处理器上运行的另一个线程。 操作系统选择要执行的下一个线程。|

## <a name="remarks"></a>备注

线程代理与接口`IExecutionContext`表示的执行上下文耦合，作为调度工作的一种手段。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IThreadProxy`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="ithreadproxygetid-method"></a><a name="getid"></a>IThreadProxy：GetId 方法

返回线程代理的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

唯一的整数标识符。

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a>IThreadProxy：：切换方法

解除上下文与基础虚拟处理器根的关联。

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>参数

*开关状态*<br/>
指示执行交换机的线程代理的状态。 参数的类型`SwitchingProxyState`为 。

### <a name="remarks"></a>备注

如果由于某种原因需要解除上下文与执行它的虚拟处理器根的关联，请使用 `SwitchOut`。 根据传入参数 `switchState`的值，以及它是否在虚拟处理器根上执行，此调用将立即返回或阻塞与上下文关联的线程代理。 调用将参数设置为 `SwitchOut` 的 `Idle` 是错误的。 这样做将导致[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。

当您因资源管理器指示或是请求了临时过度订阅的虚拟处理器根，而要减少计划程序所拥有的虚拟处理器根的数量，并且已完成时，`SwitchOut` 很有用。 在这种情况下，您应该调用方法[IVirtualProcessorRoot：：删除](iexecutionresource-structure.md#remove)虚拟处理器根，然后再调用`SwitchOut`参数`switchState`设置为`Blocking`。 这将阻塞线程代理，并且当计划程序中不同的虚拟处理器根可用来执行它时，线程代理将继续执行。 可以通过调用函数`SwitchTo`切换到此线程代理的执行上下文来恢复阻塞线程代理。 您还可以使用其关联的上下文来激活虚拟处理器根，从而恢复线程代理。 有关如何执行此操作的详细信息，请参阅[IVirtualProcessorRoot：：：激活](ivirtualprocessorroot-structure.md#activate)。

如果您希望重新初始化虚拟处理器，也可以使用 `SwitchOut`，这样在将来阻塞线程代理或从运行它的虚拟处理器根和它进行调度工作的计划程序暂时分离该线程代理时，可以将虚拟处理器激活。 如果您希望阻塞线程代理，请使用 `SwitchOut` 并将参数 `switchState` 设置为 `Blocking`。 如上所示，稍后可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 将其恢复。 当您想要将该线程代理从运行它的虚拟处理器根和与虚拟处理器关联的计划程序暂时分离时，请使用 `SwitchOut` 并将参数设置为 `Nesting`。 当线程代理在虚拟处理器根上执行时，调用 `SwitchOut` 并将参数 `switchState` 设置为 `Nesting` 将导致根重新初始化，而当前线程代理无需虚拟处理器根也会继续执行。 线程代理被视为已离开计划程序，直到它调用[IThreadProxy：：switchOut](#switchout)方法，稍后`Blocking`时间点使用。 对将参数设置为 `SwitchOut` 的 `Blocking` 的第二次调用旨在使上下文返回已阻止状态，以便通过 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 在之前与其分离的计划程序中恢复它。 由于它不是在虚拟处理器根上执行的，因此不会发生重新初始化。

重新初始化后的虚拟处理器根与资源管理器授予您的计划程序的全新虚拟处理器根没有任何不同。 您可以使用 `IVirtualProcessorRoot::Activate`，通过一个执行上下文来激活它，将其用于执行。

`SwitchOut`必须在表示当前正在执行`IThreadProxy`的线程的接口上调用，否则结果未定义。

在随 Visual Studio 2010 一同提供的库和标头中，此方法未采用参数，而且没有重新初始化虚拟处理器根。 为了保留旧行为，提供 `Blocking` 的默认参数值。

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a>IThreadProxy：：切换到方法

执行协作上下文从当前执行的上下文切换到其他上下文。

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>参数

*pContext*<br/>
要协同切换到的执行上下文。

*开关状态*<br/>
指示执行交换机的线程代理的状态。 参数的类型`SwitchingProxyState`为 。

### <a name="remarks"></a>备注

使用此方法从第一个执行上下文的[iExecutionContext：:Dispatch](iexecutioncontext-structure.md#dispatch)方法从一个执行上下文切换到另一个执行上下文。 如果执行上下文尚未与线程`pContext`代理关联，则该方法将执行上下文与线程代理关联。 当前线程代理的所有权由您为`switchState`参数指定的值确定。

如果要将当前`Idle`正在执行的线程代理返回到资源管理器，请使用 该值。 使用`SwitchTo``switchState`参数设置为调用`Idle`将导致执行上下文`pContext`开始在基础执行资源上执行。 此线程代理的所有权将转移到资源管理器，并且您希望在返回后立即`Dispatch``SwitchTo`从执行上下文的方法返回，以便完成传输。 线程代理调度的执行上下文与线程代理分离，调度程序可以自由地重用它或销毁它，因为它认为合适。

当希望此`Blocking`线程代理进入阻止状态时，请使用 该值。 使用`SwitchTo`参数`switchState`设置为调用`Blocking`将导致执行上下文`pContext`开始执行，并阻止当前线程代理，直到恢复它。 当线程代理处于`Blocking`状态时，计划程序保留线程代理的所有权。 可以通过调用函数`SwitchTo`切换到此线程代理的执行上下文来恢复阻塞线程代理。 您还可以使用其关联的上下文来激活虚拟处理器根，从而恢复线程代理。 有关如何执行此操作的详细信息，请参阅[IVirtualProcessorRoot：：：激活](ivirtualprocessorroot-structure.md#activate)。

如果要暂时将`Nesting`此线程代理从正在运行的虚拟处理器根和为其调度工作的调度程序分离时，请使用 该值。 使用`SwitchTo`参数`switchState`设置为调用`Nesting`将导致执行上下文`pContext`开始执行，并且当前线程代理也继续执行，而无需虚拟处理器根。 线程代理被视为已离开计划程序，直到它在以后的时间点调用[IThreadProxy：：SwitchOut](#switchout)方法。 该方法`IThreadProxy::SwitchOut`可以阻止线程代理，直到虚拟处理器根可用于重新计划它。

`SwitchTo`必须在表示当前正在执行`IThreadProxy`的线程的接口上调用，否则结果未定义。 如果参数`invalid_argument``pContext`设置为`NULL`，则将引发该函数。

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a>IThreadProxy：屈服到系统方法

导致调用线程执行准备好在当前处理器上运行的另一个线程。 操作系统选择要执行的下一个线程。

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>备注

当由常规 Windows 线程支持的线程代理调用时，`YieldToSystem`其运行方式与 Windows 函数`SwitchToThread`完全一样。 但是，当从用户模式可分排 （UMS） 线程调用时`SwitchToThread`，该函数将选取要运行的下一个线程的任务委派给用户模式计划程序，而不是操作系统。 要达到在系统中切换到其他就绪线程的预期效果，请使用`YieldToSystem`。

`YieldToSystem`必须在表示当前正在执行`IThreadProxy`的线程的接口上调用，否则结果未定义。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[IExecutionContext 结构](iexecutioncontext-structure.md)<br/>
[IScheduler 结构](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)
