---
title: "Scheduler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
dev_langs: C++
helpviewer_keywords: Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f59b48022cc448b8b06502febdaf1634998ac9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="scheduler-class"></a>Scheduler 类
表示并发运行时计划程序的抽象。  
  
## <a name="syntax"></a>语法  
  
```
class Scheduler;
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[计划程序](#ctor)|对象`Scheduler`类可以仅使用工厂方法，创建或隐式。|  
|[~ Scheduler 析构函数](#dtor)|对象`Scheduler`类隐式被销毁时对它的所有外部引用停止存在。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[附加](#attach)|将计划程序附加到调用上下文。 此方法返回后，由计划程序管理调用的上下文和计划程序将成为当前计划程序。|  
|[创建](#create)|创建新的计划程序描述其行为`_Policy`参数，将初始引用放在计划程序，并将指针返回到它。|  
|[CreateScheduleGroup](#createschedulegroup)|已重载。 创建新的计划组的计划程序中。 采用参数的版本`_Placement`将导致任务偏向在该参数指定的位置执行新创建的计划组中。|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|返回计划程序的当前虚拟处理器数。|  
|[GetPolicy](#getpolicy)|返回用其创建计划的策略的副本。|  
|[Id](#id)|返回计划程序的唯一标识符。|  
|[IsAvailableLocation](#isavailablelocation)|确定给定的位置是否在计划程序上可用。|  
|[引用](#reference)|递增计划程序引用计数。|  
|[RegisterShutdownEvent](#registershutdownevent)|Windows 事件句柄传递中的原因`_Event`参数来计划程序关闭和销毁本身时发出信号。 在该事件处于有信号状态的时间，已计划至计划程序的所有工作都已完成。 可以通过此方法注册多个关闭事件。|  
|[发布](#release)|递减计划程序的引用计数。|  
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|将默认计划程序策略重置为运行时的默认值。 创建一个默认计划程序下, 一步时它将使用运行时默认策略设置。|  
|[ScheduleTask](#scheduletask)|已重载。 计划的计划程序中轻量任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。|  
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|允许用户定义的策略将用于创建默认计划程序。 仅当没有默认计划程序在进程中存在时，可以调用此方法。 已设置了默认策略后，它仍然有效，直到下一步有效调用`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。|  
  
## <a name="remarks"></a>备注  
 并发运行时计划程序使用映射到操作系统执行上下文，如的线程的执行上下文，来执行工作对其进行排队应用程序。 在任何时候，计划程序的并发级别是向它授予通过资源管理器中的虚拟处理器的数量相等。 虚拟处理器是处理资源和映射到基础系统上的硬件线程的抽象。 在给定时间，只有一个计划程序上下文可以执行虚拟处理器上。  
  
 并发运行时将创建一个默认计划程序每个进程来执行并行工作。 此外，你可以创建你自己的计划程序实例和操作使用此类。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Scheduler`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="attach"></a>附加 

 将计划程序附加到调用上下文。 此方法返回后，由计划程序管理调用的上下文和计划程序将成为当前计划程序。  
  
```
virtual void Attach() = 0;
```  
  
### <a name="remarks"></a>备注  
 隐式附加计划程序将在计划程序的引用。  
  
 在某一时刻将来，你必须调用[currentscheduler:: Detach](currentscheduler-class.md#detach)方法，以允许关闭的计划程序。  
  
 如果程序已附加到不同的计划程序的上下文中调用此方法，现有的计划程序将被视为前一个计划程序，并且新创建的计划程序将成为当前计划程序。 当调用`CurrentScheduler::Detach`以后前, 一个计划程序的方法还原当前计划程序。  
  
 此方法将引发[improper_scheduler_attach](improper-scheduler-attach-class.md)如果此计划程序是调用上下文的当前计划程序的异常。  
  
##  <a name="create"></a>创建 

 创建新的计划程序描述其行为`_Policy`参数，将初始引用放在计划程序，并将指针返回到它。  
  
```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>参数  
 `_Policy`  
 计划程序策略描述新创建的计划程序行为。  
  
### <a name="return-value"></a>返回值  
 指向新创建的计划程序的指针。 这`Scheduler`对象具有在其上放置的初始引用计数。  
  
