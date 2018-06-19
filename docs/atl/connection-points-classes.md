---
title: 连接点类 (ATL) |Microsoft 文档
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
ms.openlocfilehash: 8c0d75c101bb23b3e7b788e607e325c18d729c81
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355074"
---
# <a name="connection-points-classes"></a>连接点类
下面的类为连接点提供支持：  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)实现连接点容器。  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)实现连接点。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)实现连接点表示[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638)接口。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理连接点和其的接收器间不受限制的连接。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理固定的数量的连接点和其的接收器间的连接。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知客户端的接收器对象的属性已更改或即将更改。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md)为连接点的 ATL COM 对象提供支持。 这些连接点使用事件接收器映射，提供你的 COM 对象的映射。  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)结合使用事件接收器映射中你将事件路由到适当的处理程序函数的类。  
  
## <a name="related-articles"></a>相关文章  
 [连接点](../atl/atl-connection-points.md)  
  
 [事件处理和 ATL](../atl/event-handling-and-atl.md)  
  
## <a name="see-also"></a>请参阅  
 [类概述](../atl/atl-class-overview.md)   
 [连接点宏](../atl/reference/connection-point-macros.md)   
 [连接点全局函数](../atl/reference/connection-point-global-functions.md)

