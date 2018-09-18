---
title: CurrentScheduler 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e96b9d70e48b63eafb8cb3c6f4938f962114fd39
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059480"
---
# <a name="currentscheduler-class"></a>CurrentScheduler 类
表示与调用上下文关联的当前计划程序的抽象。  
  
## <a name="syntax"></a>语法  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[创建](#create)|创建新的计划程序的行为所描述`_Policy`参数并将其附加到调用上下文。 新创建的计划程序会调用上下文的当前计划程序。|  
|[CreateScheduleGroup](#createschedulegroup)|已重载。 创建新的计划组中与调用上下文关联的计划程序。 采用参数的版本`_Placement`导致任务偏向在该参数指定的位置执行新创建的计划组中。|  
|[分离](#detach)|从调用上下文的当前计划程序中分离，并将还原以前附加的计划程序当前计划程序，如果存在。 此方法返回后，调用上下文然后由以前已经附加到上下文使用的计划程序管理`CurrentScheduler::Create`或`Scheduler::Attach`方法。|  
|[Get](#get)|返回一个指向与调用上下文，也称为当前计划程序关联的计划程序。|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|返回与调用上下文关联的计划程序的虚拟处理器数目。|  
|[GetPolicy](#getpolicy)|返回当前计划程序使用已创建的策略的一个副本。|  
|[Id](#id)|返回当前计划程序的唯一标识符。|  
|[IsAvailableLocation](#isavailablelocation)|确定在当前计划程序中给定位置是否可用。|  
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件句柄传递中的原因`_ShutdownEvent`参数，以与当前上下文关联的计划程序关闭并销毁自身时发出信号。 在该事件发出信号时，已计划至计划程序的所有工作都已完成。 可以通过此方法注册多个关闭事件。|  
|[ScheduleTask](#scheduletask)|已重载。 计划内与调用上下文关联的计划程序的轻型任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。|  
  
## <a name="remarks"></a>备注  
 如果没有计划程序 (请参阅[计划程序](scheduler-class.md)) 与调用上下文中的许多方法相关联`CurrentScheduler`类将导致进程的默认计划程序的附件。 这可能表示进程的默认计划程序在此类调用期间创建。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CurrentScheduler`  
  
## <a name="requirements"></a>要求  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="create"></a> 创建 

 创建新的计划程序的行为所描述`_Policy`参数并将其附加到调用上下文。 新创建的计划程序会调用上下文的当前计划程序。  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>参数  
*策略 （_p)*<br/>
计划程序策略，用于描述新创建的计划程序的行为。  
  
### <a name="remarks"></a>备注  
 计划程序附加到调用上下文隐式将引用计数放在计划程序上。  
  
 用其创建计划后`Create`方法时，必须调用[currentscheduler:: Detach](#detach)以便允许计划程序若要关闭的情况下在将来某个时刻的方法。  
  
 如果已附加到不同的计划程序的上下文中调用此方法，现有的计划程序将记住上一个计划程序和新创建的计划程序将成为当前计划程序。 当您调用`CurrentScheduler::Detach`方法在以后上, 一个计划程序还原为当前计划程序。  
  
 此方法会引发异常，包括各种[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)并[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。  
  
##  <a name="createschedulegroup"></a> CreateScheduleGroup 

 创建新的计划组中与调用上下文关联的计划程序。 采用参数的版本`_Placement`导致任务偏向在该参数指定的位置执行新创建的计划组中。  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>参数  
*放置 （_p)*<br/>
对其中的计划组中的任务将偏向执行处的位置的引用。  
  
### <a name="return-value"></a>返回值  
 一个指向新创建的计划组。 这`ScheduleGroup`对象具有在其上放置的初始引用计数。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
 必须调用[版本](schedulegroup-class.md#release)上完成计划工作时的计划组的方法。 计划程序将销毁该计划组时对其进行排队的所有工作已完成。  
  
 请注意，是否显式创建此计划程序，必须释放通过分离当前上下文从其发布在计划程序，参考前的计划中，组的所有引用。  
  
##  <a name="detach"></a> 分离 

 从调用上下文的当前计划程序中分离，并将还原以前附加的计划程序当前计划程序，如果存在。 此方法返回后，调用上下文然后由以前已经附加到上下文使用的计划程序管理`CurrentScheduler::Create`或`Scheduler::Attach`方法。  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>备注  
 `Detach`方法从调度器会隐式删除引用计数。  
  
 如果没有计划程序附加到调用上下文，调用此方法将导致[scheduler_not_attached](scheduler-not-attached-class.md)所引发异常。  
  
 从上下文调用此方法是内部的由计划程序或使用一种方法不已附加的上下文进行管理[scheduler:: attach](scheduler-class.md#attach)或[currentscheduler:: Create](#create)方法，将导致[improper_scheduler_detach](improper-scheduler-detach-class.md)所引发异常。  
  
##  <a name="get"></a> 获取 

 返回一个指向与调用上下文，也称为当前计划程序关联的计划程序。  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>返回值  
 指向与调用上下文 （当前计划程序） 相关联的计划程序的指针。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。 没有其他引用位于`Scheduler`此方法返回的对象。  
  
##  <a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors 

 返回与调用上下文关联的计划程序的虚拟处理器数目。  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>返回值  
 如果计划程序调用的上下文中，为该计划程序; 的虚拟处理器的数目与相关联否则为值`-1`。  
  
### <a name="remarks"></a>备注  
 此方法不会导致计划程序附件如果调用的上下文是不与计划程序相关联。  
  
 此方法的返回值是计划程序与调用上下文关联的虚拟处理器数的瞬时采样。 此值在返回时可能过时。  
  
##  <a name="getpolicy"></a> GetPolicy 

 返回当前计划程序使用已创建的策略的一个副本。  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>返回值  
 使用创建当前计划程序策略的副本。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
##  <a name="id"></a> Id 

 返回当前计划程序的唯一标识符。  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>返回值  
 如果计划程序与调用上下文，该计划程序; 的唯一标识符相关联否则为值`-1`。  
  
### <a name="remarks"></a>备注  
 此方法不会导致计划程序附件如果调用的上下文是不与计划程序相关联。  
  
##  <a name="isavailablelocation"></a> IsAvailableLocation 

 确定在当前计划程序中给定位置是否可用。  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>参数  
*放置 （_p)*<br/>
对在当前计划程序中查询的位置的引用。  
  
### <a name="return-value"></a>返回值  
 有关 `_Placement` 参数指定的位置在当前计划程序中是否可用的指示。  
  
### <a name="remarks"></a>备注  
 此方法不会导致计划程序附件如果调用的上下文是不与计划程序相关联。  
  
 注意，返回值是给定位置是否可用的瞬时采样。 在存在多个计划程序时，动态资源管理可以从计划程序中的任意点添加或移除资源。 如果发生这种情况，那么给定位置的可用性会发生更改。  
  
##  <a name="registershutdownevent"></a> RegisterShutdownEvent 

 Windows 事件句柄传递中的原因`_ShutdownEvent`参数，以与当前上下文关联的计划程序关闭并销毁自身时发出信号。 在该事件发出信号时，已计划至计划程序的所有工作都已完成。 可以通过此方法注册多个关闭事件。  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>参数  
*_ShutdownEvent*<br/>
Windows 事件对象时与当前上下文关联的计划程序关闭并销毁本身由运行时信号的句柄。  
  
### <a name="remarks"></a>备注  
 如果没有计划程序附加到调用上下文，调用此方法将导致[scheduler_not_attached](scheduler-not-attached-class.md)所引发异常。  
  
##  <a name="scheduletask"></a> ScheduleTask 

 计划内与调用上下文关联的计划程序的轻型任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。  
  
```
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```  
  
### <a name="parameters"></a>参数  
*_Proc*<br/>
指向要执行要执行的轻量任务正文的函数的指针。  
  
*数据 （_d)*<br/>
指向将作为参数传递给任务的正文数据的 void 指针。  
  
*放置 （_p)*<br/>
对偏向执行轻量任务的位置的引用。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [Scheduler 类](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



