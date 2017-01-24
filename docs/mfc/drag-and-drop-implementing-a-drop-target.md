---
title: "拖放：实现放置目标 | Microsoft Docs"
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
  - "拖放, 放置目标"
  - "OLE 拖放, 放置目标"
  - "OLE 拖放, 实现放置目标"
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 拖放：实现放置目标
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文概述如何让应用程序放置目标。  实现放置目标实现放置源采用比稍微多的工作，但是，这依然是相对简单。  这些方法也适用于非 OLE 应用程序。  
  
#### 实现放置目标  
  
1.  将成员变量为应用程序的每个视图。若要成为放置目标。  该成员变量都必须是 `COleDropTarget` 类型或从其派生的类。  
  
2.  在处理 `WM_CREATE` 的消息视图类函数 \(通常为 `OnCreate`\)，请调用新成员变量的 `Register` 成员函数。  当销毁，利用`Revoke` 将自动调用"视图。  
  
3.  重写函数。  如果希望在整个应用程序中相同的行为，请在重写视图类的这些函数。  如果您希望修改行为在不同情况中或者要启用删除对非`CView` 窗口，请重写 `COleDropTarget`这些函数的派生类。  
  
    |重写|授权|  
    |--------|--------|  
    |`OnDragEnter`|发生放置操作的窗口中。  当光标首次进入窗口时调用。|  
    |`OnDragLeave`|特定行为，在拖动操作保留指定的窗口。|  
    |`OnDragOver`|发生放置操作的窗口中。  调用，以及当光标在窗口中拖动。|  
    |`OnDrop`|放置到指定窗口中处理数据。|  
    |`OnScrollBy`|特定行为，该滚动是必需的目标窗口中。|  
  
 参见是 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md) 中的示例 MAINVIEW.CPP 文件这些函数如何。  
  
 有关详细信息，请参阅：  
  
-   [实现放置源](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [创建和销毁 OLE 数据和对象数据源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [控制OLE数据对象和数据源](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## 请参阅  
 [拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget Class](../mfc/reference/coledroptarget-class.md)