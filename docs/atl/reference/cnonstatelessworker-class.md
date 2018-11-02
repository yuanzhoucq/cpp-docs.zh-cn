---
title: CNonStatelessWorker 类
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: 7aaae3728113cfd91c0655d2eac445cdd4b34246
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619617"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker 类

从线程池中接收请求并将它们传递到创建和销毁的工作对象上每个请求。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>参数

*辅助角色*<br/>
辅助角色线程类符合[辅助原型](../../atl/reference/worker-archetype.md)合适上处理的请求排队[CThreadPool](../../atl/reference/cthreadpool-class.md)。

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

此类是用于简单的工作线程[CThreadPool](../../atl/reference/cthreadpool-class.md)。 此类不提供其自己的任何请求处理功能。 相反，它实例化的一个实例*辅助*每个请求，并委托给该实例及其方法的实现。

此类的好处是，它提供了方便地更改现有辅助角色线程类的状态模型。 `CThreadPool` 将线程的生存期内创建单个辅助角色以便如果辅助类保存状态，它将多个请求间保存它。 进行简单包装即可在该类`CNonStatelessWorker`然后再将它与模板`CThreadPool`、 辅助角色和它所持有仅限于单个请求的状态的生存期。

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

此方法创建的实例*辅助角色*上的堆栈和调用类[初始化](worker-archetype.md#initialize)对该对象。 如果初始化成功，此方法还会调用[Execute](worker-archetype.md#execute)并[终止](worker-archetype.md#terminate)对同一对象。

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

实现[WorkerArchetype::Initialize](worker-archetype.md#initialize)。

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

此类不会进行任意初始化`Initialize`。

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

实现[WorkerArchetype::RequestType](worker-archetype.md#requesttype)。

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>备注

此类处理相同类型的工作项作为用于类*辅助*模板参数。 请参阅[CNonStatelessWorker 概述](../../atl/reference/cnonstatelessworker-class.md)有关详细信息。

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

实现[WorkerArchetype::Terminate](worker-archetype.md#terminate)。

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>备注

此类不执行任何清理操作`Terminate`。

## <a name="see-also"></a>请参阅

[CThreadPool 类](../../atl/reference/cthreadpool-class.md)<br/>
[Worker Archetype](../../atl/reference/worker-archetype.md)<br/>
[类](../../atl/reference/atl-classes.md)
