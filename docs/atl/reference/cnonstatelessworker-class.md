---
title: CNonStatelessWorker 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de03ded4bc0021a8884f608d10368e3d09c11cf8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker 类
从线程池接收请求，并将它们传递到创建和销毁的辅助对象上每个请求。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class Worker>  
class CNonStatelessWorker
```  
  
#### <a name="parameters"></a>参数  
 *辅助进程*  
 符合的辅助线程类[辅助 archetype](../../atl/reference/worker-archetype.md)合适的处理请求上排队[CThreadPool](../../atl/reference/cthreadpool-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](#requesttype)|实现[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](#execute)|实现[WorkerArchetype::Execute](worker-archetype.md#execute)。|  
|[CNonStatelessWorker::Initialize](#initialize)|实现[WorkerArchetype::Initialize](worker-archetype.md#initialize)。|  
|[CNonStatelessWorker::Terminate](#terminate)|实现[WorkerArchetype::Terminate](worker-archetype.md#terminate)。|  
  
## <a name="remarks"></a>备注  
 此类是用于简单的工作线程[CThreadPool](../../atl/reference/cthreadpool-class.md)。 此类不提供自己的任何请求处理功能。 相反，它实例化的一个实例*辅助*每个请求，并委托到该实例其方法的实现。  
  
 此类的好处是，它提供了一种简便方式更改现有的辅助线程类的状态模型。 `CThreadPool` 将该线程的生存期内创建的单个辅助因此如果辅助类保存状态，它将跨多个请求保存它。 包装在该类`CNonStatelessWorker`再使用它与模板`CThreadPool`、 辅助角色和它包含仅限于单个请求的状态的生存期。  
  
## <a name="requirements"></a>要求  
 **标头：** atlutil.h  
  
##  <a name="execute"></a>  CNonStatelessWorker::Execute  
 实现[WorkerArchetype::Execute](worker-archetype.md#execute)。  

  
```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```  
  
### <a name="remarks"></a>备注  
 此方法创建的一个实例*辅助*类上的堆栈和调用[初始化](worker-archetype.md#initialize)对该对象。 如果初始化成功，此方法也会调用[执行](worker-archetype.md#execute)和[终止](worker-archetype.md#terminate)对同一对象。  

  
##  <a name="initialize"></a>  CNonStatelessWorker::Initialize  
 实现[WorkerArchetype::Initialize](worker-archetype.md#initialize)。  
  
```
BOOL Initialize(void* /* pvParam */) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 TRUE。  
  
### <a name="remarks"></a>备注  
 此类不会执行任何初始化操作`Initialize`。  
  
##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType  
 实现[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。  
  
```
typedef Worker::RequestType RequestType;
```  
  
### <a name="remarks"></a>备注  
 此类处理用于类具有相同类型的工作项*辅助*模板参数。 请参阅[CNonStatelessWorker 概述](../../atl/reference/cnonstatelessworker-class.md)有关详细信息。  
  
##  <a name="terminate"></a>  CNonStatelessWorker::Terminate  
 实现[WorkerArchetype::Terminate](worker-archetype.md#terminate)。  
  
```
void Terminate(void* /* pvParam */) throw();
```  
  
### <a name="remarks"></a>备注  
 此类不执行任何清理操作`Terminate`。  
  
## <a name="see-also"></a>请参阅  
 [CThreadPool 类](../../atl/reference/cthreadpool-class.md)   
 [辅助原型](../../atl/reference/worker-archetype.md)   
 [类](../../atl/reference/atl-classes.md)
