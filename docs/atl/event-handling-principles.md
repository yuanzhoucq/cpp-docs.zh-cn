---
title: 事件处理原则 （ATL）
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 2e810853e7c81f279039e0b3dfda5199d38deee2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319570"
---
# <a name="event-handling-principles"></a>事件处理原则

所有事件处理共有三个步骤。 您需要：

- 在对象上实现事件接口。

- 建议对象要接收事件的事件源。

- 当对象不再需要接收事件时，取消通知事件源。

实现事件接口的方式将取决于其类型。 事件接口可以是可 v 可的、双接口的，也可以是接口。 由事件源的设计器来定义接口;由您来实现该接口。

> [!NOTE]
> 尽管事件接口不能是双重的，但是有许多良好的设计原因可以避免使用双重。 但是，这是事件*源*的设计者/实现者做出的决定。 由于您从事件`sink`的角度工作，您需要允许除了实现双事件接口外可能别无选择。 有关双接口的详细信息，请参阅[双接口和 ATL](../atl/dual-interfaces-and-atl.md)。

建议事件源可以分为三个步骤：

- 查询[IConnectPoint 容器](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)的源对象。

- 调用[IConnectPoint 容器：查找连接点](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint)传递您感兴趣的事件接口的 IID。 如果成功，这将返回连接点对象上的[IConnectPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)接口。

- 呼叫[IConnectionPoint：：建议](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise)传递`IUnknown`事件接收器。 如果成功，这将返回表示连接`DWORD`的 Cookie。

成功注册了接收事件的兴趣后，将根据源对象触发的事件调用对象事件接口上的方法。 当您不再需要接收事件时，您可以通过[IConnectionPoint：：：：un建议](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)将 Cookie 传回连接点。 这将中断源和接收器之间的连接。

在处理事件时，请小心避免引用周期。

## <a name="see-also"></a>另请参阅

[事件处理](../atl/event-handling-and-atl.md)
