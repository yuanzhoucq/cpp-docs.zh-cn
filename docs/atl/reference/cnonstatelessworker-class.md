---
title: "CNonStatelessWorker 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs:
- C++
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: 21
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 804b87bf752aac5cecf64cb61b4d53d6269963f2
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker 类
从线程池中接收请求并将它们传递到创建和销毁的工作对象，对每个请求。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>参数  
 *辅助进程*  
 辅助线程类符合[辅助原型](../../atl/reference/worker-archetype.md)合适的处理请求上排队[CThreadPool](../../atl/reference/cthreadpool-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](#requesttype)|实现[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](#execute)|实现[WorkerArchetype::Execute](worker-archetype.md#execute)。|  
|[CNonStatelessWorker::Initialize](#initialize)|实现[WorkerArchetype::Initialize](worker-archetype.md#initialize)。|  
|[CNonStatelessWorker::Terminate](#terminate)|实现[WorkerArchetype::Terminate](worker-archetype.md#terminate)。|  
  
## <a name="remarks"></a>备注  
 此类是适用于简单的工作线程[CThreadPool](../../atl/reference/cthreadpool-class.md)。 此类不提供其自身的任何请求处理功能。 相反，它实例化的一个实例*工作人员*每个请求并将其对该实例的方法的实现委托。  
  
 此类的好处是，它提供了方便地更改现有辅助线程类的状态模型。 `CThreadPool`将该线程的生存期内创建的单个辅助因此如果 worker 类保存状态，它将跨多个请求保存它。 进行简单包装该类`CNonStatelessWorker`然后再将它与模板`CThreadPool`、 工作和它包含仅限于单个请求的状态的生存期。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
##  <a name="execute"></a>CNonStatelessWorker::Execute  
 实现[WorkerArchetype::Execute](worker-archetype.md#execute)。  

  
```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```  
  
### <a name="remarks"></a>备注  
 此方法创建的一个实例*工作人员*类上的堆栈和调用[初始化](worker-archetype.md#initialize)对该对象。 如果初始化成功，此方法还会调用[Execute](worker-archetype.md#execute)和[终止](worker-archetype.md#terminate)对同一个对象。  

  
##  <a name="initialize"></a>CNonStatelessWorker::Initialize  
 实现[WorkerArchetype::Initialize](worker-archetype.md#initialize)。  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 TRUE。  
  
### <a name="remarks"></a>备注  
 此类不会进行任意初始化`Initialize`。  
  
##  <a name="requesttype"></a>CNonStatelessWorker::RequestType  
 实现[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>备注  
 此类处理类用于具有相同类型的工作项*工作人员*模板参数。 请参阅[CNonStatelessWorker 概述](../../atl/reference/cnonstatelessworker-class.md)有关的详细信息。  
  
##  <a name="terminate"></a>CNonStatelessWorker::Terminate  
 实现[WorkerArchetype::Terminate](worker-archetype.md#terminate)。  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>备注  
 此类不执行任何清理操作`Terminate`。  
  
## <a name="see-also"></a>另请参阅  
 [CThreadPool 类](../../atl/reference/cthreadpool-class.md)   
 [辅助原型](../../atl/reference/worker-archetype.md)   
 [类](../../atl/reference/atl-classes.md)

