---
title: "MFC 中可用的派生视图类 | Microsoft Docs"
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
  - "类 [C++], 派生"
  - "CView 类, 类派生自"
  - "派生类, 视图类"
  - "视图类, 派生"
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 中可用的派生视图类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表说明 MFC 视图的类以及它们的相互关系。  视图类的功能取决于它派生的 MFC 视图类。  
  
### 视图类  
  
|类|说明|  
|-------|--------|  
|[CView](../mfc/reference/cview-class.md)|的所有基类视图。|  
|[CCtrlView](../mfc/reference/cctrlview-class.md)|`CTreeView`、`CListView`、`CEditView`和 `CRichEditView`的基类。  这些类使您可以使用一个 Windows 公共控件的文档\/视图结构。|  
|[CEditView](../mfc/reference/ceditview-class.md)|基于 Windows 编辑框控件的简单视图。  允许输入和编辑文本，并且可以用作一简单文本编辑器应用程序。  另请参见`CRichEditView`。|  
|[CRichEditView](../mfc/reference/cricheditview-class.md)|包含 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) 对象的视图。  此类是与 `CEditView`类似，但是，与 `CEditView`不同的是，`CRichEditView` 处理的格式文本。|  
|[CListView](../mfc/reference/clistview-class.md)|包含 [CListCtrl](../mfc/reference/clistctrl-class.md) 对象的视图。|  
|[CTreeView](../mfc/reference/ctreeview-class.md)|包含 [CTreeCtrl](../mfc/reference/ctreectrl-class.md) 对象，类似于 Visual C\+\+ 的解决方案资源管理器窗口中的视图的视图。|  
|[CScrollView](../mfc/reference/cscrollview-class.md)|`CFormView`、`CRecordView`和 `CDaoRecordView`的基类。  滚动的内容视图实现的。|  
|[CFormView](../mfc/reference/cformview-class.md)|窗体视图，包含控件的视图。  基于窗体的应用程序提供一个或多个此类窗体接口。|  
|[CHtmlView](../mfc/reference/chtmlview-class.md)|应用程序用户可以浏览 Web 的站点的 Web 浏览器，以及视图文件夹在本地文件系统和网络上。  Web 浏览器视图还可为活动文档容器。|  
|[CRecordView](../mfc/reference/crecordview-class.md)|演示控件中的 ODBC 数据库记录窗体的视图。  如果您在项目中选择 ODBC 支持，视图的基类是 `CRecordView`。  视图连接到 `CRowset` 对象。|  
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|该窗体的视图控件中的 DAO 数据库记录。  如果选择项目中，DAO 支持视图的基类是 `CDaoRecordView`。  视图连接到 `CDaoRecordset` 对象。|  
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|在控件中显示 OLE DB 记录窗体的视图。  如果选择项目中，OLE DB 支持视图的基类是 `COleDBRecordView`。  视图连接到 `CRowset` 对象。|  
  
> [!NOTE]
>  自 MFC 版本 4.0 一样，`CEditView` 派生自 `CCtrlView`。  
  
 若要使用这些类在应用程序，请从它们派生应用程序的视图类。  有关相关信息，请参见 [滚动和缩放视图](../mfc/scrolling-and-scaling-views.md)。  有关数据库的类的更多信息，请参见 [概述：数据库编程](../data/data-access-programming-mfc-atl.md)。  
  
## 请参阅  
 [使用视图](../mfc/using-views.md)