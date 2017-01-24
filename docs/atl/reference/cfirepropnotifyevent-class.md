---
title: "CFirePropNotifyEvent Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFirePropNotifyEvent"
  - "ATL::CFirePropNotifyEvent"
  - "ATL.CFirePropNotifyEvent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFirePropNotifyEvent class"
  - "连接点 [C++], notifying of events"
  - "sinks, notifying of ATL events"
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFirePropNotifyEvent Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于通知控件属性的更改容器的接收器的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CFirePropNotifyEvent  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFirePropNotifyEvent::FireOnChanged](../Topic/CFirePropNotifyEvent::FireOnChanged.md)|（静态）通知容器接收器的控件属性已更改。|  
|[CFirePropNotifyEvent::FireOnRequestEdit](../Topic/CFirePropNotifyEvent::FireOnRequestEdit.md)|（静态）通知容器接收器的控件属性将更改。|  
  
## 备注  
 `CFirePropNotifyEvent` 有通知容器的接收器的两个方法控件属性已更改或将发生更改。  
  
 如果实现控件的选件类从 `IPropertyNotifySink`派生，`CFirePropNotifyEvent` 调用方法，在调用 `FireOnRequestEdit` 或 `FireOnChanged`时。  如果控件选件类从 `IPropertyNotifySink`未派生，对这些函数返回 `S_OK`。  
  
 有关创建控件的更多信息，请参见 [ATL教程](../../atl/active-template-library-atl-tutorial.md)。  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)