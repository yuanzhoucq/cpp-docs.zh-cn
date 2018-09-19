---
title: 连接点类 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 490084ef16afb1f00f05bea07f95d13209661343
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024342"
---
# <a name="connection-points-classes"></a>连接点类

以下类提供支持的连接点：

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)实现连接点容器。

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)实现连接点。

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)实现连接点表示[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)接口。

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理不受限制的连接点和其接收器之间的连接。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理固定的数量的连接点和其接收器之间的连接。

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知客户端的接收器对象的属性已更改或将要更改。

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md)连接点的 ATL COM 对象提供支持。 与 COM 对象提供事件接收器映射进行了映射这些连接点。

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)结合使用事件接收器映射事件路由到相应的处理程序函数在类中。

## <a name="related-articles"></a>相关文章

[连接点](../atl/atl-connection-points.md)

[事件处理和 ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)<br/>
[连接点宏](../atl/reference/connection-point-macros.md)<br/>
[连接点全局函数](../atl/reference/connection-point-global-functions.md)

