---
title: "橡皮筋和跟踪器 | Microsoft Docs"
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
  - "CRectTracker 类, 实现跟踪器"
  - "OLE 对象, 选择"
  - "橡皮筋"
  - "跟踪器"
  - "WM_LBUTTONDOWN"
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 橡皮筋和跟踪器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其他功能提供追踪器是“橡皮筋”的选择，允许用户通过拖动尺寸矩形选择多种 OLE 项在要选择的项附近。  用户松开鼠标左键后，在用户选定区域中选择项并可由用户操作。  例如，用户可以选择拖动到另一个容器应用程序。  
  
 在应用程序 `WM_LBUTTONDOWN` 处理程序函数中实现此功能需要一些附加代码。  
  
 下面的代码示例实现橡胶带选择和其他功能。  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/CPP/rubber-banding-and-trackers_1.cpp)]  
  
 在橡皮筋方法期间，如果要允许 TRACKER 的可逆方向，您应调用使用第三个参数中的 [CRectTracker::TrackRubberBand](../Topic/CRectTracker::TrackRubberBand.md) 设置为 **TRUE**。  记住允许可逆方向有时将导致[CRectTracker::m\_rect](../Topic/CRectTracker::m_rect.md)反向。  这可以通过调用[CRect::NormalizeRect](../Topic/CRect::NormalizeRect.md)来更正。  
  
 有关更多信息，请参见 [容器客户项](../mfc/containers-client-items.md) 和 [自定义拖放](../mfc/drag-and-drop-customizing.md)。  
  
## 请参阅  
 [跟踪器：在您的 OLE 应用程序内实现跟踪器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [CRectTracker Class](../mfc/reference/crecttracker-class.md)