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
ms.openlocfilehash: c6b219eabd008114f40401c64465e44607c2ee9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555072"
---
# <a name="context-class"></a>Context 类

表示执行上下文的抽象。

## <a name="syntax"></a>语法

```
class Context;
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[~ Context 析构函数](#dtor)||

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[块](#block)|阻止当前上下文。|
|[CurrentContext](#currentcontext)|返回指向当前上下文的指针。|
|[GetId](#getid)|返回上下文所属的计划程序中是唯一的上下文的标识符。|
|[GetScheduleGroupId](#getschedulegroupid)|返回上下文目前正在从事的计划组的标识符。|
|[GetVirtualProcessorId](#getvirtualprocessorid)|返回当前正在执行上下文的虚拟处理器的标识符。|
|[Id](#id)|返回在当前上下文所属的计划程序中是唯一的当前上下文的标识符。|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|返回一个指示是否当前正在执行内联在当前上下文的任务集合正处于活动状态的取消操作 （或不久将）。|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|确定以同步方式阻止上下文。 若要以同步方式阻止它显式执行的操作导致阻塞，则认为该上下文。|
|[超额订阅](#oversubscribe)|注入一个计划程序的其他虚拟处理器的其中一个该计划程序中的虚拟处理器上执行的上下文调用时的代码块的持续时间。|
|[ScheduleGroupId](#schedulegroupid)|返回当前上下文正在处理的计划组的标识符。|
|[Unblock](#unblock)|取消阻止上下文，并使其成为可运行。|
|[VirtualProcessorId](#virtualprocessorid)|返回当前上下文在其执行的虚拟处理器的标识符。|
|[Yield](#yield)|让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。|

## <a name="remarks"></a>备注

并发运行时计划程序 (请参阅[计划程序](scheduler-class.md)) 使用执行上下文来执行工作排列到您的应用程序。 Win32 线程是在 Windows 操作系统上的执行上下文的示例。

在任何时候，计划程序的并发级别等于向它授予通过资源管理器的虚拟处理器的数量。 虚拟处理器是处理资源和映射到基础系统上的硬件线程的抽象。 在给定时间，只有单个计划程序上下文可以执行虚拟处理器上。

计划程序是协作性在本质上，执行上下文可以在任何时间产生其虚拟处理器到不同的上下文，如果它希望进入等待状态。 其等待它满足时，它不能继续直到在计划程序中的虚拟处理器可用开始执行它。

## <a name="inheritance-hierarchy"></a>继承层次结构

`Context`

## <a name="requirements"></a>要求

**标头：** concrt.h

**命名空间：** 并发

##  <a name="block"></a> 块

阻止当前上下文。

```
static void __cdecl Block();
```

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

如果虚拟处理器上运行时调用的上下文，虚拟处理器将查找另一个可运行的上下文执行，也有可能会创建一个新。

之后`Block`方法已调用，或将调用，必须将它与对的调用配对[解除阻止](#unblock)方法从另一个执行上下文才能使它再次运行。 请注意，你的代码发布为另一个线程可以调用其上下文的点之间没有重要的时间段`Unblock`方法和其中的实际方法调用的点`Block`进行。 在此时间段内，您不能调用任何可能会反过来阻止或取消阻止其自身原因（例如获取一个锁）的方法。 调用`Block`和`Unblock`方法不会跟踪阻止和取消阻止的原因。 只有一个对象应具有的所有权`Block` -  `Unblock`对。

此方法会引发异常，包括各种[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)。

##  <a name="dtor"></a> ~ 上下文

```
virtual ~Context();
```

##  <a name="currentcontext"></a> CurrentContext

返回指向当前上下文的指针。

```
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>返回值

指向当前上下文的指针。

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

##  <a name="getid"></a> GetId

返回上下文所属的计划程序中是唯一的上下文的标识符。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

上下文所属的计划程序中是唯一的上下文标识符。

##  <a name="getschedulegroupid"></a> GetScheduleGroupId

返回上下文目前正在从事的计划组的标识符。

```
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>返回值

目前正计划组上下文的标识符。

### <a name="remarks"></a>备注

此方法的返回值是在其执行上下文的计划组的瞬时采样。 如果是在除当前上下文外的其他上下文中调用此方法，则该值可能在返回时过时，不可依靠。 通常情况下，此方法用于调试或跟踪目的。

##  <a name="getvirtualprocessorid"></a> GetVirtualProcessorId

返回当前正在执行上下文的虚拟处理器的标识符。

```
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>返回值

如果上下文当前正在执行一个虚拟处理器上的虚拟处理器上; 当前执行上下文的标识符否则为值`-1`。

### <a name="remarks"></a>备注

