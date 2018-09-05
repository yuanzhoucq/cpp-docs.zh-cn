---
title: 事件处理原则 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9931e194236871b9d767805464928fd4e553015e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762868"
---
# <a name="event-handling-principles"></a>事件处理原则

有三个步骤普遍适用于所有事件处理。 你将需要：

- 在对象上实现事件接口。

- 建议您的对象想要接收事件的事件源。

- 当您的对象不再需要接收事件时，不建议事件源。

将实现事件接口的方式将取决于其类型。 事件接口可以是 vtable、 双重、 或调度接口。 这取决于事件源的设计器来定义接口;由你来实现该接口。

> [!NOTE]
>  虽然有事件接口不能为双没有技术原因，但有多种良好的设计原因，若要避免使用双接口。 但是，这是由设计器/事件的实施者所做的决策*源*。 由于您是从事件的角度来看`sink`，您需要以允许您可能不具有任何所选的可能性，但若要实现双事件接口。 双重接口的详细信息，请参阅[双重接口和 ATL](../atl/dual-interfaces-and-atl.md)。

通知事件源可以分解为三个步骤：

- 查询的源对象[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)。

- 调用[IConnectionPointContainer::FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint)传递的事件接口的 IID 感兴趣。 如果成功，这将返回[IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint)连接点对象上的接口。

- 调用[IConnectionPoint::Advise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-advise)传递`IUnknown`的事件接收器。 如果成功，这将返回`DWORD`表示连接 cookie。

一旦您已成功注册你有兴趣接收事件，将根据源对象触发的事件调用对象的事件接口上的方法。 当不再需要接收事件时，可以将 cookie 传递到的连接点通过[iconnectionpoint::](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)。 这将中断源和接收器之间的连接。

小心地避免引用时处理事件周期。

## <a name="see-also"></a>请参阅

[事件处理](../atl/event-handling-and-atl.md)

