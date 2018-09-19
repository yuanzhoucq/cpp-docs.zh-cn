---
title: IThreadProxy 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
dev_langs:
- C++
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3be0a32de4e0e5b57471722ffa2cf8fcea5fd6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027851"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy 结构
执行线程的抽象。 根据你创建的计划程序的 `SchedulerType` 策略键，资源管理器将授予你由普通的 Win32 线程或用户模式计划 (UMS) 线程支持的线程代理。 UMS 线程在具有 Windows 7 或更高版本的 64 位操作系统上受到支持。  
  
## <a name="syntax"></a>语法  
  
```
struct IThreadProxy;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IThreadProxy::GetId](#getid)|线程代理返回的唯一标识符。|  
|[IThreadProxy::SwitchOut](#switchout)|解除上下文与基础虚拟处理器根的关联。|  
|[IThreadProxy::SwitchTo](#switchto)|从当前正在执行的上下文执行的协作上下文切换到另一个。|  
|[IThreadProxy::YieldToSystem](#yieldtosystem)|导致调用线程执行准备好在当前处理器上运行的另一个线程。 由操作系统选择要执行的下一个线程。|  
  
## <a name="remarks"></a>备注  
 线程代理耦合到执行上下文由接口表示`IExecutionContext`作为调度工作的方式。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IThreadProxy`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="getid"></a>  Ithreadproxy:: Getid 方法  
 线程代理返回的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个唯一整数标识符。  
  
##  <a name="switchout"></a>  Ithreadproxy:: Switchout 方法  
 解除上下文与基础虚拟处理器根的关联。  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>参数  
*switchState*<br/>
指示正在执行切换的线程代理的状态。 参数的类型是`SwitchingProxyState`。  
  
