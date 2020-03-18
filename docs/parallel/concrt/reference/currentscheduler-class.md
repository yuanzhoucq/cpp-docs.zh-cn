---
title: CurrentScheduler 类
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: 6bf61af9ff55722553353a045c87501dbd27fad9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427409"
---
# <a name="currentscheduler-class"></a>CurrentScheduler 类

表示与调用上下文关联的当前计划程序的抽象。

## <a name="syntax"></a>语法

```cpp
class CurrentScheduler;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[创建](#create)|创建新的计划程序，该计划程序的行为由 `_Policy` 参数描述，并将其附加到调用上下文。 新创建的计划程序将成为调用上下文的当前计划程序。|
|[CreateScheduleGroup](#createschedulegroup)|已重载。 在与调用上下文关联的计划程序中创建新的计划组。 采用参数的版本 `_Placement` 会导致新创建的计划组内的任务偏离到在该参数指定的位置执行。|
|[分离](#detach)|将当前计划程序与调用上下文分离，并将以前附加的计划程序还原为当前计划程序（如果存在）。 此方法返回后，调用上下文由以前使用 `CurrentScheduler::Create` 或 `Scheduler::Attach` 方法附加到上下文的计划程序管理。|
|[Get](#get)|返回一个指向与调用上下文关联的计划程序的指针，也称为当前计划程序。|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|返回与调用上下文关联的计划程序的当前虚拟处理器数。|
|[GetPolicy](#getpolicy)|返回用来创建当前计划程序的策略的副本。|
|[Id](#id)|返回当前计划程序的唯一标识符。|
|[IsAvailableLocation](#isavailablelocation)|确定在当前计划程序中给定位置是否可用。|
|[RegisterShutdownEvent](#registershutdownevent)|当与当前上下文相关联的计划程序关闭并销毁自身时，导致在 `_ShutdownEvent` 参数中传递的 Windows 事件句柄发出信号。 在事件终止时，已计划计划程序的所有工作都已完成。 可以通过此方法注册多个关闭事件。|
|[ScheduleTask](#scheduletask)|已重载。 在计划程序中计划与调用上下文关联的轻型任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。|

## <a name="remarks"></a>备注

如果没有与调用上下文关联的计划程序（请参阅[计划程序](scheduler-class.md)），则 `CurrentScheduler` 类中的许多方法将导致连接进程的默认计划程序。 这也可能意味着在调用过程中创建了进程的默认计划程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CurrentScheduler`

## <a name="requirements"></a>要求

**标头：** concrt

**命名空间：** 并发

## <a name="create"></a> 创建

创建新的计划程序，该计划程序的行为由 `_Policy` 参数描述，并将其附加到调用上下文。 新创建的计划程序将成为调用上下文的当前计划程序。

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>parameters

*_Policy*<br/>
描述新创建的计划程序的行为的计划程序策略。

### <a name="remarks"></a>备注

计划程序与调用上下文的附件会将引用计数隐式置于计划程序上。

