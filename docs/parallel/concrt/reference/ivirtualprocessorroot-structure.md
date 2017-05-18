---
title: "IVirtualProcessorRoot 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 2635f1c18dd61127360b8398ad1b0da03f1666d7
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 结构
线程代理可在其中执行的硬件线程的抽象。  
  
## <a name="syntax"></a>语法  
  
```
struct IVirtualProcessorRoot : public IExecutionResource;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Ivirtualprocessorroot:: Activate](#activate)|与执行上下文接口相关联的线程代理将导致`pContext`开始在此虚拟处理器根上执行。|  
|[Ivirtualprocessorroot:: Deactivate](#deactivate)|导致此虚拟处理器根停止调度的执行上下文中当前正在执行的线程代理。 线程代理将继续执行调用`Activate`方法。|  
|[Ivirtualprocessorroot:: Ensurealltasksvisible](#ensurealltasksvisible)|会导致数据存储在内存层次结构的各处理器，以对系统上的所有处理器都可见。 它确保了全内存界定已执行的所有处理器上在方法返回之前。|  
|[Ivirtualprocessorroot:: Getid](#getid)|返回的虚拟处理器根的唯一标识符。|  
  
## <a name="remarks"></a>备注  
 每个虚拟处理器根具有关联的执行资源。 `IVirtualProcessorRoot`接口继承自[IExecutionResource](iexecutionresource-structure.md)接口。 多个虚拟处理器根可能对应于相同的基础硬件线程。  
  
 资源管理器授予对资源的请求的响应中的计划程序的虚拟处理器根。 计划程序可以使用的虚拟处理器根来激活与一个执行上下文，从而执行工作。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IExecutionResource](iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="activate"></a>Ivirtualprocessorroot:: Activate 方法  
 与执行上下文接口相关联的线程代理将导致`pContext`开始在此虚拟处理器根上执行。  
  
```
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 将调度此虚拟处理器根执行上下文的接口。  
  
### <a name="remarks"></a>备注  
 资源管理器将提供的线程代理，如果没有与执行上下文接口相关联`pContext`  
  
 `Activate`方法可返回由资源管理器中，新的虚拟处理器根上开始执行工作或恢复已停用或即将停用的虚拟处理器根上的线程代理。 请参阅[ivirtualprocessorroot:: Deactivate](#deactivate)有关停用的详细信息。 当恢复已停用的虚拟处理器根时，参数`pContext`必须是用来停用的虚拟处理器根的参数相同。  
  
 第一次调用的后面几对激活虚拟处理器根之后`Deactivate`和`Activate`可能会互相争用。 这意味着它是可用于资源管理器接收到呼叫接受`Activate`它接收之前`Deactivate`所代表的调用。  
  
 在启用虚拟处理器根时，发信号通知到资源管理器中此虚拟处理器根没有当前正在使用。 如果您的计划程序无法找到此根上执行任何工作，则应调用`Deactivate`通知资源管理器的虚拟处理器根处于空闲状态的方法。 资源管理器使用此数据进行负载平衡系统。  
  
 `invalid_argument`如果参数`pContext`具有值`NULL`。  
  
 `invalid_operation`如果参数`pContext`不表示最近调度由此虚拟处理器根的执行上下文。  
  
 激活的虚拟处理器根的行为会增加一个基础硬件线程的订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="deactivate"></a>Ivirtualprocessorroot:: Deactivate 方法  
 导致此虚拟处理器根停止调度的执行上下文中当前正在执行的线程代理。 线程代理将继续执行调用`Activate`方法。  
  
```
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 当前正在此根调度上下文。  
  
### <a name="return-value"></a>返回值  
 一个布尔值。 值为`true`指示从返回的线程代理`Deactivate`方法来响应对的调用`Activate`方法。 值为`false`指示从资源管理器中的通知事件的响应中的方法返回的线程代理。 用户模式可计划 (UMS) 线程计划程序上，这指示项目已出现在计划程序的完成列表中，并且需要该计划程序来处理它们。  
  
### <a name="remarks"></a>备注  
 使用此方法若要暂时停止在您的计划程序找不到任何工作时所执行的虚拟处理器根。 调用`Deactivate`方法必须源自内`Dispatch`的执行上下文的虚拟处理器根上次激活所用的方法。 换而言之，调用的线程代理`Deactivate`方法必须是在虚拟处理器根当前正在执行的一个。 在您将不执行的虚拟处理器根上调用的方法可能导致未定义的行为。  
  
 已停用的虚拟处理器根可能会通过调用唤醒`Activate`具有相同的参数中传递到方法`Deactivate`方法。 计划程序负责确保调用到`Activate`和`Deactivate`方法成对的但这些内容并非必需的特定顺序接收。 资源管理器可以处理接收到呼叫`Activate`方法获得对的调用之前`Deactivate`所代表的方法。  
  
 如果虚拟处理器根唤醒和返回值从`Deactivate`方法是值`false`，计划程序应查询 UMS 完成列表通过`IUMSCompletionList::GetUnblockNotifications`方法，该信息，对其执行操作，并随后调用`Deactivate`再次方法。 这应为理想实现之前重复`Deactivate`方法返回的值`true`。  
  
 `invalid_argument`如果参数`pContext`具有值`NULL`。  
  
 `invalid_operation`如果尚未激活过虚拟处理器根，则会引发或参数`pContext`不表示最近调度由此虚拟处理器根的执行上下文。  
  
 停用的虚拟处理器根的 act 减一基础硬件线程的订阅级别。 订阅级别的详细信息，请参阅[iexecutionresource:: Currentsubscriptionlevel](iexecutionresource-structure.md#currentsubscriptionlevel)。  
  
##  <a name="ensurealltasksvisible"></a>Ivirtualprocessorroot:: Ensurealltasksvisible 方法  
 会导致数据存储在内存层次结构的各处理器，以对系统上的所有处理器都可见。 它确保了全内存界定已执行的所有处理器上在方法返回之前。  
  
```
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pContext`  
 当前正由此虚拟处理器根调度上下文。  
  
### <a name="remarks"></a>备注  
 当你想要添加到计划程序的新工作了同步的虚拟处理器根的停用时，可能会发现此方法很有用。 出于性能原因，您可以决定将工作项添加到您的计划程序，无需执行内存屏障，这意味着添加一个处理器上执行的线程的工作项不会立即显示出来的所有其他处理器。 通过结合使用此方法`Deactivate`方法可以确保您的计划程序不会停用其所有虚拟处理器根在工作项存在于您的计划程序集合时。  
  
 调用`EnsureAllTasksVisibleThe`方法必须源自内`Dispatch`的执行上下文的虚拟处理器根上次激活所用的方法。 换而言之，调用的线程代理`EnsureAllTasksVisible`方法必须是在虚拟处理器根当前正在执行的一个。 在您将不执行的虚拟处理器根上调用的方法可能导致未定义的行为。  
  
 `invalid_argument`如果参数`pContext`具有值`NULL`。  
  
 `invalid_operation`如果尚未激活过虚拟处理器根，则会引发或参数`pContext`不表示最近调度由此虚拟处理器根的执行上下文。  
  
##  <a name="getid"></a>Ivirtualprocessorroot:: Getid 方法  
 返回的虚拟处理器根的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 整数标识符。  
  
## <a name="see-also"></a>另请参阅  
 [并发命名空间](concurrency-namespace.md)