此方法的返回值是在其执行上下文的虚拟处理器的瞬时采样。 此值可能在返回时过时并且不可依靠。 通常情况下，此方法用于调试或跟踪目的。

##  <a name="id"></a> Id

返回在当前上下文所属的计划程序中是唯一的当前上下文的标识符。

```
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>返回值

如果当前上下文附加到计划程序，在当前上下文属于; 计划程序中是唯一的当前上下文的标识符否则为值`-1`。

##  <a name="iscurrenttaskcollectioncanceling"></a> IsCurrentTaskCollectionCanceling

返回一个指示是否当前正在执行内联在当前上下文的任务集合正处于活动状态的取消操作 （或不久将）。

```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>返回值

如果计划附加到调用上下文，并且任务组该上下文上执行内联任务，指示该任务组正处于活动状态的取消操作 （或不久将）;否则为值`false`。

##  <a name="issynchronouslyblocked"></a> IsSynchronouslyBlocked

确定以同步方式阻止上下文。 若要以同步方式阻止它显式执行的操作导致阻塞，则认为该上下文。

```
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>返回值

是否以同步方式阻止上下文。

### <a name="remarks"></a>备注

若要以同步方式阻止它显式执行的操作导致阻塞，则认为该上下文。 在线程计划程序上，这将指示对 `Context::Block` 方法或通过 `Context::Block` 方法构建的同步对象的直接调用。

此方法的返回值是瞬间完成示例的上下文是否以同步方式阻止。 此值可能会过时的时刻，它将返回并仅可以非常具体的情况下使用。

##  <a name="operator_delete"></a> 运算符 delete

一个`Context`由运行时在内部销毁对象。 无法显式删除它。

```
void operator delete(void* _PObject);
```

### <a name="parameters"></a>参数

*_PObject*<br/>
指向要删除的对象的指针。

##  <a name="oversubscribe"></a> 超额订阅

注入一个计划程序的其他虚拟处理器的其中一个该计划程序中的虚拟处理器上执行的上下文调用时的代码块的持续时间。

```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>参数

*_BeginOversubscription*<br/>
如果 **，则返回 true**，则表示应过度订阅的持续时间添加额外虚拟处理器。 如果**false**，指示过度订阅应结束，并且应删除以前添加的虚拟处理器。

##  <a name="schedulegroupid"></a> ScheduleGroupId

返回当前上下文正在处理的计划组的标识符。

```
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>返回值

如果当前上下文附加到计划程序，并使用计划组，计划程序的标识符进行分组的当前上下文正常否则为值`-1`。

##  <a name="unblock"></a> 取消阻止

取消阻止上下文，并使其成为可运行。

```
virtual void Unblock() = 0;
```

### <a name="remarks"></a>备注

它是对的调用完全合法`Unblock`方法以相应地调用之前[块](#block)方法。 只要调用`Block`和`Unblock`恰当配对方法、 运行时正确处理任何顺序的自然竞争。 `Unblock`调用之前即将`Block`调用只是求反的效果`Block`调用。

有几个例外情况可能会引发此方法。 如果上下文尝试调用`Unblock`方法本身[context_self_unblock](context-self-unblock-class.md)将引发异常。 如果调用`Block`并`Unblock`未恰当配对 (例如，两次调用`Unblock`当前正在运行的上下文所做)、 一个[context_unblock_unbalanced](context-unblock-unbalanced-class.md)将引发异常。

请注意，你的代码发布为另一个线程可以调用其上下文的点之间没有重要的时间段`Unblock`方法和其中的实际方法调用的点`Block`进行。 在此时间段内，您不能调用任何可能会反过来阻止或取消阻止其自身原因（例如获取一个锁）的方法。 调用`Block`和`Unblock`方法不会跟踪阻止和取消阻止的原因。 只有一个对象应具有的所有权`Block`和`Unblock`对。

##  <a name="virtualprocessorid"></a> VirtualProcessorId

返回当前上下文在其执行的虚拟处理器的标识符。

```
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>返回值

如果当前上下文附加到计划程序，当前的上下文执行; 的虚拟处理器的标识符否则为值`-1`。

### <a name="remarks"></a>备注

此方法的返回值是在其执行当前上下文的虚拟处理器的瞬时采样。 此值可能在返回时过时并且不可依靠。 通常情况下，此方法用于调试或跟踪目的。

##  <a name="yield"></a> yield

让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。

```
static void __cdecl Yield();
```

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

##  <a name="yieldexecution"></a> YieldExecution

让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。

```
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

此函数是 Visual Studio 2015 中的新增功能，等同于[产生](#yield)正常工作，但是不与 Windows.h 中的 Yield 宏冲突。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[Scheduler 类](scheduler-class.md)<br/>
[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

