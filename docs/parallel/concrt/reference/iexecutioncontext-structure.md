---
title: IExecutionContext 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b3f33cf98adc011d872a7d71246e6b94afaf4cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059779"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 结构
可以在给定虚拟处理器上运行并可以协作切换上下文的执行上下文的接口。  
  
## <a name="syntax"></a>语法  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IExecutionContext::Dispatch](#dispatch)|当线程代理开始执行特定的执行上下文时调用的方法。 这应该是你的计划程序的主工作例程。|  
|[IExecutionContext::GetId](#getid)|返回的执行上下文的唯一标识符。|  
|[IExecutionContext::GetProxy](#getproxy)|此上下文中执行的线程代理返回的接口。|  
|[IExecutionContext::GetScheduler](#getscheduler)|此执行上下文所属的接口返回到计划程序。|  
|[IExecutionContext::SetProxy](#setproxy)|此执行上下文相关联的线程代理。 关联的线程代理调用此方法之前开始执行上下文的`Dispatch`方法。|  
  
## <a name="remarks"></a>备注  
 如果要实现接口使用并发运行时的资源管理器中的自定义计划，您需要实现`IExecutionContext`接口。 创建由资源管理器中的线程执行代表你的计划程序的工作，通过执行`IExecutionContext::Dispatch`方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IExecutionContext`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="dispatch"></a>  Iexecutioncontext:: Dispatch 方法  
 当线程代理开始执行特定的执行上下文时调用的方法。 这应该是你的计划程序的主工作例程。  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>参数  
*pDispatchState*<br/>
指向要在其下调度此执行上下文的状态的指针。 调度状态的详细信息，请参阅[DispatchState](dispatchstate-structure.md)。  
  
##  <a name="getid"></a>  Iexecutioncontext:: Getid 方法  
 返回的执行上下文的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个唯一整数标识符。  
  
### <a name="remarks"></a>备注  
 应使用的方法`GetExecutionContextId`以获取实现的对象的唯一标识符`IExecutionContext`接口，然后作为方法的参数使用该接口提供由资源管理器。 应该会返回相同的标识符时`GetId`调用函数。  
  
 从不同源中获取的标识符可能导致未定义的行为。  
  
##  <a name="getproxy"></a>  Iexecutioncontext:: Getproxy 方法  
 此上下文中执行的线程代理返回的接口。  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个 `IThreadProxy` 接口。 如果尚未通过调用初始化的执行上下文的线程代理`SetProxy`，该函数必须返回`NULL`。  
  
### <a name="remarks"></a>备注  
 资源管理器将调用`SetProxy`上的执行上下文，方法与`IThreadProxy`作为参数，在进入接口`Dispatch`方法上下文上。 你需要存储此自变量并将其返回到调用`GetProxy()`。  
  
##  <a name="getscheduler"></a>  Iexecutioncontext:: Getscheduler 方法  
 此执行上下文所属的接口返回到计划程序。  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个 `IScheduler` 接口。  
  
### <a name="remarks"></a>备注  
 需要使用有效的执行上下文初始化`IScheduler`之前将其用作方法参数的接口提供由资源管理器。  
  
##  <a name="setproxy"></a>  Iexecutioncontext:: Setproxy 方法  
 此执行上下文相关联的线程代理。 关联的线程代理调用此方法之前开始执行上下文的`Dispatch`方法。  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>参数  
*pThreadProxy*<br/>
即将进入的线程代理的接口`Dispatch`上此执行上下文的方法。  
  
### <a name="remarks"></a>备注  
 您应保存参数`pThreadProxy`并将其返回到调用`GetProxy`方法。 资源管理器可保证执行线程代理时不会更改执行上下文与关联的线程代理`Dispatch`方法。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IThreadProxy 结构](ithreadproxy-structure.md)
