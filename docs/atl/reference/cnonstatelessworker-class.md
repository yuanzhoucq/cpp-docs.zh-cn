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
ms.openlocfilehash: 6264bb6bc9070b5ce170b294f9db0d371e7b6b71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747664"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker 类

从线程池接收请求，并将它们传递到在每个请求上创建和销毁的工作对象。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>参数

*工人*<br/>
符合工作[原型](../../atl/reference/worker-archetype.md)的工作线程类，适合处理在[CThreadPool](../../atl/reference/cthreadpool-class.md)上排队的请求。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[无状态工作人员：：请求类型](#requesttype)|[workerArche 类型的实现：请求类型](worker-archetype.md#requesttype)。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[无状态工作人员：执行](#execute)|[工作Arche类型的实现：执行](worker-archetype.md#execute)。|
|[无状态工作人员：初始化](#initialize)|[工作Arche类型的实现：初始化](worker-archetype.md#initialize)。|
|[无状态工作人员：：终止](#terminate)|[workerArche 类型的实现：终止](worker-archetype.md#terminate)。|

## <a name="remarks"></a>备注

此类是一个简单的工作线程，用于[CThreadPool。](../../atl/reference/cthreadpool-class.md) 此类不提供其自己的任何请求处理功能。 相反，它实例化每个请求的一个*Worker*实例，并将其方法的实现委托给该实例。

此类的好处是它提供了一种更改现有辅助线程类的状态模型的便捷方法。 `CThreadPool`将为线程的生存期创建单个辅助角色，因此，如果辅助角色类保持状态，它将跨多个请求保留该工作线程。 只需在`CNonStatelessWorker`模板中包装该类，即可使用`CThreadPool`，辅助角色的生存期及其保留状态仅限于单个请求。

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a>无状态工作人员：执行

[工作Arche类型的实现：执行](worker-archetype.md#execute)。

```cpp
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>备注

此方法在堆栈上创建*辅助角色*类的实例，并在该对象上调用[初始化](worker-archetype.md#initialize)。 如果初始化成功，此方法也会在同一对象上调用["执行](worker-archetype.md#execute)"和["终止](worker-archetype.md#terminate)"。

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a>无状态工作人员：初始化

[工作Arche类型的实现：初始化](worker-archetype.md#initialize)。

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>返回值

始终返回 TRUE。

### <a name="remarks"></a>备注

此类不会在 中`Initialize`执行任何初始化。

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a>无状态工作人员：：请求类型

[workerArche 类型的实现：请求类型](worker-archetype.md#requesttype)。

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>备注

此类处理的工作项类型与用于*辅助角色*模板参数的类相同。 有关详细信息，请参阅[无状态工作人员概述](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a>无状态工作人员：：终止

[workerArche 类型的实现：终止](worker-archetype.md#terminate)。

```cpp
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>备注

此类不会在 中`Terminate`进行任何清理。

## <a name="see-also"></a>请参阅

[CThreadPool 类](../../atl/reference/cthreadpool-class.md)<br/>
[Worker Archetype](../../atl/reference/worker-archetype.md)<br/>
[类](../../atl/reference/atl-classes.md)
