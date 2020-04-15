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
ms.openlocfilehash: 0b88ddd4184e982a5e07c536efc301eaa16f4a41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368062"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 结构

表示来自资源管理器的通知，说明阻止并触发返回到计划程序的指定计划上下文的线程代理已解除阻止，并已准备好进行计划。 一旦重新计划该线程代理的关联执行上下文（从 `GetContext` 方法返回），此接口将变得无效。

## <a name="syntax"></a>语法

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IUMUnSunblock 通知：：获取上下文](#getcontext)|返回与`IExecutionContext`已解除阻止的线程代理关联的执行上下文的接口。 一旦此方法返回，并且通过调用 方法`IThreadProxy::SwitchTo`重新计划基础执行上下文，此接口将不再有效。|
|[IUMUnSunblock 通知：：获取下一个取消阻止通知](#getnextunblocknotification)|返回从`IUMSUnblockNotification`方法`IUMSCompletionList::GetUnblockNotifications`返回的链中的下一个接口。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUMSUnblockNotification`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>IUMUnSunblock 通知：：获取上下文方法

返回与`IExecutionContext`已解除阻止的线程代理关联的执行上下文的接口。 一旦此方法返回，并且通过调用 方法`IThreadProxy::SwitchTo`重新计划基础执行上下文，此接口将不再有效。

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>返回值

执行`IExecutionContext`上下文的接口，用于已解除阻止的线程代理。

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>IUMUnSunblock 通知：：获取NextUnblock通知方法

返回从`IUMSUnblockNotification`方法`IUMSCompletionList::GetUnblockNotifications`返回的链中的下一个接口。

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>返回值

链中的`IUMSUnblockNotification`下一个接口从 方法`IUMSCompletionList::GetUnblockNotifications`返回。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)<br/>
[IUMSCompletionList 结构](iumscompletionlist-structure.md)
