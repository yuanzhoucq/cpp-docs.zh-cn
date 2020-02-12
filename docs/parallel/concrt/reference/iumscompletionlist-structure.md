---
title: IUMSCompletionList 结构
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: 02382ef4606a6e73804fcbd5ce7735ecf2f0dcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140038"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 结构

表示 UMS 完成列表。 UMS 线程阻止时，将分派计划程序的指定计划上下文，以便决定原始线程被阻止时，在基础虚拟处理器根上计划哪些内容。 如果原始线程解除阻止，则操作系统将它排队到完成列表，该列表可以通过此接口访问。 计划程序可以在指定计划上下文中或其搜索工作的任何其他位置查询完成列表。

## <a name="syntax"></a>语法

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IUMSCompletionList：： GetUnblockNotifications](#getunblocknotifications)|检索一个 `IUMSUnblockNotification` 接口链，该链表示自上次调用此方法以来关联的线程代理已取消阻止的执行上下文。|

## <a name="remarks"></a>备注

计划程序必须特别注意使用此接口对完成列表中的项取消排队后，执行了哪些操作。 应将这些项放在可运行上下文的计划程序列表中，并尽快进行访问。 完全有可能为某个取消排队的项授予了任意锁的所有权。 计划程序可以不执行任何函数调用，它们可能会在对出列项的调用和列表中放置这些项的位置之间进行阻止，通常可以从计划程序内访问这些项。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUMSCompletionList`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="getunblocknotifications"></a>IUMSCompletionList：： GetUnblockNotifications 方法

检索一个 `IUMSUnblockNotification` 接口链，该链表示自上次调用此方法以来关联的线程代理已取消阻止的执行上下文。

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>返回值

`IUMSUnblockNotification` 接口的链。

### <a name="remarks"></a>备注

重新计划执行上下文后，返回的通知无效。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification 结构](iumsunblocknotification-structure.md)
