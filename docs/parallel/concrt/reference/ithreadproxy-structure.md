---
title: IThreadProxy 结构 |Microsoft 文档
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
ms.openlocfilehash: fbf59302a73374f08f1c226c1e7e56202654dcfb
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693203"
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
|[IThreadProxy::SwitchTo](#switchto)|到另一个从当前正在执行的上下文中执行的协作上下文切换。|  
|[IThreadProxy::YieldToSystem](#yieldtosystem)|导致调用线程执行准备好在当前处理器上运行的另一个线程。 由操作系统选择要执行的下一个线程。|  
  
## <a name="remarks"></a>备注  
 线程代理耦合到执行上下文由接口表示`IExecutionContext`作为一种调度工作。  
  
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
 唯一的整数标识符。  
  
##  <a name="switchout"></a>  Ithreadproxy:: Switchout 方法  
 解除上下文与基础虚拟处理器根的关联。  
  
```
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```  
  
### <a name="parameters"></a>参数  
 `switchState`  
 指示正在执行切换线程代理的状态。 该参数属于类型`SwitchingProxyState`。  
  
### <a name="remarks"></a>备注  
 如果由于某种原因需要解除上下文与执行它的虚拟处理器根的关联，请使用 `SwitchOut`。 根据传入参数 `switchState`的值，以及它是否在虚拟处理器根上执行，此调用将立即返回或阻塞与上下文关联的线程代理。 调用将参数设置为 `SwitchOut` 的 `Idle` 是错误的。 这样将导致[invalid_argument](../../../standard-library/invalid-argument-class.md)异常。  
  
 当您因资源管理器指示或是请求了临时过度订阅的虚拟处理器根，而要减少计划程序所拥有的虚拟处理器根的数量，并且已完成时，`SwitchOut` 很有用。 在这种情况下应调用该方法[IVirtualProcessorRoot::Remove](http://msdn.microsoft.com/en-us/ad699b4a-1972-4390-97ee-9c083ba7d9e4)上的虚拟处理器根，请在进行调用之前`SwitchOut`与参数`switchState`设置为`Blocking`。 这将阻塞线程代理，并且当计划程序中不同的虚拟处理器根可用来执行它时，线程代理将继续执行。 可以通过调用函数中恢复阻塞线程代理`SwitchTo`切换到该线程代理的执行上下文。 您还可以通过使用其相关联的上下文来激活的虚拟处理器根继续线程代理。 有关如何执行此操作的详细信息，请参阅[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。  
  
 如果您希望重新初始化虚拟处理器，也可以使用 `SwitchOut`，这样在将来阻塞线程代理或从运行它的虚拟处理器根和它进行调度工作的计划程序暂时分离该线程代理时，可以将虚拟处理器激活。 如果您希望阻塞线程代理，请使用 `SwitchOut` 并将参数 `switchState` 设置为 `Blocking`。 如上所示，稍后可以使用 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 将其恢复。 当您想要将该线程代理从运行它的虚拟处理器根和与虚拟处理器关联的计划程序暂时分离时，请使用 `SwitchOut` 并将参数设置为 `Nesting`。 当线程代理在虚拟处理器根上执行时，调用 `SwitchOut` 并将参数 `switchState` 设置为 `Nesting` 将导致根重新初始化，而当前线程代理无需虚拟处理器根也会继续执行。 线程代理被视为已离开计划程序，直到它调用[ithreadproxy:: Switchout](#switchout)方法替换`Blocking`在一个更高版本的时间点。 对将参数设置为 `SwitchOut` 的 `Blocking` 的第二次调用旨在使上下文返回已阻止状态，以便通过 `SwitchTo` 或 `IVirtualProcessorRoot::Activate` 在之前与其分离的计划程序中恢复它。 由于它不是在虚拟处理器根上执行的，因此不会发生重新初始化。  
  
 重新初始化后的虚拟处理器根与资源管理器授予您的计划程序的全新虚拟处理器根没有任何不同。 您可以使用 `IVirtualProcessorRoot::Activate`，通过一个执行上下文来激活它，将其用于执行。  
  
 `SwitchOut` 必须在调用`IThreadProxy`表示当前正在执行的线程或结果的接口都是未定义。  
  
 在随 Visual Studio 2010 一同提供的库和标头中，此方法未采用参数，而且没有重新初始化虚拟处理器根。 为了保留旧行为，提供 `Blocking` 的默认参数值。  
  
##  <a name="switchto"></a>  Ithreadproxy:: Switchto 方法  
 到另一个从当前正在执行的上下文中执行的协作上下文切换。  
  
```
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 若要以协作方式切换到执行上下文。  
  
 `switchState`  
 指示正在执行切换线程代理的状态。 该参数属于类型`SwitchingProxyState`。  
  
### <a name="remarks"></a>备注  
 使用此方法可从一个执行上下文切换到另一个字符串，从[iexecutioncontext:: Dispatch](iexecutioncontext-structure.md#dispatch)方法的第一个执行上下文。 该方法将执行上下文相关联`pContext`与如果尚未与一个相关联的线程代理。 由你为指定的值来确定当前的线程代理的所有权`switchState`自变量。  
  
 使用值`Idle`当你想要返回到资源管理器的当前正在执行的线程代理。 调用`SwitchTo`与参数`switchState`设置为`Idle`将导致执行上下文`pContext`开始执行的基础的执行资源上。 此线程代理的所有权将转移到资源管理器中，并且您希望返回的执行上下文从`Dispatch`方法之后不久`SwitchTo`返回时，若要完成传输。 已调度线程代理的执行上下文的线程代理，从不再关联时，计划程序可以自由重用它或销毁它，因为它认为合适。  
  
 使用值`Blocking`您希望此线程代理输入受阻的状态。 调用`SwitchTo`与参数`switchState`设置为`Blocking`将导致执行上下文`pContext`开始执行，并会在恢复之前阻止当前线程代理。 计划程序会保留线程代理的所有权，当线程代理处于`Blocking`状态。 可以通过调用函数中恢复阻塞线程代理`SwitchTo`切换到该线程代理的执行上下文。 您还可以通过使用其相关联的上下文来激活的虚拟处理器根继续线程代理。 有关如何执行此操作的详细信息，请参阅[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)。  
  
 使用值`Nesting`当你想要暂时分离该线程代理从运行的虚拟处理器根和进行调度工作计划程序。 调用`SwitchTo`与参数`switchState`设置为`Nesting`将导致执行上下文`pContext`以开始执行，并且当前线程代理也会继续执行而无需虚拟处理器根。 线程代理被视为已离开计划程序，直到它调用[ithreadproxy:: Switchout](#switchout)方法在一个更高版本的时间点。 `IThreadProxy::SwitchOut`方法无法阻塞线程代理，直到程序虚拟处理器根可用来重新计划它。  
  
 `SwitchTo` 必须在调用`IThreadProxy`表示当前正在执行的线程或结果的接口都是未定义。 该函数将引发`invalid_argument`如果参数`pContext`设置为`NULL`。  
  
##  <a name="yieldtosystem"></a>  Ithreadproxy:: Yieldtosystem 方法  
 导致调用线程执行准备好在当前处理器上运行的另一个线程。 由操作系统选择要执行的下一个线程。  
  
```
virtual void YieldToSystem() = 0;
```  
  
### <a name="remarks"></a>备注  
 在由正则 Windows 线程，支持的线程代理被调用时`YieldToSystem`完全一样 Windows 函数的行为`SwitchToThread`。 但是，当从用户模式计划 (UMS) 线程，调用`SwitchToThread`函数委托选取下一个线程运行到用户模式计划，而不是操作系统的任务。 若要实现所需的效果的系统中切换到不同的就绪线程，使用`YieldToSystem`。  
  
 `YieldToSystem` 必须在调用`IThreadProxy`表示当前正在执行的线程或结果的接口都是未定义。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IExecutionContext 结构](iexecutioncontext-structure.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IVirtualProcessorRoot 结构](ivirtualprocessorroot-structure.md)
