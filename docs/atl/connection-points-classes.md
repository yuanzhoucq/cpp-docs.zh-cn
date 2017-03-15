---
title: "Connection Points Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.connection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 连接点"
  - "connection points classes"
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Connection Points Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面选件类提供支持连接点:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) 实现连接点容器。  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 实现连接点。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 实现连接点表示 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 接口。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) 管理之间的无限制的连接连接点及其接收器。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) 管理连接的内置的数字之间的联接和其接收器。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) 通知客户端接收器的对象的属性已更改或将发生更改。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 提供对支持ATL COM对象连接点。  这些连接点映射与事件接收器映射，您的COM对象提供。  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 与您的选件类的事件接收器映射一起使用路由事件到适当的处理程序函数。  
  
## 相关文章  
 [连接点](../atl/atl-connection-points.md)  
  
 [事件处理和ATL](../atl/event-handling-and-atl.md)  
  
## 请参阅  
 [Class Overview](../atl/atl-class-overview.md)   
 [Connection Point Macros](../atl/reference/connection-point-macros.md)   
 [Connection Point Global Functions](../atl/reference/connection-point-global-functions.md)