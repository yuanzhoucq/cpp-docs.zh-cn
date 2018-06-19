---
title: IVirtualProcessorRoot 结构 |Microsoft 文档
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
ms.openlocfilehash: 9620ee391b525356bfdb50b00d7e76c03b480815
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692418"
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
|[IVirtualProcessorRoot::Activate](#activate)|导致与执行上下文接口关联的线程代理`pContext`开始在此虚拟处理器根上执行。|  
|[IVirtualProcessorRoot::Deactivate](#deactivate)|将导致停止调度执行上下文，在此虚拟处理器根上当前正在执行的线程代理。 线程代理将继续执行调用`Activate`方法。|  
|[IVirtualProcessorRoot::EnsureAllTasksVisible](#ensurealltasksvisible)|使数据存储在内存层次结构的单个处理器，以对系统上的所有处理器都可见。 它确保完整内存界定已执行的所有处理器在方法返回之前。|  
|[IVirtualProcessorRoot::GetId](#getid)|返回的虚拟处理器根的唯一标识符。|  
  
## <a name="remarks"></a>备注  
 每个虚拟处理器根具有关联的执行资源。 `IVirtualProcessorRoot`接口继承自[IExecutionResource](iexecutionresource-structure.md)接口。 多个虚拟处理器根可能对应于相同的基础硬件线程。  
  
 资源管理器授予对资源的请求的响应中的计划程序的虚拟处理器根。 计划程序可以使用的虚拟处理器根的激活它的执行上下文中执行工作。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IExecutionResource](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="activate"></a>  Ivirtualprocessorroot:: Activate 方法  
 导致与执行上下文接口关联的线程代理`pContext`开始在此虚拟处理器根上执行。  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 将调度此虚拟处理器根执行上下文的接口。  
  
### <a name="remarks"></a>备注  
 资源管理器将提供的线程代理，如果其中一个不与执行上下文接口相关联 `pContext`  
  
 `Activate`方法可用来启动返回由资源管理器中，新的虚拟处理器根上执行工作或恢复已停用或即将停用的虚拟处理器根上的线程代理。 请参阅[ivirtualprocessorroot:: Deactivate](#deactivate)有关停用的详细信息。 当恢复已停用的虚拟处理器根时，参数`pContext`必须与用于停用的虚拟处理器根的参数相同。  
  
 第一次，对的调用的后续对激活的虚拟处理器根之后`Deactivate`和`Activate`可能相互争用。 这意味着它是可用于资源管理器接收调用接受`Activate`接收之前`Deactivate`所代表的调用。  
  
 在启用虚拟处理器根时，发信号通知到资源管理器中此虚拟处理器根没有当前正在使用。 如果您的计划程序找不到要在此根上执行任何工作，则应调用`Deactivate`通知资源管理器的虚拟处理器根处于空闲状态的方法。 资源管理器使用此数据进行负载平衡系统。  
  
 `invalid_argument` 如果引发自变量`pContext`具有值`NULL`。  
  
 `invalid_operation` 如果引发自变量`pContext`不表示最近已调度由此虚拟处理器根的执行上下文。  
  
 激活的虚拟处理器根的行为都将使基础硬件线程的订阅级别加一。 在订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="deactivate"></a>  Ivirtualprocessorroot:: Deactivate 方法  
 将导致停止调度执行上下文，在此虚拟处理器根上当前正在执行的线程代理。 线程代理将继续执行调用`Activate`方法。  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 当前正通过此根调度上下文。  
  
### <a name="return-value"></a>返回值  
 一个布尔值。 值为`true`表示线程代理返回`Deactivate`方法以响应对的调用`Activate`方法。 值为`false`指示线程代理返回从资源管理器中的通知事件的响应中的方法。 用户模式计划 (UMS) 线程在计划程序上，这表示项出现在计划程序的完成列表中，并且需要该计划程序来处理它们。  
  
### <a name="remarks"></a>备注  
 使用此方法暂时停止执行的虚拟处理器根，当在您的计划程序找不到任何工作。 调用`Deactivate`方法必须源自内`Dispatch`执行上下文的虚拟处理器根上次激活所用的方法。 换而言之，线程代理调用`Deactivate`方法必须是当前在虚拟处理器根执行的一个。 在你未在执行的虚拟处理器根上调用方法可能导致未定义的行为。  
  
 已停用的虚拟处理器根可能通过调用唤醒`Activate`方法，用同一参数中传递到`Deactivate`方法。 计划程序负责确保调用到`Activate`和`Deactivate`方法成对发生，但它们不需要以特定顺序接收。 资源管理器可以处理接收调用`Activate`方法，它接收到的调用之前`Deactivate`所代表的方法。  
  
 如果虚拟处理器根唤醒和返回值从`Deactivate`方法是值`false`，计划程序应查询 UMS 完成列表通过`IUMSCompletionList::GetUnblockNotifications`方法，该信息，对其执行操作，然后随后调用`Deactivate`再次方法。 这应重复之前为此类时间`Deactivate`方法返回的值`true`。  
  
 `invalid_argument` 如果引发自变量`pContext`具有值`NULL`。  
  
 `invalid_operation` 如果尚未激活过虚拟处理器根，则会引发或自变量`pContext`不表示最近已调度由此虚拟处理器根的执行上下文。  
  
 停用的虚拟处理器根的 act 减一基础硬件线程的订阅级别。 在订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="ensurealltasksvisible"></a>  Ivirtualprocessorroot:: Ensurealltasksvisible 方法  
 使数据存储在内存层次结构的单个处理器，以对系统上的所有处理器都可见。 它确保完整内存界定已执行的所有处理器在方法返回之前。  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 当前正通过此虚拟处理器根调度上下文。  
  
### <a name="remarks"></a>备注  
 在你想要添加到计划程序的新工作同步的虚拟处理器根的停用，可能会发现此方法很有用。 出于性能原因，你可能决定将工作项添加到您的计划程序，而不执行内存屏障，这意味着添加一个处理器上执行的线程的工作项不会对所有其他处理器立即可见。 通过结合使用此方法`Deactivate`方法可以确保你的计划程序不会停用其所有虚拟处理器根在工作项存在于计划程序的集合时。  
  
 调用`EnsureAllTasksVisibleThe`方法必须源自内`Dispatch`执行上下文的虚拟处理器根上次激活所用的方法。 换而言之，线程代理调用`EnsureAllTasksVisible`方法必须是当前在虚拟处理器根执行的一个。 在你未在执行的虚拟处理器根上调用方法可能导致未定义的行为。  
  
 `invalid_argument` 如果引发自变量`pContext`具有值`NULL`。  
  
 `invalid_operation` 如果尚未激活过虚拟处理器根，则会引发或自变量`pContext`不表示最近已调度由此虚拟处理器根的执行上下文。  
  
##  <a name="getid"></a>  Ivirtualprocessorroot:: Getid 方法  
 返回的虚拟处理器根的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 整数标识符。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
