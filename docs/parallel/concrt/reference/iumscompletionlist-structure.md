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
ms.openlocfilehash: c388cc98aedbd35b2d0e00a4653a85a47abcb838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368124"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 结构

表示 UMS 完成列表。 UMS 线程阻止时，将分派计划程序的指定计划上下文，以便决定原始线程被阻止时，在基础虚拟处理器根上计划哪些内容。 如果原始线程解除阻止，则操作系统将它排队到完成列表，该列表可以通过此接口访问。 计划程序可以在指定计划上下文中或其搜索工作的任何其他位置查询完成列表。

## <a name="syntax"></a>语法

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IUMS 完成列表：：获取取消阻止通知](#getunblocknotifications)|检索表示执行上下文的`IUMSUnblockNotification`接口链，自上次调用此方法以来，其关联的线程代理已解除阻止。|

## <a name="remarks"></a>备注

计划程序必须格外小心，利用此接口从完成列表中取消项目排队后执行哪些操作。 这些项目应放在计划程序的可运行上下文列表中，并且通常可以尽快访问。 完全有可能，其中一个取消排队的项目已被授予任意锁的所有权。 计划程序不能进行任意的函数调用，这些调用在取消排队项的调用和这些项放置在通常可以从计划程序内访问的列表中之间。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUMSCompletionList`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>IUMS 完成列表：：获取取消阻止通知方法

检索表示执行上下文的`IUMSUnblockNotification`接口链，自上次调用此方法以来，其关联的线程代理已解除阻止。

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>返回值

接口链`IUMSUnblockNotification`。

### <a name="remarks"></a>备注

重新计划执行上下文后，返回的通知将无效。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification 结构](iumsunblocknotification-structure.md)
