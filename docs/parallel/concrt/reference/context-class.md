---
title: Context 类
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865480"
---
# <a name="context-class"></a>Context 类

表示执行上下文的抽象。

## <a name="syntax"></a>语法

```cpp
class Context;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>受保护构造函数

|名称|说明|
|----------|-----------------|
|[~ 上下文析构函数](#dtor)||

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[块](#block)|阻止当前上下文。|
|[CurrentContext](#currentcontext)|返回指向当前上下文的指针。|
|[GetId](#getid)|返回上下文所属计划程序中唯一的上下文标识符。|
|[GetScheduleGroupId](#getschedulegroupid)|返回上下文当前正在处理的计划组的标识符。|
|[GetVirtualProcessorId](#getvirtualprocessorid)|返回上下文当前正在其上执行的虚拟处理器的标识符。|
|[Id](#id)|返回当前上下文的唯一标识符，该标识符在当前上下文所属的计划程序中是唯一的。|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|返回一个指示当前上下文中当前正在执行内联的任务集合是否正在活动取消的中间（或将很快发生）。|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|确定是否同步阻塞上下文。 如果上下文显式执行了导致阻止的操作，则会将其视为同步阻止。|
|[过度](#oversubscribe)|当对在该计划程序的某个虚拟处理器上执行的上下文调用时，在代码块的持续时间内将额外的虚拟处理器注入到计划程序中。|
|[ScheduleGroupId](#schedulegroupid)|返回当前上下文正在处理的计划组的标识符。|
|[阻挡](#unblock)|取消阻止上下文并使其变为可运行。|
|[VirtualProcessorId](#virtualprocessorid)|返回当前上下文正在其上执行的虚拟处理器的标识符。|
|[Yield](#yield)|让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。|

## <a name="remarks"></a>备注

并发运行时计划程序（请参阅[计划](scheduler-class.md)程序）使用执行上下文来执行应用程序对其进行排队的工作。 Win32 线程是 Windows 操作系统上的执行上下文的示例。

在任何时候，计划程序的并发级别都等于资源管理器向其授予的虚拟处理器的数目。 虚拟处理器是处理资源的抽象，并映射到基础系统上的硬件线程。 在给定的时间，只有单个计划程序上下文可在虚拟处理器上执行。

计划程序在本质上是协作的，如果正在执行的上下文希望进入等待状态，则可以随时将其虚拟处理器生成到不同的上下文中。 如果其等待时间满足，则无法继续，直到计划程序的可用虚拟处理器开始执行它。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Context`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="block"></a>模块

阻止当前上下文。

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

如果调用上下文正在虚拟处理器上运行，则虚拟处理器将查找要执行的另一个可运行上下文，或者可能会创建新上下文。

