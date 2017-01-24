---
title: "视图类（体系结构） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件视图"
  - "窗体和记录视图"
  - "视图类"
  - "视图类, 体系结构"
ms.assetid: 8894579a-1436-441e-b985-83711061e495
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 视图类（体系结构）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CView` 及其派生类是指框架窗口的工作区内的子窗口。  视图显示数据并接受文档的输入。  
  
 使用文档模板对象，类视图与文档框架窗口类和类。  
  
 [CView](../mfc/reference/cview-class.md)  
 文档数据的特定视图的基类。  视图显示数据并接受编辑或选择数据的用户输入。  从 `CView`派生的类。  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 视图的基类提供滚动功能。  从视图的自动滚动的 `CScrollView` 派生类。  
  
## 窗体和记录视图  
 窗体视图还滚动视图。  它们基于对话框模板。  
  
 记录视图窗体视图从派生。  除了对话框模板之外，还有与数据库的连接。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 布局是在对话框模板定义的滚动视图。  从 `CFormView` 派生的类来实现基于对话框模板的用户界面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供直接连接的一个窗体向视图数据访问对象 \(DAO\) \(DAO\) 记录集对象。  同所有窗体视图中，`CDaoRecordView` 基于对话框模板。  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 若要支持浏览在 Web 应用程序中的控件。  MFC 控件支持中的动态 HTML。  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 对于 Forms 视图提供 MFC OLE DB 支持。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供直接连接的一个窗体向视图开放式数据库连接 \(ODBC\) 记录集对象。  同所有窗体视图中，`CRecordView` 基于对话框模板。  
  
## 控件视图  
 控件视图中显示控件与它们的视图。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 所有基的类演示与 Windows 控件。  根据视图控件的下面。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含一个标准 Windows 编辑控件的视图 \(参见 [CEdit](../mfc/reference/cedit-class.md)\)。  编辑控件编辑，搜索和替换，滚动功能的文本支持。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Rich Edit 控件视图包含一个窗口 \(请参见\)。[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) 除了编辑控件的功能之外，Rich Edit 控件支持字体、颜色、段落格式和嵌入的 OLE 对象。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Windows 包含一个列表控件 \(视图参见 [CListCtrl](../mfc/reference/clistctrl-class.md)\)。  列表控件显示图标和字符串与类似文件资源管理器右窗格。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 窗口包含一个树控件 \(视图参见 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)\)。  树控件以层次结构和位置的字符串显示图标文件类似于资源管理器左窗格。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)