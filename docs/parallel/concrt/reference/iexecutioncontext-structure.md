---
title: IExecutionContext 结构
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 532247ca1776452ad32476d2bcdfafcee3481058
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358794"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 结构

可以在给定虚拟处理器上运行并可以协作切换上下文的执行上下文的接口。

## <a name="syntax"></a>语法

```cpp
struct IExecutionContext;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I 执行上下文：:D](#dispatch)|线程代理开始执行特定执行上下文时调用的方法。 这应该是计划程序的主要工作例程。|
|[I 执行上下文：GetId](#getid)|返回执行上下文的唯一标识符。|
|[I 执行上下文：获取代理](#getproxy)|返回执行此上下文的线程代理的接口。|
|[I 执行上下文：获取计划](#getscheduler)|将接口返回此执行上下文所属的计划程序。|
|[I 执行上下文：：设置代理](#setproxy)|将线程代理与此执行上下文关联。 关联的线程代理在开始执行上下文`Dispatch`的方法之前调用此方法。|

## <a name="remarks"></a>备注

如果要实现与并发运行时的资源管理器接口的自定义计划程序，则需要实现该`IExecutionContext`接口。 资源管理器创建的线程通过执行`IExecutionContext::Dispatch`方法代表计划程序执行工作。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IExecutionContext`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a>I 执行上下文：:Dispatch 方法

线程代理开始执行特定执行上下文时调用的方法。 这应该是计划程序的主要工作例程。

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>参数

*p调度状态*<br/>
指向调度此执行上下文的状态的指针。 有关调度状态的详细信息，请参阅[调度状态](dispatchstate-structure.md)。

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a>I 执行上下文：getId 方法

返回执行上下文的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

唯一的整数标识符。

### <a name="remarks"></a>备注

在使用接口作为资源管理器`GetExecutionContextId`提供的方法的参数之前，应使用 方法为`IExecutionContext`实现接口的对象获取唯一标识符。 调用`GetId`函数时，应返回相同的标识符。

从其他源获取的标识符可能会导致未定义的行为。

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>I 执行上下文：获取代理方法

返回执行此上下文的线程代理的接口。

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>返回值

一个 `IThreadProxy` 接口。 如果执行上下文的线程代理未用 调用`SetProxy`初始化 ，则函数必须返回`NULL`。

### <a name="remarks"></a>备注

资源管理器将在执行上下文中调用`SetProxy`该方法，在上下文中输入`IThreadProxy``Dispatch`方法之前，将接口作为参数。 应存储此参数并在调用 时将其返回到`GetProxy()`。

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>I 执行上下文：：获取计划程序方法

将接口返回此执行上下文所属的计划程序。

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>返回值

一个 `IScheduler` 接口。

### <a name="remarks"></a>备注

在将执行上下文用作资源管理器提供的方法的参数之前，`IScheduler`您需要使用有效的接口初始化执行上下文。

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>I 执行上下文：：设置代理方法

将线程代理与此执行上下文关联。 关联的线程代理在开始执行上下文`Dispatch`的方法之前调用此方法。

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>参数

*pThreadProxy*<br/>
即将在此执行上下文中输入方法的`Dispatch`线程代理的接口。

### <a name="remarks"></a>备注

应保存参数`pThreadProxy`并在调用`GetProxy`方法时将其返回。 资源管理器保证与执行上下文关联的线程代理在线程代理执行`Dispatch`该方法时不会更改。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[IScheduler 结构](ischeduler-structure.md)<br/>
[IThreadProxy 结构](ithreadproxy-structure.md)
