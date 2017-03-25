---
title: "CurrentScheduler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 9536dd28eeb375f3b9e018539cefb338812e340b
ms.lasthandoff: 03/17/2017

---
# <a name="currentscheduler-class"></a>CurrentScheduler 类
表示与调用上下文关联的当前计划程序的抽象。  
  
## <a name="syntax"></a>语法  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[创建](#create)|创建新的计划程序由描述其行为`_Policy`参数并将其附加到调用上下文。 新创建的计划程序将成为的当前计划程序调用的上下文。|  
|[CreateScheduleGroup](#createschedulegroup)|已重载。 创建新的计划组与调用上下文相关联的计划程序中。 采用参数的版本`_Placement`会导致任务偏向在该参数指定的位置执行新创建的计划组中。|  
|[分离](#detach)|分离当前计划程序中调用的上下文和还原以前附加的计划程序当前计划程序，如果存在。 然后，由以前被附加到上下文使用的计划程序管理此方法返回后，调用上下文`CurrentScheduler::Create`或`Scheduler::Attach`方法。|  
|[获取](#get)|与调用上下文，也称为当前计划程序关联的计划程序返回的指针。|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|返回与调用上下文相关的计划程序的当前虚拟处理器数。|  
|[GetPolicy](#getpolicy)|返回当前计划程序使用已创建的策略的副本。|  
|[Id](#id)|返回当前计划程序的唯一标识符。|  
|[IsAvailableLocation](#isavailablelocation)|确定在当前计划程序中给定位置是否可用。|  
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件句柄传入的原因`_ShutdownEvent`参数，以与当前上下文关联的计划程序关闭和销毁本身时发出信号。 发出事件信号时，已计划至计划程序的所有工作都都完成。 可以通过此方法注册多个关闭事件。|  
|[ScheduleTask](#scheduletask)|已重载。 安排与调用上下文相关联的计划程序中的轻量任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。|  
  
## <a name="remarks"></a>备注  
 如果没有计划程序 (请参阅[计划程序](scheduler-class.md)) 与调用上下文中的许多方法相关联`CurrentScheduler`类将导致附加的进程的默认计划。 这可能意味着，在此类调用期间，才创建进程的默认计划。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CurrentScheduler`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="create"></a>创建 

 创建新的计划程序由描述其行为`_Policy`参数并将其附加到调用上下文。 新创建的计划程序将成为的当前计划程序调用的上下文。  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>参数  
 `_Policy`  
 计划程序策略描述新创建的计划程序的行为。  
  
### <a name="remarks"></a>备注  
 计划程序连接到调用上下文隐式将引用计数放在计划程序。  
  
 用其创建计划后`Create`方法时，必须调用[currentscheduler:: Detach](#detach)为了允许计划程序关闭的情况下在将来某个时刻的方法。  
  
 如果已附加到不同的计划程序上下文中调用此方法，现有的计划程序将被视为前一个计划程序，并且新创建的计划程序将成为当前计划程序。 当您调用`CurrentScheduler::Detach`以后前, 一个计划程序的方法还原当前计划程序。  
  
 此方法会引发异常，包括各种[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 创建新的计划组与调用上下文相关联的计划程序中。 采用参数的版本`_Placement`会导致任务偏向在该参数指定的位置执行新创建的计划组中。  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>参数  
 `_Placement`  
 对其中的计划组中的任务将偏向执行在一个位置的引用。  
  
### <a name="return-value"></a>返回值  
 指向新创建的计划组的指针。 这`ScheduleGroup`对象具有在其上放置一个初始引用计数。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
 必须调用[版本](schedulegroup-class.md#release)方法完成计划工作时的计划组。 计划程序将会销毁计划组时对其进行排队的所有工作已完成。  
  
 请注意，是否显式创建此计划程序，必须释放内的计划组，通过分离从其当前上下文中发布该计划程序上的引用之前的所有引用。  
  
##  <a name="detach"></a>分离 

 分离当前计划程序中调用的上下文和还原以前附加的计划程序当前计划程序，如果存在。 然后，由以前被附加到上下文使用的计划程序管理此方法返回后，调用上下文`CurrentScheduler::Create`或`Scheduler::Attach`方法。  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>备注  
 `Detach`方法隐式从计划程序中移除的引用计数。  
  
 如果没有计划程序附加到调用上下文，调用此方法将导致[scheduler_not_attached](scheduler-not-attached-class.md)所引发异常。  
  
 内部且正由一个计划程序或已附加以外使用的方法的上下文管理上下文中调用此方法是[scheduler:: attach](scheduler-class.md#attach)或[currentscheduler:: Create](#create)方法，将导致[improper_scheduler_detach](improper-scheduler-detach-class.md)所引发异常。  
  
##  <a name="get"></a>获取 

 与调用上下文，也称为当前计划程序关联的计划程序返回的指针。  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>返回值  
 指向与调用上下文 （当前计划程序） 相关联的计划程序的指针。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。 没有其他引用放置在`Scheduler`此方法返回的对象。  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 返回与调用上下文相关的计划程序的当前虚拟处理器数。  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>返回值  
 如果计划程序与调用上下文，当前为该计划程序; 的虚拟处理器数否则为值`-1`。  
  
### <a name="remarks"></a>备注  
 此方法不会导致计划程序连接如果调用的上下文已不与计划程序相关联。  
  
 此方法的返回值是与调用上下文相关的计划程序的虚拟处理器数的瞬时采样。 此值在返回时可能过时。  
  
##  <a name="getpolicy"></a>GetPolicy 

 返回当前计划程序使用已创建的策略的副本。  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>返回值  
 策略的副本，创建当前计划程序时使用。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
##  <a name="id"></a>Id 

 返回当前计划程序的唯一标识符。  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>返回值  
 如果调度程序调用的上下文中，为该计划程序; 的唯一标识符与相关联否则为值`-1`。  
  
### <a name="remarks"></a>备注  
 此方法不会导致计划程序连接如果调用的上下文已不与计划程序相关联。  
  
##  <a name="isavailablelocation"></a>IsAvailableLocation 

 确定在当前计划程序中给定位置是否可用。  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>参数  
 `_Placement`  
 对在当前计划程序中查询的位置的引用。  
  
### <a name="return-value"></a>返回值  
 有关 `_Placement` 参数指定的位置在当前计划程序中是否可用的指示。  
  
### <a name="remarks"></a>备注  
 此方法不会导致计划程序连接如果调用的上下文已不与计划程序相关联。  
  
 注意，返回值是给定位置是否可用的瞬时采样。 在存在多个计划程序时，动态资源管理可以从计划程序中的任意点添加或移除资源。 如果发生这种情况，那么给定位置的可用性会发生更改。  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Windows 事件句柄传入的原因`_ShutdownEvent`参数，以与当前上下文关联的计划程序关闭和销毁本身时发出信号。 发出事件信号时，已计划至计划程序的所有工作都都完成。 可以通过此方法注册多个关闭事件。  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>参数  
 `_ShutdownEvent`  
 Windows 事件对象与当前上下文关联的计划程序关闭且销毁本身时由运行时信号的句柄。  
  
### <a name="remarks"></a>备注  
 如果没有计划程序附加到调用上下文，调用此方法将导致[scheduler_not_attached](scheduler-not-attached-class.md)所引发异常。  
  
##  <a name="scheduletask"></a>ScheduleTask 

 安排与调用上下文相关联的计划程序中的轻量任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。  
  
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
 `_Proc`  
 指向要执行来执行轻量任务的主体的函数的指针。  
  
 `_Data`  
 指向将作为参数传递给任务的主体的数据的 void 指针。  
  
 `_Placement`  
 对偏向执行轻量任务的位置的引用。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [Scheduler 类](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




