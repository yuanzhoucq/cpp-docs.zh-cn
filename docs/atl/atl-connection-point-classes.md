---
title: ATL 连接点类
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: 8644fc087d7f0a651724c40d2868e96c9b6ec96a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491824"
---
# <a name="atl-connection-point-classes"></a>ATL 连接点类

ATL 使用以下类支持连接点:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)实现连接点。 它表示的输出接口的 IID 作为模板参数传递。

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)实现连接点容器并管理`IConnectionPointImpl`对象列表。

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)实现表示[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)接口的连接点。

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理连接点与其接收器之间的任意数目的连接。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理模板参数指定的预定义连接数。

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知客户端的接收器, 对象的属性已更改或即将发生更改。

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md)为 ATL COM 对象的连接点提供支持。 这些连接点通过事件接收器映射进行映射, 该映射由您的 COM 对象提供。

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)与类中的事件接收器映射结合使用, 以将事件路由到适当的处理程序函数。

## <a name="see-also"></a>请参阅

[连接点](../atl/atl-connection-points.md)
