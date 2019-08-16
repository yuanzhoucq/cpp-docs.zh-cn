---
title: 事件处理原则 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 066c8db60afed31ceba1c9ef6f4a10d5f842e608
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492144"
---
# <a name="event-handling-principles"></a>事件处理原则

所有事件处理都共有三个步骤。 你将需要:

- 在对象上实现事件接口。

- 建议你的对象要接收事件的事件源。

- 当对象不再需要接收事件时, Unadvise 事件源。

实现事件接口的方式将取决于其类型。 事件接口可以是 vtable、双重或调度接口。 它由事件源的设计器来定义接口;实现该接口是由您来实现的。

> [!NOTE]
>  尽管事件接口不能是双重的技术原因, 但有很多合理的设计原因可以避免使用 duals。 但是, 这是由事件*源*的设计器/实施者决定的。 由于从事件`sink`的角度来看, 您需要考虑到可能不会有任何选择来实现双重事件接口。 有关双重接口的详细信息, 请参阅[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)。

通知事件源可以分为三个步骤:

- 查询[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)的源对象。

- 调用[IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint)传递感兴趣的事件接口的 IID。 如果成功, 将返回连接点对象上的[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)接口。

- 调用[IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise)传递`IUnknown`事件接收器的。 如果成功, 将返回`DWORD`表示连接的 cookie。

成功注册接收事件的兴趣后, 将根据源对象触发的事件调用对象的事件接口中的方法。 当不再需要接收事件时, 可以通过[IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)将该 cookie 传递回连接点。 这会中断源和接收器之间的连接。

在处理事件时, 请注意避免引用循环。

## <a name="see-also"></a>请参阅

[事件处理](../atl/event-handling-and-atl.md)
