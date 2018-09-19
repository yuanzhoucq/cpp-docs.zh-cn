---
title: IVirtualProcessorRoot 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
dev_langs:
- C++
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb34946a9860746bbe96c5ec9bcd96a990c5f281
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022575"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 结构
线程代理可在其中执行的硬件线程的抽象。  
  
## <a name="syntax"></a>语法  
  
```
struct IVirtualProcessorRoot : public IExecutionResource;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IVirtualProcessorRoot::Activate](#activate)|与执行上下文接口关联的线程代理将导致`pContext`开始执行此虚拟处理器根上。|  
|[IVirtualProcessorRoot::Deactivate](#deactivate)|将导致停止调度的执行上下文此虚拟处理器根上当前正在执行的线程代理。 线程代理将继续执行调用`Activate`方法。|  
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|会导致数据存储在内存层次结构的各个处理器，若要对系统上的所有处理器都可见。 它可确保完整内存界定已执行的所有处理器在方法返回之前。|  
|[IVirtualProcessorRoot::GetId](#getid)|返回虚拟处理器根的唯一标识符。|  
  
## <a name="remarks"></a>备注  
 每个虚拟处理器根具有关联的执行资源。 `IVirtualProcessorRoot`接口继承自[IExecutionResource](iexecutionresource-structure.md)接口。 多个虚拟处理器根可能对应于相同的基础硬件线程。  
  
 资源管理器授予对资源的请求响应中的计划程序的虚拟处理器根。 计划程序可以使用的虚拟处理器根来激活它的执行上下文中执行工作。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IExecutionResource](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="activate"></a>  Ivirtualprocessorroot:: Activate 方法  
 与执行上下文接口关联的线程代理将导致`pContext`开始执行此虚拟处理器根上。  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
*pContext*<br/>
将此虚拟处理器根调度执行上下文的接口。  
  
### <a name="remarks"></a>备注  
 资源管理器将提供的线程代理，如果没有与执行上下文接口相关联 `pContext`  
  
 `Activate`方法可用于开始返回由资源管理器中，新的虚拟处理器根上执行工作，或继续线程代理已停用或即将停用的虚拟处理器根上。 请参阅[ivirtualprocessorroot:: Deactivate](#deactivate)有关停用的详细信息。 当恢复已停用的虚拟处理器根，该参数`pContext`必须与用于停用的虚拟处理器根的参数相同。  
  
 第一次调用到后续对激活虚拟处理器根后`Deactivate`和`Activate`可能会互相争用。 这意味着可为资源管理器接收到调用接受`Activate`它接收之前`Deactivate`所代表的调用。  
  
 激活后的虚拟处理器根，发信号通知到资源管理器中此虚拟处理器根是当前正忙于工作。 如果你的计划程序找不到此根上执行任何工作，则应调用`Deactivate`通知资源管理器的虚拟处理器根处于空闲状态的方法。 资源管理器使用此数据进行负载平衡系统。  
  
 `invalid_argument` 如果引发参数`pContext`具有值`NULL`。  
  
 `invalid_operation` 如果引发参数`pContext`不表示最近调度由此虚拟处理器根的执行上下文。  
  
 激活的虚拟处理器根的操作会基础硬件线程的订阅级别增加 1。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="deactivate"></a>  Ivirtualprocessorroot:: Deactivate 方法  
 将导致停止调度的执行上下文此虚拟处理器根上当前正在执行的线程代理。 线程代理将继续执行调用`Activate`方法。  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
*pContext*<br/>
当前正在此根调度上下文。  
  
### <a name="return-value"></a>返回值  
 一个布尔值。 值为`true`指示从返回的线程代理`Deactivate`方法以响应对的调用`Activate`方法。 值为`false`指示线程代理返回从资源管理器中的通知事件的响应中的方法。 对于用户模式计划 (UMS) 线程计划程序，这表示项目出现在计划程序的完成列表中，并处理其所需的计划程序。  
  
### <a name="remarks"></a>备注  
 使用此方法以暂停执行虚拟处理器根时在你的计划程序找不到任何工作。 调用`Deactivate`方法内必须源自`Dispatch`虚拟处理器根上次激活所用的执行上下文的方法。 换而言之，线程代理调用`Deactivate`方法必须是一个虚拟处理器根上当前正在执行。 在您将不执行的虚拟处理器根上调用该方法可能导致未定义的行为。  
  
 已停用的虚拟处理器根可能会通过调用唤醒`Activate`方法，使用同一参数中传递给`Deactivate`方法。 计划程序负责确保为调用`Activate`和`Deactivate`配对方法，但它们不需要按特定顺序接收。 资源管理器可以处理接收到呼叫`Activate`方法获得调用之前`Deactivate`所代表的方法。  
  
 如果虚拟处理器根唤醒和返回值从`Deactivate`方法将值`false`，计划程序应查询 UMS 完成列表通过`IUMSCompletionList::GetUnblockNotifications`方法，处理的该信息，然后随后调用`Deactivate`再次方法。 这应为理想实现之前重复`Deactivate`方法将返回值`true`。  
  
 `invalid_argument` 如果引发参数`pContext`具有值`NULL`。  
  
 `invalid_operation` 如果尚未激活过虚拟处理器根，则会引发或自变量`pContext`不表示最近调度由此虚拟处理器根的执行上下文。  
  
 停用的虚拟处理器根的 act 减一的基础硬件线程的订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="ensurealltasksvisible"></a>  Ivirtualprocessorroot:: Ensurealltasksvisible 方法  
 会导致数据存储在内存层次结构的各个处理器，若要对系统上的所有处理器都可见。 它可确保完整内存界定已执行的所有处理器在方法返回之前。  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
*pContext*<br/>
当前正由此虚拟处理器根调度上下文。  
  
### <a name="remarks"></a>备注  
 当你想要添加到计划程序的新工作了同步的虚拟处理器根的停用时，可能会发现此方法很有用。 出于性能原因，您可能决定将工作项添加到你的计划程序，而无需执行内存屏障，这意味着添加一个处理器上执行的线程的工作项不会立即可见的所有其他处理器。 通过结合使用此方法`Deactivate`方法可以确保你的计划程序不会停用其所有虚拟处理器根时计划程序的集合中存在工作项。  
  
 调用`EnsureAllTasksVisibleThe`方法内必须源自`Dispatch`虚拟处理器根上次激活所用的执行上下文的方法。 换而言之，线程代理调用`EnsureAllTasksVisible`方法必须是一个虚拟处理器根上当前正在执行。 在您将不执行的虚拟处理器根上调用该方法可能导致未定义的行为。  
  
 `invalid_argument` 如果引发参数`pContext`具有值`NULL`。  
  
 `invalid_operation` 如果尚未激活过虚拟处理器根，则会引发或自变量`pContext`不表示最近调度由此虚拟处理器根的执行上下文。  
  
##  <a name="getid"></a>  Ivirtualprocessorroot:: Getid 方法  
 返回虚拟处理器根的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 整数标识符。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
