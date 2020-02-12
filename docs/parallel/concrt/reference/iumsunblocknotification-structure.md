---
title: IUMSUnblockNotification 结构
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: d4fd95b1f11ed6edac26cb03e41e8b650acfafa3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139974"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 结构

表示来自资源管理器的通知，说明阻止并触发返回到计划程序的指定计划上下文的线程代理已解除阻止，并已准备好进行计划。 一旦重新计划该线程代理的关联执行上下文（从 `GetContext` 方法返回），此接口将变得无效。

## <a name="syntax"></a>语法

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IUMSUnblockNotification：： GetContext](#getcontext)|返回与已解除阻止的线程代理关联的执行上下文的 `IExecutionContext` 接口。 此方法返回并且基础执行上下文已通过调用 `IThreadProxy::SwitchTo` 方法重新安排，此接口不再有效。|
|[IUMSUnblockNotification：： GetNextUnblockNotification](#getnextunblocknotification)|返回从方法 `IUMSCompletionList::GetUnblockNotifications`返回的链中的下一个 `IUMSUnblockNotification` 接口。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUMSUnblockNotification`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="getcontext"></a>IUMSUnblockNotification：： GetContext 方法

返回与已解除阻止的线程代理关联的执行上下文的 `IExecutionContext` 接口。 此方法返回并且基础执行上下文已通过调用 `IThreadProxy::SwitchTo` 方法重新安排，此接口不再有效。

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>返回值

用于执行上下文到已解除阻止的线程代理的 `IExecutionContext` 接口。

## <a name="getnextunblocknotification"></a>IUMSUnblockNotification：： GetNextUnblockNotification 方法

返回从方法 `IUMSCompletionList::GetUnblockNotifications`返回的链中的下一个 `IUMSUnblockNotification` 接口。

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>返回值

`IUMSCompletionList::GetUnblockNotifications`的方法返回的链中的下一个 `IUMSUnblockNotification` 接口。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)<br/>
[IUMSCompletionList 结构](iumscompletionlist-structure.md)