调用或调用 `Block` 方法后，必须将其与另一个执行上下文中的[解除阻止](#unblock)方法的调用配对，以便它再次运行。 请注意，在代码为另一个线程发布其上下文以便能够调用 `Unblock` 方法的点与对 `Block` 进行实际方法调用的点之间存在关键时间间隔。 在此时间段内，您不能调用任何可能会反过来阻止或取消阻止其自身原因（例如获取一个锁）的方法。 对 `Block` 和 `Unblock` 方法的调用不会跟踪阻止和取消阻止的原因。 只有一个对象应该拥有 `Block`- `Unblock` 对的所有权。

此方法可能会引发各种异常，包括[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)。

## <a name="dtor"></a>~ 上下文

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

返回指向当前上下文的指针。

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>返回值

指向当前上下文的指针。

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

## <a name="getid"></a>GetId

返回上下文所属计划程序中唯一的上下文标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

上下文的标识符，该标识符在上下文所属的计划程序中是唯一的。

## <a name="getschedulegroupid"></a>GetScheduleGroupId

返回上下文当前正在处理的计划组的标识符。

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>返回值

上下文当前正在处理的计划组的标识符。

### <a name="remarks"></a>备注

此方法的返回值是上下文正在其上执行的计划组的即时采样。 如果是在除当前上下文外的其他上下文中调用此方法，则该值可能在返回时过时，不可依靠。 通常，此方法仅用于调试或跟踪目的。

## <a name="getvirtualprocessorid"></a>GetVirtualProcessorId

返回上下文当前正在其上执行的虚拟处理器的标识符。

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>返回值

如果上下文当前正在虚拟处理器上执行，则为当前正在其上执行上下文的虚拟处理器的标识符;否则，值 `-1`。

### <a name="remarks"></a>备注

此方法的返回值是上下文正在其上执行的虚拟处理器的即时采样。 此值可能在返回时过时并且不可依靠。 通常，此方法仅用于调试或跟踪目的。

## <a name="id"></a>识别

返回当前上下文的唯一标识符，该标识符在当前上下文所属的计划程序中是唯一的。

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>返回值

如果当前上下文附加到计划程序，则当前上下文在当前上下文所属的计划程序中是唯一的，它是当前上下文的标识符;否则，值 `-1`。

## <a name="iscurrenttaskcollectioncanceling"></a>IsCurrentTaskCollectionCanceling

返回一个指示当前上下文中当前正在执行内联的任务集合是否正在活动取消的中间（或将很快发生）。

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>返回值

如果将计划程序附加到调用上下文，并且任务组在该上下文上执行内联任务，则指示该任务组是否正在活动取消（或将很快）;否则，值 `false`。

## <a name="issynchronouslyblocked"></a>IsSynchronouslyBlocked

确定是否同步阻塞上下文。 如果上下文显式执行了导致阻止的操作，则会将其视为同步阻止。

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>返回值

上下文是否已同步阻止。

### <a name="remarks"></a>备注

如果上下文显式执行了导致阻止的操作，则会将其视为同步阻止。 在线程计划程序上，这将指示对 `Context::Block` 方法或通过 `Context::Block` 方法构建的同步对象的直接调用。

此方法的返回值是是否同步阻塞上下文的即时示例。 此值可能在返回时过时，并且只能在非常特定的情况下使用。

## <a name="operator_delete"></a>运算符删除

`Context` 对象由运行时内部销毁。 无法显式删除它。

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>参数

*_PObject*<br/>
指向要删除的对象的指针。

## <a name="oversubscribe"></a>过度

当对在该计划程序的某个虚拟处理器上执行的上下文调用时，在代码块的持续时间内将额外的虚拟处理器注入到计划程序中。

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>参数

*_BeginOversubscription*<br/>
如果**为 true**，则指示应在超额订阅的持续时间内添加额外的虚拟处理器。 如果**为 false**，则表示超额订阅应结束，并且应删除以前添加的虚拟处理器。

## <a name="schedulegroupid"></a>ScheduleGroupId

返回当前上下文正在处理的计划组的标识符。

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>返回值

如果当前上下文附加到计划程序并处理计划组，则为当前上下文正在处理的计划程序组的标识符;否则，值 `-1`。

## <a name="unblock"></a>阻挡

取消阻止上下文并使其变为可运行。

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>备注

在对[Block](#block)方法的相应调用之前调用 `Unblock` 方法是完全合法的。 只要对 `Block` 和 `Unblock` 方法的调用正确配对，运行时就会正确地处理任意排序的自然争用。 `Block` 调用之前的 `Unblock` 调用只会否定 `Block` 调用的效果。

此方法可能会引发多个异常。 如果某个上下文尝试自行调用 `Unblock` 方法，则将引发[context_self_unblock](context-self-unblock-class.md)异常。 如果对 `Block` 和 `Unblock` 的调用未正确配对（例如，对当前正在运行的上下文进行了两次 `Unblock` 调用），则将引发[context_unblock_unbalanced](context-unblock-unbalanced-class.md)异常。

请注意，在代码为另一个线程发布其上下文以便能够调用 `Unblock` 方法的点与对 `Block` 进行实际方法调用的点之间存在关键时间间隔。 在此时间段内，您不能调用任何可能会反过来阻止或取消阻止其自身原因（例如获取一个锁）的方法。 对 `Block` 和 `Unblock` 方法的调用不会跟踪阻止和取消阻止的原因。 只有一个对象应具有 `Block` 和 `Unblock` 对的所有权。

## <a name="virtualprocessorid"></a>VirtualProcessorId

返回当前上下文正在其上执行的虚拟处理器的标识符。

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>返回值

如果当前上下文附加到计划程序，则为当前上下文正在其上执行的虚拟处理器的标识符;否则，值 `-1`。

### <a name="remarks"></a>备注

此方法的返回值是在其上执行当前上下文的虚拟处理器的即时采样。 此值可能在返回时过时并且不可依靠。 通常，此方法仅用于调试或跟踪目的。

## <a name="yield"></a>产生

让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

## <a name="yieldexecution"></a>YieldExecution

让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

此函数是 Visual Studio 2015 中的新增功能，与[yield](#yield)函数相同，但不与 Windows 中的 yield 宏冲突。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[Scheduler 类](scheduler-class.md)<br/>
[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
