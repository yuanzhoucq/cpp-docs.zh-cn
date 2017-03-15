---
title: "拖放：实现放置源 | Microsoft Docs"
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
  - "拖放, 调用 DoDragDrop"
  - "拖放, 放置源"
  - "拖放, 启动拖动操作"
  - "OLE 拖放, 调用 DoDragDrop"
  - "OLE 拖放, 放置源"
  - "OLE 拖放, 启动拖动操作"
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 拖放：实现放置源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何获取应用程序为拖放操作提供数据。  
  
 放置源的基本实现也相对较简单。  第一步是确定事件启动拖动操作。  建议用户界面指南定义拖动操作的开始为选定数据以及发生在点的选定数据内的 `WM_LBUTTONDOWN` 事件。  MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md) 和[HIERSVR](../top/visual-cpp-samples.md) 遵循这些准则。  
  
 如果应用程序是容器，并且选定的数据类型是链接或 `COleClientItem`类型的嵌入对象，请调用 `DoDragDrop` 成员函数。  否则，请构造 `COleDataSource` 对象，初始化该选择，并调用数据源对象的 `DoDragDrop` 成员函数。  如果应用程序是服务器，请使用 `COleServerItem::DoDragDrop`。  有关自定义标准拖放行为的信息，请参见 [拖放：自定义](../mfc/drag-and-drop-customizing.md)文章。  
  
 如果 `DoDragDrop` 返回 `DROPEFFECT_MOVE`，则直接删除原始文档的源数据。  从 `DoDragDrop` 中返回其他值没有对放置源产生影响。  
  
 有关详细信息，请参阅：  
  
-   [实现放置目标](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [自定义拖放](../mfc/drag-and-drop-customizing.md)  
  
-   [创建和销毁 OLE 数据和对象数据源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [控制OLE数据对象和数据源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## 请参阅  
 [拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)   
 [COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)   
 [CView::OnDragLeave](../Topic/CView::OnDragLeave.md)