### <a name="remarks"></a>备注  
 用其创建计划后`Create`方法时，必须调用`Release`在某个时间点将来以便删除初始引用计数和允许将关闭的计划程序的方法。  
  
 使用此方法创建的计划未附加到调用上下文。 可以将它附加到上下文使用[附加](#attach)方法。  
  
 此方法会引发异常，包括各种[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)和[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)。  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 创建新的计划组的计划程序中。 采用参数的版本`_Placement`将导致任务偏向在该参数指定的位置执行新创建的计划组中。  
  
```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Placement`  
 对其中的计划组中的任务将偏向于执行的位置的引用。  
  
### <a name="return-value"></a>返回值  
 指向新创建的计划组的指针。 这`ScheduleGroup`对象具有在其上放置的初始引用计数。  
  
### <a name="remarks"></a>备注  
 必须调用[版本](schedulegroup-class.md#release)方法完成计划工作时的计划组。 计划程序将会破坏计划组时对其进行排队所有的工作已完成。  
  
 请注意，是否你显式创建此计划程序，必须释放之前释放在计划程序上的你引用的计划组中，所有引用。  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 返回计划程序的当前虚拟处理器数。  
  
```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 当前的计划程序的虚拟处理器数。  
  
##  <a name="getpolicy"></a>GetPolicy 

 返回用其创建计划的策略的副本。  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 用其创建计划策略的副本。  
  
##  <a name="id"></a>Id 

 返回计划程序的唯一标识符。  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 计划程序唯一标识符。  
  
##  <a name="isavailablelocation"></a>IsAvailableLocation 

 确定给定的位置是否在计划程序上可用。  
  
```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Placement`  
 对有关查询计划程序的位置的引用。  
  
### <a name="return-value"></a>返回值  
 相对值的位置是否由指定`_Placement`自变量是在计划程序上可用。  
  
### <a name="remarks"></a>备注  
 注意，返回值是给定位置是否可用的瞬时采样。 在存在多个计划程序时，动态资源管理可以从计划程序中的任意点添加或移除资源。 如果发生这种情况，那么给定位置的可用性会发生更改。  
  
##  <a name="reference"></a>引用 

 递增计划程序引用计数。  
  
```
virtual unsigned int Reference() = 0 ;
```  
  
### <a name="return-value"></a>返回值  
 新递增的引用计数。  
  
### <a name="remarks"></a>备注  
 这通常用于管理计划程序为组合的生存期。 当计划程序的引用计数降为零时，计划程序将在其所有工作完成后关闭并析构自身。  
  
 该方法将引发[improper_scheduler_reference](improper-scheduler-reference-class.md)异常的引用计数在调用之前如果`Reference`方法为零，默认情况下，调用程序不由计划程序拥有的上下文中。  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Windows 事件句柄传递中的原因`_Event`参数来计划程序关闭和销毁本身时发出信号。 在该事件处于有信号状态的时间，已计划至计划程序的所有工作都已完成。 可以通过此方法注册多个关闭事件。  
  
```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Event`  
 Windows 事件对象将由运行时计划程序关闭，然后销毁本身时信号的句柄。  
  
##  <a name="release"></a>版本 

 递减计划程序的引用计数。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>返回值  
 新递减引用计数。  
  
### <a name="remarks"></a>备注  
 这通常用于管理计划程序为组合的生存期。 当计划程序的引用计数降为零时，计划程序将在其所有工作完成后关闭并析构自身。  
  
##  <a name="resetdefaultschedulerpolicy"></a>ResetDefaultSchedulerPolicy 

 将默认计划程序策略重置为运行时的默认值。 创建一个默认计划程序下, 一步时它将使用运行时默认策略设置。  
  
```
static void __cdecl ResetDefaultSchedulerPolicy();
```  
  
### <a name="remarks"></a>备注  
 在进程中存在一个默认计划程序时，可以调用此方法。 它将不会影响现有的默认计划程序的策略。 但是，如果默认计划程序将要关闭，并且打算在以后创建的新默认值，新的计划程序将使用运行时默认策略设置。  
  
##  <a name="ctor"></a>计划程序 

 对象`Scheduler`类可以仅使用工厂方法，创建或隐式。  
  
```
Scheduler();
```  
  
### <a name="remarks"></a>备注  
 你可以利用许多运行时函数需要计划程序附加到调用上下文时，将隐式创建进程的默认计划程序。 中的方法`CurrentScheduler`类和 PPL 和代理层的功能通常可以执行隐式的附件。  
  
 你还可以创建明确地通过计划程序`CurrentScheduler::Create`方法或`Scheduler::Create`方法。  
  
##  <a name="dtor"></a>~ 计划程序 

 对象`Scheduler`类隐式被销毁时对它的所有外部引用停止存在。  
  
```
virtual ~Scheduler();
```  
  
##  <a name="scheduletask"></a>ScheduleTask 

 计划的计划程序中轻量任务。 轻量任务将放置在运行时确定的计划组中。 采用参数 `_Placement` 的版本导致任务偏向在指定的位置执行。  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```  
  
### <a name="parameters"></a>参数  
 `_Proc`  
 指向要执行执行轻量任务的主体的函数的指针。  
  
 `_Data`  
 指向将作为参数传递给任务的主体的数据的 void 指针。  
  
 `_Placement`  
 对偏向执行轻量任务的位置的引用。  
  
##  <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy 

 允许用户定义的策略将用于创建默认计划程序。 仅当没有默认计划程序在进程中存在时，可以调用此方法。 已设置了默认策略后，它仍然有效，直到下一步有效调用`SetDefaultSchedulerPolicy`或[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)方法。  
  
```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>参数  
 `_Policy`  
 要设置为默认计划程序策略的策略。  
  
### <a name="remarks"></a>备注  
 如果`SetDefaultSchedulerPolicy`方法调用时进程内已存在默认计划程序，则运行时将引发[default_scheduler_exists](default-scheduler-exists-class.md)异常。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [Scheduler 类](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



