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
ms.openlocfilehash: 70954906122c048e5199a801632626d35a8e3f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368096"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 结构

工作计划程序的抽象的接口，该工作计划程序希望并发运行时的资源管理器向其传递用户模式计划 (UMS) 线程。 资源管理器使用此接口与 UMS 线程计划程序进行通信。 `IUMSScheduler` 接口继承自 `IScheduler` 接口。

## <a name="syntax"></a>语法

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IUMS计划：：设置完成列表](#setcompletionlist)|将`IUMSCompletionList`接口分配给 UMS 线程计划程序。|

## <a name="remarks"></a>备注

如果要实现与资源管理器通信的自定义计划程序，并且希望将 UMS 线程交给您的计划程序而不是普通的 Win32 线程，则应提供`IUMSScheduler`接口的实现。 此外，应将计划程序策略键`SchedulerKind`的策略值设置为`UmsThreadDefault`。 如果策略指定 UMS 线程，`IScheduler`则作为参数传递给[IResourceManager：：注册调度器](iresourcemanager-structure.md#registerscheduler)方法的接口必须是接口`IUMSScheduler`。

资源管理器只能将 UMS 线程交给具有 UMS 功能的操作系统。 64 位操作系统，版本 Windows 7 和更高版本支持 UMS 线程。 如果创建`SchedulerKind`具有键设置为`UmsThreadDefault`值的调度程序策略，而基础平台不支持 UMS，则该策略上的`SchedulerKind`键的值将更改为值`ThreadScheduler`。 在期望接收 UMS 线程之前，应始终读取此策略值。

该`IUMSScheduler`接口是调度程序与资源管理器之间双向通信通道的一端。 另一端由`IResourceManager`和`ISchedulerProxy`接口表示，这些接口由资源管理器实现。

## <a name="inheritance-hierarchy"></a>继承层次结构

[I时间](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>IUMS计划：：设置完成列表方法

将`IUMSCompletionList`接口分配给 UMS 线程计划程序。

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>参数

*p 完成列表*<br/>
计划程序的完成列表接口。 每个计划程序只有一个列表。

### <a name="remarks"></a>备注

在计划程序请求初始分配资源后，资源管理器将在指定所需的 UMS 线程的计划程序上调用此方法。 计划程序可以使用接口`IUMSCompletionList`来确定 UMS 线程代理何时未解除阻止。 仅从分配给 UMS 计划程序的虚拟处理器根上运行的线程代理访问此接口才有效。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[策略元素键](concurrency-namespace-enums.md)<br/>
[IScheduler 结构](ischeduler-structure.md)<br/>
[IUMSCompletionList 结构](iumscompletionlist-structure.md)<br/>
[IResourceManager 结构](iresourcemanager-structure.md)
