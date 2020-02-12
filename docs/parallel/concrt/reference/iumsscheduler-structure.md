---
title: IUMSScheduler 结构
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 45df744a9850510006e4bf887c8ed61b000a8e5c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139998"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 结构

工作计划程序的抽象的接口，该工作计划程序希望并发运行时的资源管理器向其传递用户模式计划 (UMS) 线程。 资源管理器使用此接口与 UMS 线程计划程序进行通信。 `IUMSScheduler` 接口继承自 `IScheduler` 接口。

## <a name="syntax"></a>语法

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IUMSScheduler：： SetCompletionList](#setcompletionlist)|向 UMS 线程计划程序分配 `IUMSCompletionList` 接口。|

## <a name="remarks"></a>备注

如果要实现与资源管理器进行通信的自定义计划程序，并且希望将 UMS 线程传递到计划程序而不是普通 Win32 线程，则应提供 `IUMSScheduler` 接口的实现。 此外，应将计划程序策略密钥 `SchedulerKind` 的策略值设置为 `UmsThreadDefault`。 如果策略指定 UMS 线程，则作为参数传递给[IResourceManager：： RegisterScheduler](iresourcemanager-structure.md#registerscheduler)方法的 `IScheduler` 接口必须是 `IUMSScheduler` 接口。

资源管理器只能在具有 UMS 功能的操作系统上手动使用 UMS 线程。 Windows 7 和更高版本支持 UMS 线程的64位操作系统。 如果创建的计划程序策略将 `SchedulerKind` 的键设置为该值 `UmsThreadDefault` 并且基础平台不支持 UMS，则该策略上的 `SchedulerKind` 键的值将更改为 `ThreadScheduler`值。 应始终在预期接收 UMS 线程之前读回此策略值。

`IUMSScheduler` 接口是计划程序与资源管理器之间的双向通信通道的一端。 另一端由资源管理器实现的 `IResourceManager` 和 `ISchedulerProxy` 接口表示。

## <a name="inheritance-hierarchy"></a>继承层次结构

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="setcompletionlist"></a>IUMSScheduler：： SetCompletionList 方法

向 UMS 线程计划程序分配 `IUMSCompletionList` 接口。

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>参数

*pCompletionList*<br/>
计划程序的完成列表接口。 每个计划程序都有一个列表。

### <a name="remarks"></a>备注

在计划程序请求初始资源分配后，资源管理器将在指定它需要 UMS 线程的计划程序上调用此方法。 计划程序可以使用 `IUMSCompletionList` 接口来确定 UMS 线程代理何时解除阻止。 只有从分配给 UMS 计划程序的虚拟处理器根上运行的线程代理访问此接口才有效。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler 结构](ischeduler-structure.md)<br/>
[IUMSCompletionList 结构](iumscompletionlist-structure.md)<br/>
[IResourceManager 结构](iresourcemanager-structure.md)
