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
ms.openlocfilehash: f377d6079017266630434ce71602a7e70e58ae21
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282300"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 结构

工作计划程序的抽象的接口，该工作计划程序希望并发运行时的资源管理器向其传递用户模式计划 (UMS) 线程。 资源管理器使用此接口与 UMS 线程计划程序进行通信。 `IUMSScheduler` 接口继承自 `IScheduler` 接口。

## <a name="syntax"></a>语法

```
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|将分配`IUMSCompletionList`UMS 线程计划程序的接口。|

## <a name="remarks"></a>备注

如果要实现的自定义计划程序进行通信使用资源管理器中，并且你想要传递给你的计划程序而不是普通的 Win32 线程的 UMS 线程，则应提供的实现`IUMSScheduler`接口。 此外，应设置计划程序策略密钥的策略值`SchedulerKind`为`UmsThreadDefault`。 如果该策略都指定 UMS 线程`IScheduler`作为参数传递的接口[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法必须是`IUMSScheduler`接口。

资源管理器就能够处理 UMS 线程仅在具有 UMS 功能的操作系统上。 64 位版本 Windows 7 和更高版本操作系统的系统支持 UMS 线程。 如果您创建的计划程序策略`SchedulerKind`键设置为值`UmsThreadDefault`和基础平台不支持 UMS 的值`SchedulerKind`密钥对该策略将更改为值`ThreadScheduler`。 您应始终读回此策略值预期会收到 UMS 线程之前。

`IUMSScheduler`接口是一种计划程序和资源管理器之间的通信的双向通道的一端。 表示另一端`IResourceManager`和`ISchedulerProxy`接口，实现由资源管理器。

## <a name="inheritance-hierarchy"></a>继承层次结构

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>要求

**标头：** concrtrm.h

**命名空间：** 并发

##  <a name="setcompletionlist"></a>  Iumsscheduler:: Setcompletionlist 方法

将分配`IUMSCompletionList`UMS 线程计划程序的接口。

```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>参数

*pCompletionList*<br/>
计划程序完成列表接口。 没有每个计划程序的单个列表。

### <a name="remarks"></a>备注

资源管理器将调用此方法在指定计划程序已请求资源的初始分配后，其需要 UMS 线程计划程序上。 计划程序可以使用`IUMSCompletionList`接口，以确定当 UMS 线程代理已解除阻塞。 才有效，若要从分配给 UMS 调度程序的虚拟处理器根上运行的线程代理访问此接口。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler 结构](ischeduler-structure.md)<br/>
[IUMSCompletionList 结构](iumscompletionlist-structure.md)<br/>
[IResourceManager 结构](iresourcemanager-structure.md)
