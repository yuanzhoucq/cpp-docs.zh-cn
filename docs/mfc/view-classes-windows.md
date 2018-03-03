---
title: "查看类 (Windows) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.view
dev_langs:
- C++
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d737176df2676f543f47bb77a0d205fa7c908fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="view-classes-windows"></a>视图类 (Windows)
`CView`而其派生的类是表示框架窗口的工作区的子窗口。 视图显示数据，并接受输入文档。  
  
 视图类是与文档类和使用文档模板对象的框架窗口类相关联。  
  
 [CView](../mfc/reference/cview-class.md)  
 应用程序特定数据视图的文档的基类。 视图显示数据，并接受用户输入要编辑或选择数据。 派生视图类或从类`CView`。  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 带滚动功能的视图的基类。 派生视图类从`CScrollView`自动滚动。  
  
## <a name="form-and-record-views"></a>窗体和记录视图  
 窗体视图也滚动视图。 它们基于对话框模板。  
  
 记录视图派生而来窗体视图。 除了对话框模板，它们还具有与数据库的连接。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 在对话框模板中定义其布局滚动视图。 从派生类`CFormView`可以实现基于对话框模板的用户界面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供了一种直接连接到数据访问对象 (DAO) 记录集对象的视图。 如所有窗体视图中，`CDaoRecordView`基于对话框模板。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供了一种直接连接到开放式数据库连接 (ODBC) 记录集对象的视图。 如所有窗体视图中，`CRecordView`基于对话框模板。  
  
 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)  
 窗体视图提供 WebBrowser HTML 编辑平台功能。  
  
## <a name="control-views"></a>控件视图  
 控件视图其视图以显示控件。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 与 Windows 控件关联的所有视图的基类。 基于控件的视图如下所述。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 一个包含 Windows 标准视图编辑控件 (请参阅[CEdit](../mfc/reference/cedit-class.md))。 编辑控件支持文本编辑、 搜索、 替换和滚动功能。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 一个包含 Windows 丰富视图编辑控件 (请参阅[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 除编辑控件的功能，格式文本编辑控件支持字体、 颜色、 段落格式设置，和嵌入的 OLE 对象。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 包含 Windows 列表控件的视图 (请参阅[CListCtrl](../mfc/reference/clistctrl-class.md))。 列表控件显示的项，其中每个包括的一个图标和标签时，方式类似于右窗格中的文件资源管理器中的集合。  
  
 [Ctreeview 类](../mfc/reference/ctreeview-class.md)  
 包含 Windows 树控件的视图 (请参阅[CTreeCtrl](../mfc/reference/ctreectrl-class.md))。 树控件显示图标和标签排列方式类似于左窗格中的文件资源管理器中的分层的列表。  
  
## <a name="related-classes"></a>相关的类  
 `CSplitterWnd`可以在单个框架窗口内有多个视图。 `CPrintDialog`和`CPrintInfo`支持视图的打印和打印预览功能。 `CRichEditDoc`和`CRichEditCntrItem`用于`CRichEditView`实现 OLE 容器功能。  
  
 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)  
 用户可以拆分为多个窗格窗口。 这些窗格可以是可由用户或固定的大小调整大小。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 为打印文件中提供的标准对话框。  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 包含有关打印或打印预览作业的信息的结构。 使用`CView`的打印体系结构。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 维护中的 OLE 客户端项的列表`CRichEditView`。  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 提供对 OLE 项存储在客户端访问`CRichEditView`。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

