---
title: IUMSUnblockNotification 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63dcd78af0804a6921d34a35611591f044c2633f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438023"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 结构

表示来自资源管理器的通知，说明阻止并触发返回到计划程序的指定计划上下文的线程代理已解除阻止，并已准备好进行计划。 一旦重新计划该线程代理的关联执行上下文（从 `GetContext` 方法返回），此接口将变得无效。

## <a name="syntax"></a>语法

```
struct IUMSUnblockNotification;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|返回`IExecutionContext`与已解除阻止该线程代理关联的执行上下文的接口。 此方法返回，并通过调用已重新计划基础的执行上下文后`IThreadProxy::SwitchTo`方法，此接口将不再有效。|
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|返回下一步`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUMSUnblockNotification`

## <a name="requirements"></a>要求

**标头：** concrtrm.h

**命名空间：** 并发

##  <a name="getcontext"></a>  Iumsunblocknotification:: Getcontext 方法

返回`IExecutionContext`与已解除阻止该线程代理关联的执行上下文的接口。 此方法返回，并通过调用已重新计划基础的执行上下文后`IThreadProxy::SwitchTo`方法，此接口将不再有效。

```
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>返回值

`IExecutionContext`已解除阻止的线程代理的执行上下文的接口。

##  <a name="getnextunblocknotification"></a>  Iumsunblocknotification:: Getnextunblocknotification 方法

返回下一步`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。

```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>返回值

下一步`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)<br/>
[IUMSCompletionList 结构](iumscompletionlist-structure.md)
