---
title: ATL 连接点类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 289ff7ae7db1abd6a0a19577a2c567b462a2910e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201395"
---
# <a name="atl-connection-point-classes"></a>ATL 连接点类
ATL 使用下面的类以支持连接点：  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)实现连接点。 作为模板参数传递它所代表的输出接口的 IID。  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md)实现连接点容器，并管理的列表`IConnectionPointImpl`对象。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md)实现连接点表示[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)接口。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md)管理任意数量的连接点和其接收器之间的连接。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md)管理预定义的模板参数指定的连接数。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md)通知客户端的接收器对象的属性已更改或将要更改。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md)连接点的 ATL COM 对象提供支持。 与 COM 对象提供事件接收器映射进行了映射这些连接点。  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)与事件路由到相应的处理程序函数在类中的事件接收器映射一起工作。  
  
## <a name="see-also"></a>请参阅  
 [连接点](../atl/atl-connection-points.md)

