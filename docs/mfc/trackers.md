---
title: "跟踪器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [OLE], 跟踪器"
  - "CDC 类, 跟踪器"
  - "CRectTracker 类, 实现跟踪器"
  - "OLE 应用程序 [C++], 跟踪器"
  - "OLE 容器, 跟踪器"
  - "OLE 服务器应用程序, 跟踪器"
  - "跟踪器"
  - "跟踪 OLE 项"
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 跟踪器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[种 CRectTracker](../mfc/reference/crecttracker-class.md) 矩形项类提供在应用程序和用户之间的一个用户界面。提供各种各样的显示样式。  这些包含固定样式，阴影的或飞奔的边界；包含项的阴影的模式；对外部可以位于内或边框的大小调整柄。  TRACKER 与 OLE 项，即，从 `COleClientItem`派生对象一起用于的。  TRACKER 矩形只对项的当前状态的可视提示。  
  
 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md) 演示通用接口使用客户从 TRACKER 和 OLE 项容器应用程序的视图。  TRACKER 对于的不同样式和功能的演示对象中，请参见 MFC 泛型示例 [TRACKER](../top/visual-cpp-samples.md)。  
  
 有关实现 OLE 的跟踪器应用程序的更多信息，请参见 [TRACKER:实现 OLE 的跟踪器应用程序](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem Class](../mfc/reference/coleclientitem-class.md)