---
title: "ATL Connection Point Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 连接点"
  - "CComDynamicUnkArray class, connection point classes"
  - "CComUnkArray class, connection point classes"
  - "CFirePropNotifyEvent class"
  - "CFirePropNotifyEvent class, connection point classes"
  - "连接点 [C++], ATL 类"
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Connection Point Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL使用以下选件类支持连接点:  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 实现连接点。  它表示输出接口的IID将作为模板参数。  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) 实现连接点容器和管理 `IConnectionPointImpl` 对象的列表。  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) 实现连接点表示 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) 接口。  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) 管理之间的任意连接连接点及其接收器。  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) 管理连接的预定义的数字为指定的模板参数。  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) 通知客户端接收器的对象的属性已更改或将发生更改。  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 提供支持ATL COM对象连接点。  这些连接点映射与事件接收器映射，您的COM对象提供。  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 与您的选件类的事件接收器映射一起使用路由事件到适当的处理程序函数。  
  
## 请参阅  
 [连接点](../atl/atl-connection-points.md)