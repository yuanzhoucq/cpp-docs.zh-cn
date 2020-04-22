---
title: Worker Archetype
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: c9ed9b30b94a8debe133bc213c12063750bfb15a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747343"
---
# <a name="worker-archetype"></a>Worker Archetype

符合*辅助角色*原型的类提供处理线程池上排队的工作项的代码。

**实现**

要实现符合此原型的类，类必须提供以下功能：

|方法|说明|
|------------|-----------------|
|[Initialize](#initialize)|调用 以在将任何请求传递到[执行](#execute)之前初始化辅助角色对象。|
|[执行](#execute)|调用以处理工作项。|
|[终止](#terminate)|调用 以在将所有请求传递到[执行](#execute)后取消初始化辅助角色对象。|

|Typedef|说明|
|-------------|-----------------|
|[RequestType](#requesttype)|工兵类可以处理的工作项类型的类型类型。|

典型的*工人*类如下所示：

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**现有实现**

这些类符合此原型：

|类|说明|
|-----------|-----------------|
|[无状态工人](../../atl/reference/cnonstatelessworker-class.md)|从线程池接收请求，并将它们传递到为每个请求创建和销毁的工作对象。|

**使用**

这些模板参数期望类符合此原型：

|参数名称|使用者|
|--------------------|-------------|
|*工人*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*工人*|[无状态工人](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="workerarchetypeexecute"></a><a name="execute"></a>辅助类型：执行

调用以处理工作项。

```cpp
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>参数

*请求*<br/>
要处理的工作项。 工作项的类型与`RequestType`相同。

*pvWorkerParam*<br/>
辅助角色类理解的自定义参数。 也传递到`WorkerArchetype::Initialize`和`Terminate`。

*p重叠*<br/>
指向[OVERLAPPED 结构](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)的指针，用于创建工作项排队的队列。

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a>工人Arche类型：：初始化

调用 以在将任何请求传递到`WorkerArchetype::Execute`之前初始化辅助角色对象。

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>参数

*pvParam*<br/>
辅助角色类理解的自定义参数。 也传递到`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a>辅助类型：请求类型

工兵类可以处理的工作项类型的类型类型。

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>备注

此类型必须用作 的第一个参数，`WorkerArchetype::Execute`并且必须能够强制转换到和从ULONG_PTR。

## <a name="workerarchetypeterminate"></a><a name="terminate"></a>工人类：终止

调用 以在将所有请求传递到`WorkerArchetype::Execute`后取消初始化辅助角色对象。

```cpp
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>参数

*pvParam*<br/>
辅助角色类理解的自定义参数。 也传递到`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。

## <a name="see-also"></a>请参阅

[概念](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
