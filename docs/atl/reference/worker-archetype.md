---
title: 工作原型
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 3efd77c38508df8302fa4e1dd5c9b51f66cd5e43
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915450"
---
# <a name="worker-archetype"></a>工作原型

符合*辅助*原型的类提供用于处理线程池上排队的工作项的代码。

**实现**

若要实现符合此原型的类, 类必须提供以下功能:

|方法|描述|
|------------|-----------------|
|[Initialize](#initialize)|调用以初始化辅助对象, 然后将请求传递给[执行](#execute)。|
|[Execute](#execute)|调用以处理工作项。|
|[Terminate](#terminate)|调用以在所有请求都传递到[执行](#execute)之后对工作对象进行初始化。|

|Typedef|描述|
|-------------|-----------------|
|[RequestType](#requesttype)|可由 worker 类处理的工作项类型的 typedef。|

典型的*辅助角色*类如下所示:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**现有实现**

这些类符合以下原型:

|类|描述|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|接收来自线程池的请求, 并将其传递给为每个请求创建并销毁的辅助角色对象。|

**用法**

这些模板参数需要类符合以下原型:

|参数名称|通过者|
|--------------------|-------------|
|*工人*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*工人*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>要求

**标头:** atlutil

## <a name="execute"></a>WorkerArchetype::Execute

调用以处理工作项。

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>参数

*request*<br/>
要处理的工作项。 工作项的类型`RequestType`与相同。

*pvWorkerParam*<br/>
辅助类理解的自定义参数。 也传递给`WorkerArchetype::Initialize`和`Terminate`。

*pOverlapped*<br/>
指向用于创建在其上排队工作项的队列的[重叠](/windows/desktop/api/minwinbase/ns-minwinbase-overlapped)结构的指针。

## <a name="initialize"></a>WorkerArchetype:: Initialize

调用以在将任何请求传递到`WorkerArchetype::Execute`之前初始化辅助对象。
```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>参数

*pvParam*<br/>
辅助类理解的自定义参数。 也传递给`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE, 否则返回 FALSE。

## <a name="requesttype"></a>WorkerArchetype:: RequestType

可由 worker 类处理的工作项类型的 typedef。

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>备注

此类型必须用作的第一个参数`WorkerArchetype::Execute` , 并且必须能够在 ULONG_PTR 中进行转换。

## <a name="terminate"></a>WorkerArchetype:: Terminate

调用以在所有请求都被传递到`WorkerArchetype::Execute`后对工作对象进行初始化。

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>参数

*pvParam*<br/>
辅助类理解的自定义参数。 也传递给`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。

## <a name="see-also"></a>请参阅

[概念](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
