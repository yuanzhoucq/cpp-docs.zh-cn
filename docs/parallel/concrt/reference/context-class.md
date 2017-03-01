---
title: "上下文类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::Context
dev_langs:
- C++
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 11d8252afdfe9c02869b14f976f8f348513c46b8
ms.lasthandoff: 02/24/2017

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
|[Block 方法](#block)|阻止当前上下文。|  
|[CurrentContext 方法](#currentcontext)|返回与当前上下文的指针。|  
|[GetId 方法](#getid)|返回在上下文所属的计划程序中是唯一的上下文的标识符。|  
|[GetScheduleGroupId 方法](#getschedulegroupid)|返回上下文目前正在从事的计划组的标识符。|  
|[GetVirtualProcessorId 方法](#getvirtualprocessorid)|返回当前正在执行上下文的虚拟处理器的标识符。|  
|[Id 方法](#id)|返回当前上下文，在当前上下文所属的计划程序中是唯一的标识符。|  
|[IsCurrentTaskCollectionCanceling 方法](#iscurrenttaskcollectioncanceling)|返回一个指示是否当前正在执行内联在当前上下文的任务集合正在取消 （或将很快）。|  
|[IsSynchronouslyBlocked 方法](#issynchronouslyblocked)|确定同步阻止该上下文。 如果显式执行的操作，并且导致阻塞被同步阻止，则认为该上下文。|  
|[Oversubscribe 方法](#oversubscribe)|注入一个计划程序额外的虚拟处理器在执行上的虚拟处理器，在该计划程序之一的上下文中调用时的代码块的持续时间。|  
|[ScheduleGroupId 方法](#schedulegroupid)|返回当前上下文正在处理的计划组的标识符。|  
|[Unblock 方法](#unblock)|取消阻止上下文，并使其变为可运行。|  
|[VirtualProcessorId 方法](#virtualprocessorid)|返回当前上下文在其上执行的虚拟处理器的标识符。|  
|[Yield 方法](#yield)|让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。|  
  
## <a name="remarks"></a>备注  
 并发运行时计划程序 (请参阅[计划程序](scheduler-class.md)) 使用执行上下文来执行工作对其进行排队应用程序。 Win32 线程是举例说明如何在 Windows 操作系统上的执行上下文。  
  
 在任何时候，一个计划程序的并发级别等同于授予它通过资源管理器中的虚拟处理器数。 虚拟处理器是处理资源和映射到基础系统的硬件线程的抽象。 在给定时间，只有一个计划程序上下文可以执行一个虚拟处理器。  
  
 计划程序在是合作的性质和正在执行上下文可以在任何时候产生不同的上下文的虚拟处理器，如果它希望进入等待状态。 当它满足其等待时，它不能继续，直到在计划程序中的虚拟处理器可用开始执行它。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Context`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrt.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nameblocka-block"></a><a name="block"></a>块 

 阻止当前上下文。  
  
```
static void __cdecl Block();
```  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
 如果调用的上下文一个虚拟处理器上运行，虚拟处理器将找到可运行的另一个上下文执行还是有可能创建一个新。  
  
 之后`Block`方法已调用，或将调用，它必须与调用配对[解除阻止](#unblock)方法从另一个执行上下文，以使其再次运行。 请注意，您的代码发布为另一个线程将无法调用其上下文的点之间是关键时期内`Unblock`方法和实际方法调用到点`Block`进行。 在此时间段内，您不能调用任何可能会反过来阻止或取消阻止其自身原因（例如获取一个锁）的方法。 调用`Block`和`Unblock`方法不会跟踪阻止和取消阻止的原因。 只有一个对象应具有的所有权`Block` -  `Unblock`对。  
  
 此方法会引发异常，包括各种[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)。  
  
##  <a name="a-namedtora-context"></a><a name="dtor"></a>~ 上下文 

```
virtual ~Context();
```  
  
##  <a name="a-namecurrentcontexta-currentcontext"></a><a name="currentcontext"></a>CurrentContext 

 返回与当前上下文的指针。  
  
```
static Context* __cdecl CurrentContext();
```  
  
### <a name="return-value"></a>返回值  
 指向当前上下文的指针。  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
##  <a name="a-namegetida-getid"></a><a name="getid"></a>GetId 

 返回在上下文所属的计划程序中是唯一的上下文的标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 在上下文所属的计划程序中是唯一的上下文标识符。  
  
##  <a name="a-namegetschedulegroupida-getschedulegroupid"></a><a name="getschedulegroupid"></a>GetScheduleGroupId 

 返回上下文目前正在从事的计划组的标识符。  
  
```
virtual unsigned int GetScheduleGroupId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 目前正计划组上下文的标识符。  
  
### <a name="remarks"></a>备注  
 此方法的返回值是在其执行上下文的计划组的瞬时采样。 如果是在除当前上下文外的其他上下文中调用此方法，则该值可能在返回时过时，不可依靠。 通常情况下，此方法用于调试或跟踪目的。  
  
##  <a name="a-namegetvirtualprocessorida-getvirtualprocessorid"></a><a name="getvirtualprocessorid"></a>GetVirtualProcessorId 

 返回当前正在执行上下文的虚拟处理器的标识符。  
  
```
virtual unsigned int GetVirtualProcessorId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 如果在虚拟处理器上，在其; 当前执行上下文的虚拟处理器的标识符当前执行上下文否则为值`-1`。  
  
### <a name="remarks"></a>备注  
 此方法的返回值是在其执行上下文的虚拟处理器的瞬时采样。 此值可能在返回时过时并且不可依靠。 通常情况下，此方法用于调试或跟踪目的。  
  
##  <a name="a-nameida-id"></a><a name="id"></a>Id 

 返回当前上下文，在当前上下文所属的计划程序中是唯一的标识符。  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>返回值  
 如果当前上下文附加到一个计划程序，当前的上下文，在对当前上下文所属; 计划程序中是唯一的标识符否则为值`-1`。  
  
##  <a name="a-nameiscurrenttaskcollectioncancelinga-iscurrenttaskcollectioncanceling"></a><a name="iscurrenttaskcollectioncanceling"></a>IsCurrentTaskCollectionCanceling 

 返回一个指示是否当前正在执行内联在当前上下文的任务集合正在取消 （或将很快）。  
  
```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```  
  
### <a name="return-value"></a>返回值  
 如果计划附加到调用上下文，并且任务组该上下文上执行内联任务，指示是否该任务组是否正在取消 （或者将很快）;否则为值`false`。  
  
##  <a name="a-nameissynchronouslyblockeda-issynchronouslyblocked"></a><a name="issynchronouslyblocked"></a>IsSynchronouslyBlocked 

 确定同步阻止该上下文。 如果显式执行的操作，并且导致阻塞被同步阻止，则认为该上下文。  
  
```
virtual bool IsSynchronouslyBlocked() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 上下文是否是以同步方式阻止。  
  
### <a name="remarks"></a>备注  
 如果显式执行的操作，并且导致阻塞被同步阻止，则认为该上下文。 在线程计划程序上，这将指示对 `Context::Block` 方法或通过 `Context::Block` 方法构建的同步对象的直接调用。  
  
 此方法的返回值是瞬时的上下文是否以同步方式阻止示例。 此值可能过时返回的并且只能在非常特殊的情况下使用。  
  
##  <a name="a-nameoperatordeletea-operator-delete"></a><a name="operator_delete"></a>运算符 delete 

 一个`Context`由运行时内部销毁对象。 无法显式删除它。  
  
```
void operator delete(void* _PObject);
```  
  
### <a name="parameters"></a>参数  
 `_PObject`  
 指向要删除的对象的指针。  
  
##  <a name="a-nameoversubscribea-oversubscribe"></a><a name="oversubscribe"></a>过度订阅 

 注入一个计划程序额外的虚拟处理器在执行上的虚拟处理器，在该计划程序之一的上下文中调用时的代码块的持续时间。  
  
```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```  
  
### <a name="parameters"></a>参数  
 `_BeginOversubscription`  
 如果`true`，则表示应在超额订阅的持续时间添加额外虚拟处理器。 如果`false`，指示在超额订阅应结束，并且应删除以前添加的虚拟处理器。  
  
##  <a name="a-nameschedulegroupida-schedulegroupid"></a><a name="schedulegroupid"></a>ScheduleGroupId 

 返回当前上下文正在处理的计划组的标识符。  
  
```
static unsigned int __cdecl ScheduleGroupId();
```  
  
### <a name="return-value"></a>返回值  
 如果当前上下文附加到一个计划程序，并且使用计划组上，计划程序的标识符进行分组，当前上下文正在工作否则为值`-1`。  
  
##  <a name="a-nameunblocka-unblock"></a><a name="unblock"></a>取消阻止 

 取消阻止上下文，并使其变为可运行。  
  
```
virtual void Unblock() = 0;
```  
  
### <a name="remarks"></a>备注  
 它是完全合法调用`Unblock`方法相应地调用优先于[块](#block)方法。 只要调用`Block`和`Unblock`恰当配对方法、 运行时正确地处理任何顺序的自然争用。 `Unblock`之前调用`Block`调用只是求反的效果`Block`调用。  
  
 有几个例外情况，可从该方法引发。 如果上下文尝试调用`Unblock`方法本身， [context_self_unblock](context-self-unblock-class.md)将会引发异常。 如果调用`Block`和`Unblock`未恰当配对 (例如，两次调用`Unblock`当前正在运行的上下文所做)、 一个[context_unblock_unbalanced](context-unblock-unbalanced-class.md)将会引发异常。  
  
 请注意，您的代码发布为另一个线程将无法调用其上下文的点之间是关键时期内`Unblock`方法和实际方法调用到点`Block`进行。 在此时间段内，您不能调用任何可能会反过来阻止或取消阻止其自身原因（例如获取一个锁）的方法。 调用`Block`和`Unblock`方法不会跟踪阻止和取消阻止的原因。 只有一个对象应具有的所有权`Block`和`Unblock`对。  
  
##  <a name="a-namevirtualprocessorida-virtualprocessorid"></a><a name="virtualprocessorid"></a>VirtualProcessorId 

 返回当前上下文在其上执行的虚拟处理器的标识符。  
  
```
static unsigned int __cdecl VirtualProcessorId();
```  
  
### <a name="return-value"></a>返回值  
 如果当前上下文附加到一个计划程序，当前上下文执行; 的虚拟处理器的标识符否则为值`-1`。  
  
### <a name="remarks"></a>备注  
 此方法的返回值是在其执行的当前上下文的虚拟处理器的瞬时采样。 此值可能在返回时过时并且不可依靠。 通常情况下，此方法用于调试或跟踪目的。  
  
##  <a name="a-nameyielda-yield"></a><a name="yield"></a>Yield 

 让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。  
  
```
static void __cdecl Yield();
```  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
##  <a name="a-nameyieldexecutiona-yieldexecution"></a><a name="yieldexecution"></a>YieldExecution 

 让出执行，这样另一个上下文可进行执行。 如果没有其他上下文可接受执行，则计划程序可将执行让出给另一个操作系统线程。  
  
```
static void __cdecl YieldExecution();
```  
  
### <a name="remarks"></a>备注  
 如果当前没有计划程序与调用上下文关联,此方法将导致进程的默认计划程序正被创建和/或附加到调用上下文。  
  
 此函数是中的新增功能[!INCLUDE[vs_dev14](../../../ide/includes/vs_dev14_md.md)]和等同于[产生](#yield)起作用，但不是在 Windows.h 中的 Yield 宏与冲突。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [Scheduler 类](scheduler-class.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




