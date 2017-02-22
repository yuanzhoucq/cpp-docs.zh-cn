---
title: "事件接收器映射 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件接收器映射"
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 事件接收器映射
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当嵌入的 OLE 控件激发事件时，使用机制控件的容器接收事件，名为“事件接收器”映射，提供由 MFC。  此事件接收器映射指定每个特定事件的事件处理程序，以及这些函数参数相同。  有关事件接收器的更多信息，请参见知识库文章 [ActiveX 控件容器](../../mfc/activex-control-containers.md)。  
  
### 事件接收器映射  
  
|||  
|-|-|  
|[BEGIN\_EVENTSINK\_MAP](../Topic/BEGIN_EVENTSINK_MAP.md)|启动事件接收器的定义。|  
|[DECLARE\_EVENTSINK\_MAP](../Topic/DECLARE_EVENTSINK_MAP.md)|声明事件接收器映射|  
|[END\_EVENTSINK\_MAP](../Topic/END_EVENTSINK_MAP.md)|关闭事件接收器的定义。|  
|[ON\_EVENT](../Topic/ON_EVENT.md)|定义特定事件的事件处理程序。|  
|[ON\_EVENT\_RANGE](../Topic/ON_EVENT_RANGE.md)|从其OLE 控件集合定义一组特定事件的事件处理程序。|  
|[ON\_EVENT\_REFLECT](../Topic/ON_EVENT_REFLECT.md)|在控件的容器之前，处理接收控件激发的事件。|  
|[ON\_PROPNOTIFY](../Topic/ON_PROPNOTIFY.md)|从一个 OLE 控件定义处理的属性通知处理程序。|  
|[ON\_PROPNOTIFY\_RANGE](../Topic/ON_PROPNOTIFY_RANGE.md)|从一组数 OLE 控件定义处理的属性通知的处理程序。|  
|[ON\_PROPNOTIFY\_REFLECT](../Topic/ON_PROPNOTIFY_REFLECT.md)|在控件的容器之前，会收到该控件发送通知的属性。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)