### <a name="remarks"></a>备注  
 如果由于某种原因需要解除上下文与执行它的虚拟处理器根的关联，请使用 `SwitchOut`。 根据传入参数 `switchState`的值，以及它是否在虚拟处理器根上执行，此调用将立即返回或阻塞与上下文关联的线程代理。 调用将参数设置为 `SwitchOut` 的 `Idle` 是错误的。 执行此操作将导致[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。  
  
 当您因资源管理器指示或是请求了临时过度订阅的虚拟处理器根，而要减少计划程序所拥有的虚拟处理器根的数量，并且已完成时，`SwitchOut` 很有用。 在这种情况下应调用此方法[IVirtualProcessorRoot::Remove](iexecutionresource-structure.md#remove)上的虚拟处理器根，进行调用之前`SwitchOut`与参数`switchState`设置为`Blocking`。 这将阻塞线程代理，并且当计划程序中不同的虚拟处理器根可用来执行它时，线程代理将继续执行。 通过调用函数实例的阻塞线程代理可以恢复`SwitchTo`切换到该线程代理的执行上下文。 此外可以通过使用及其关联的上下文来激活虚拟处理器根恢复线程代理。 有关如何执行此操作的详细信息，请参阅[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。  
  
 如果您希望重新初始化虚拟处理器，也可以使用 `SwitchOut`，这样在将来阻塞线程代理或从运行它的虚拟处理器根和它进行调度工作的计划程序暂时分离该线程代理时，可以将虚拟处理器激活。 如果您希望阻塞线程代理，请使用 `SwitchOut` 并将参数 `switchState` 设置为 `Blocking`。 如上所示，稍后可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 将其恢复。 当您想要将该线程代理从运行它的虚拟处理器根和与虚拟处理器关联的计划程序暂时分离时，请使用 `SwitchOut` 并将参数设置为 `Nesting`。 当线程代理在虚拟处理器根上执行时，调用 `SwitchOut` 并将参数 `switchState` 设置为 `Nesting` 将导致根重新初始化，而当前线程代理无需虚拟处理器根也会继续执行。 线程代理被视为已离开计划程序，直到它调用[ithreadproxy:: Switchout](#switchout)方法替换`Blocking`在一个更高版本的时间点。 对将参数设置为 `SwitchOut` 的 `Blocking` 的第二次调用旨在使上下文返回已阻止状态，以便通过 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 在之前与其分离的计划程序中恢复它。 由于它不是在虚拟处理器根上执行的，因此不会发生重新初始化。  
  
 重新初始化后的虚拟处理器根与资源管理器授予您的计划程序的全新虚拟处理器根没有任何不同。 您可以使用 `IVirtualProcessorRoot::Activate`，通过一个执行上下文来激活它，将其用于执行。  
  
 `SwitchOut` 必须在调用`IThreadProxy`接口，表示当前正在执行的线程或结果不确定。  
  
 在随 Visual Studio 2010 一同提供的库和标头中，此方法未采用参数，而且没有重新初始化虚拟处理器根。 为了保留旧行为，提供 `Blocking` 的默认参数值。  
  
##  <a name="switchto"></a>  Ithreadproxy:: Switchto 方法  
 从当前正在执行的上下文执行的协作上下文切换到另一个。  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>参数  
*pContext*<br/>
若要以协作方式切换到执行上下文。  
  
*switchState*<br/>
指示正在执行切换的线程代理的状态。 参数的类型是`SwitchingProxyState`。  
  
### <a name="remarks"></a>备注  
 此方法用于从一个执行上下文切换到另一个，从[iexecutioncontext:: Dispatch](iexecutioncontext-structure.md#dispatch)方法的第一个执行上下文。 该方法将相关联的执行上下文`pContext`如果尚未与一个相关联的线程代理使用。 为指定的值确定当前的线程代理的所有权`switchState`参数。  
  
 使用值`Idle`当你想要返回到资源管理器的当前正在执行的线程代理。 调用`SwitchTo`与参数`switchState`设置为`Idle`将导致执行上下文`pContext`开始基础的执行资源上执行。 该线程代理的所有权将转移到资源管理器中，并且您希望返回的执行上下文从`Dispatch`方法之后不久就`SwitchTo`返回，从而完成传输。 已调度线程代理的执行上下文断开线程代理，并在计划程序可以自由地重复使用它或将其销毁，因为它认为合适。  
  
 使用值`Blocking`何时该线程代理进入阻止的状态。 调用`SwitchTo`与参数`switchState`设置为`Blocking`将导致执行上下文`pContext`开始执行，并继续之前阻止当前线程代理。 计划程序保留线程代理的所有权，当线程代理处于`Blocking`状态。 通过调用函数实例的阻塞线程代理可以恢复`SwitchTo`切换到该线程代理的执行上下文。 此外可以通过使用及其关联的上下文来激活虚拟处理器根恢复线程代理。 有关如何执行此操作的详细信息，请参阅[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。  
  
 使用值`Nesting`当你想要暂时分离该线程代理从，运行的虚拟处理器根和计划程序进行调度工作。 调用`SwitchTo`与参数`switchState`设置为`Nesting`将导致执行上下文`pContext`以开始执行，并且当前线程代理也将继续执行而无需虚拟处理器根。 线程代理被视为已离开计划程序，直到它调用[ithreadproxy:: Switchout](#switchout)方法在一个更高版本的时间点。 `IThreadProxy::SwitchOut`方法无法阻塞线程代理，直到虚拟处理器根是可用于重新计划它。  
  
 `SwitchTo` 必须在调用`IThreadProxy`接口，表示当前正在执行的线程或结果不确定。 该函数将引发`invalid_argument`如果将参数`pContext`设置为`NULL`。  
  
##  <a name="yieldtosystem"></a>  Ithreadproxy:: Yieldtosystem 方法  
 导致调用线程执行准备好在当前处理器上运行的另一个线程。 由操作系统选择要执行的下一个线程。  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>备注  
 当调用由常规的 Windows 线程，支持的线程代理`YieldToSystem`完全相同的 Windows 函数的行为`SwitchToThread`。 但是，如果从用户模式计划 (UMS) 线程，调用`SwitchToThread`函数委托选取要运行用户模式计划程序，而非操作系统的下一个线程的任务。 若要实现的系统中切换到不同的就绪线程所需的效果，请使用`YieldToSystem`。  
  
 `YieldToSystem` 必须在调用`IThreadProxy`接口，表示当前正在执行的线程或结果不确定。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IExecutionContext 结构](iexecutioncontext-structure.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)