使用 `Create` 方法创建计划程序之后，必须在未来的某个时间点调用[CurrentScheduler：:D etach](#detach)方法，以允许计划程序关闭。

如果从已附加到不同计划程序的上下文中调用此方法，则会将现有计划程序视为前一个计划程序，新创建的计划程序将成为当前计划程序。 稍后在调用 `CurrentScheduler::Detach` 方法时，会将上一个计划程序还原为当前计划程序。

此方法可能会引发各种异常，包括[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。

## <a name="createschedulegroup"></a>CreateScheduleGroup

在与调用上下文关联的计划程序中创建新的计划组。 采用参数的版本 `_Placement` 会导致新创建的计划组内的任务偏离到在该参数指定的位置执行。

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>parameters

*_Placement*<br/>
对计划组中的任务在其下执行的偏差位置的引用。

### <a name="return-value"></a>返回值

指向新创建的计划组的指针。 此 `ScheduleGroup` 对象上放置了初始引用计数。

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

向计划组计划工作完成后，必须对计划组调用[Release](schedulegroup-class.md#release)方法。 当队列中的所有工作完成后，计划程序将销毁计划组。

请注意，如果显式创建了此计划程序，则必须释放所有引用以计划其中的组，然后才能在计划程序上发布引用，方法是将其从当前上下文分离。

## <a name="detach"></a>取出

将当前计划程序与调用上下文分离，并将以前附加的计划程序还原为当前计划程序（如果存在）。 此方法返回后，调用上下文由以前使用 `CurrentScheduler::Create` 或 `Scheduler::Attach` 方法附加到上下文的计划程序管理。

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>备注

`Detach` 方法从计划程序隐式删除引用计数。

如果没有任何计划程序附加到调用上下文，则调用此方法将导致引发[scheduler_not_attached](scheduler-not-attached-class.md)异常。

从由计划程序内部和管理的上下文中调用此方法，或者从使用[计划程序：： Attach](scheduler-class.md#attach)或[CurrentScheduler：： Create](#create)方法之外的方法附加的上下文中调用此方法将导致引发[improper_scheduler_detach](improper-scheduler-detach-class.md)异常。

## <a name="get"></a>获取

返回一个指向与调用上下文关联的计划程序的指针，也称为当前计划程序。

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>返回值

指向与调用上下文关联的计划程序（当前计划程序）的指针。

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。 此方法返回的 `Scheduler` 对象上不会附加引用。

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors

返回与调用上下文关联的计划程序的当前虚拟处理器数。

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>返回值

如果计划程序与调用上下文关联，则为该计划程序的当前虚拟处理器数;否则，值 `-1`。

### <a name="remarks"></a>备注

如果调用上下文尚未与计划程序关联，则此方法不会导致计划程序附件。

此方法的返回值是与调用上下文关联的计划程序的虚拟处理器数的即时采样。 此值在返回时可能过时。

## <a name="getpolicy"></a>GetPolicy

返回用来创建当前计划程序的策略的副本。

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>返回值

用来创建当前计划程序的策略的副本。

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

## <a name="id"></a>识别

返回当前计划程序的唯一标识符。

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>返回值

如果计划程序与调用上下文相关联，则为该计划程序的唯一标识符;否则，值 `-1`。

### <a name="remarks"></a>备注

如果调用上下文尚未与计划程序关联，则此方法不会导致计划程序附件。

## <a name="isavailablelocation"></a>IsAvailableLocation

确定在当前计划程序中给定位置是否可用。

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>parameters

*_Placement*<br/>
对在当前计划程序中查询的位置的引用。

### <a name="return-value"></a>返回值

有关 `_Placement` 自变量指定的位置在当前计划程序中是否可用的指示。

### <a name="remarks"></a>备注

如果调用上下文尚未与计划程序关联，则此方法不会导致计划程序附件。

注意，返回值是给定位置是否可用的瞬时采样。 在存在多个计划程序时，动态资源管理可以从计划程序中的任意点添加或移除资源。 如果发生这种情况，那么给定位置的可用性会发生更改。

## <a name="registershutdownevent"></a>RegisterShutdownEvent

当与当前上下文相关联的计划程序关闭并销毁自身时，导致在 `_ShutdownEvent` 参数中传递的 Windows 事件句柄发出信号。 在事件终止时，已计划计划程序的所有工作都已完成。 可以通过此方法注册多个关闭事件。

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>parameters

*_ShutdownEvent*<br/>
Windows 事件对象的句柄，当与当前上下文关联的计划程序关闭并销毁自身时，运行时将由运行时发出信号。

### <a name="remarks"></a>备注

如果没有任何计划程序附加到调用上下文，则调用此方法将导致引发[scheduler_not_attached](scheduler-not-attached-class.md)异常。

## <a name="scheduletask"></a>ScheduleTask

在计划程序中计划与调用上下文关联的轻型任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>parameters

*_Proc*<br/>
一个指针，指向用于执行轻量任务的主体的函数。

*_Data*<br/>
指向将作为参数传递给任务正文的数据的 void 指针。

*_Placement*<br/>
对偏向执行轻量任务的位置的引用。

### <a name="remarks"></a>备注

如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[Scheduler 类](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
