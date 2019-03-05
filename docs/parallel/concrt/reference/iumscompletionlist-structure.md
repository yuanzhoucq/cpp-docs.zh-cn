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
ms.openlocfilehash: 567b8668934d81c49757660d1a60ca74eb033e68
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273903"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 结构

表示 UMS 完成列表。 UMS 线程阻止时，将分派计划程序的指定计划上下文，以便决定原始线程被阻止时，在基础虚拟处理器根上计划哪些内容。 如果原始线程解除阻止，则操作系统将它排队到完成列表，该列表可以通过此接口访问。 计划程序可以在指定计划上下文中或其搜索工作的任何其他位置查询完成列表。

## <a name="syntax"></a>语法

```
struct IUMSCompletionList;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|检索的链`IUMSUnblockNotification`表示其关联的线程代理已解除阻塞，因为上一次此方法调用的执行上下文的接口。|

## <a name="remarks"></a>备注

计划程序必须格外小心使用此接口可从完成列表项的取消排队后要执行的操作。 项应放置在可运行的上下文的计划程序的列表，并尽可能快地进行常规访问。 它是完全有可能取消排队项之一已被授予任意锁的所有权。 计划程序可以调用取消排队项和一个列表，其中可以通常从内部进行访问计划程序上的这些项的位置之间可能会阻止任何任意函数调用。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUMSCompletionList`

## <a name="requirements"></a>要求

**标头：** concrtrm.h

**命名空间：** 并发

##  <a name="getunblocknotifications"></a>  Iumscompletionlist:: Getunblocknotifications 方法

检索的链`IUMSUnblockNotification`表示其关联的线程代理已解除阻塞，因为上一次此方法调用的执行上下文的接口。

```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>返回值

链`IUMSUnblockNotification`接口。

### <a name="remarks"></a>备注

一旦重新计划任务的执行上下文返回的通知无效。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[IUMSScheduler 结构](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification 结构](iumsunblocknotification-structure.md)
