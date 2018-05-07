---
title: 查看类 （体系结构） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.view
dev_langs:
- C++
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11bb3d9e551089a156d255f7b27fb55cbe87bdbe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="view-classes-architecture"></a>视图类（体系结构）
`CView` 而其派生的类是表示框架窗口的工作区的子窗口。 视图显示数据，并接受输入文档。  
  
 视图类是与文档类和使用文档模板对象的框架窗口类相关联。  
  
 [CView](../mfc/reference/cview-class.md)  
 应用程序特定数据视图的文档的基类。 视图显示数据，并接受用户输入要编辑或选择数据。 派生您的视图类从`CView`。  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 带滚动功能的视图的基类。 派生视图类从`CScrollView`自动滚动。  
  
## <a name="form-and-record-views"></a>窗体和记录视图  
 窗体视图也滚动视图。 它们基于对话框模板。  
  
 记录视图派生而来窗体视图。 除了对话框模板，它们还具有与数据库的连接。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 在对话框模板中定义其布局滚动视图。 从派生类`CFormView`可以实现基于对话框模板的用户界面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供了一种直接连接到数据访问对象 (DAO) 记录集对象的视图。 如所有窗体视图中，`CDaoRecordView`基于对话框模板。  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 Web 浏览应用程序中的支持的控件。 该控件支持在 MFC 中的动态 HTML。  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 提供对窗体视图 MFC OLE DB 支持。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供了一种直接连接到开放式数据库连接 (ODBC) 记录集对象的视图。 如所有窗体视图中，`CRecordView`基于对话框模板。  
  
## <a name="control-views"></a>控件视图  
 控件视图其视图以显示控件。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 与 Windows 控件关联的所有视图的基类。 基于控件的视图如下所述。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 一个包含 Windows 标准视图编辑控件 (请参阅[CEdit](../mfc/reference/cedit-class.md))。 编辑控件支持文本编辑、 搜索、 替换和滚动功能。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 一个包含 Windows 丰富视图编辑控件 (请参阅[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 除编辑控件的功能，格式文本编辑控件支持字体、 颜色、 段落格式设置，和嵌入的 OLE 对象。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 列表控件的视图 (请参阅[CListCtrl](../mfc/reference/clistctrl-class.md))。 列表控件中的文件资源管理器的方式类似于右窗格中显示图标和字符串。  
  
 [Ctreeview 类](../mfc/reference/ctreeview-class.md)  
 包含 Windows 树控件的视图 (请参阅[CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 树控件显示图标和排列方式类似于左窗格中的文件资源管理器中的层次结构中的字符串。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

