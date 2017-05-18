---
title: "IExecutionContext 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
ms.openlocfilehash: 4c4301d7afe46249d6d67ab2a6ec0a9fc2c7935e
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

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
|[Iexecutioncontext:: Dispatch](#dispatch)|当线程代理开始执行特定的执行上下文时调用的方法。 这应该是您的计划程序的主工作例程。|  
|[Iexecutioncontext:: Getid](#getid)|返回的执行上下文的唯一标识符。|  
|[Iexecutioncontext:: Getproxy](#getproxy)|此上下文中执行的线程代理返回的接口。|  
|[Iexecutioncontext:: Getscheduler](#getscheduler)|此执行上下文所属的接口返回指向计划程序。|  
|[Iexecutioncontext:: Setproxy](#setproxy)|将与此执行上下文关联的线程代理。 关联的线程代理调用此方法之前便可开始执行上下文的`Dispatch`方法。|  
  
## <a name="remarks"></a>备注  
 如果要实现的接口与并发运行时的资源管理器中的自定义计划，您需要实现`IExecutionContext`接口。 创建由资源管理器中的线程执行代表您的计划程序的工作通过执行`IExecutionContext::Dispatch`方法。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IExecutionContext`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="dispatch"></a>Iexecutioncontext:: Dispatch 方法  
 当线程代理开始执行特定的执行上下文时调用的方法。 这应该是您的计划程序的主工作例程。  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pDispatchState`  
 指向在其下调度此执行上下文的状态的指针。 调度状态的详细信息，请参阅[DispatchState](dispatchstate-structure.md)。  
  
##  <a name="getid"></a>Iexecutioncontext:: Getid 方法  
 返回的执行上下文的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个唯一整数标识符。  
  
### <a name="remarks"></a>备注  
 应使用方法`GetExecutionContextId`若要获取实现的对象的唯一标识符`IExecutionContext`接口，然后以参数形式向方法使用该接口提供由资源管理器。 您应返回相同的标识符时`GetId`调用函数。  
  
 获取从不同源的标识符可能导致未定义的行为。  
  
##  <a name="getproxy"></a>Iexecutioncontext:: Getproxy 方法  
 此上下文中执行的线程代理返回的接口。  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个 `IThreadProxy` 接口。 如果尚未初始化通过调用执行上下文的线程代理`SetProxy`，该函数必须返回`NULL`。  
  
### <a name="remarks"></a>备注  
 资源管理器将调用`SetProxy`上的执行上下文，方法与`IThreadProxy`接口作为参数，在输入前`Dispatch`方法上下文上。 我们希望您存储该参数，并将其返回到调用`GetProxy()`。  
  
##  <a name="getscheduler"></a>Iexecutioncontext:: Getscheduler 方法  
 此执行上下文所属的接口返回指向计划程序。  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个 `IScheduler` 接口。  
  
### <a name="remarks"></a>备注  
 所需初始化使用一个有效的执行上下文`IScheduler`接口之前使用以参数形式向方法提供由资源管理器。  
  
##  <a name="setproxy"></a>Iexecutioncontext:: Setproxy 方法  
 将与此执行上下文关联的线程代理。 关联的线程代理调用此方法之前便可开始执行上下文的`Dispatch`方法。  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pThreadProxy`  
 即将进入的线程代理接口`Dispatch`上此执行上下文的方法。  
  
### <a name="remarks"></a>备注  
 您应保存该参数`pThreadProxy`并将其返回到调用`GetProxy`方法。 资源管理器保证，执行线程代理时，使用执行上下文关联的线程代理将不会更改`Dispatch`方法。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IThreadProxy 结构](ithreadproxy-structure.md)

