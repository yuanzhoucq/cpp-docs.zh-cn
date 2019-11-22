---
title: 视图类 (Windows)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: a3e0f837bc13c022bec91bfff6e38c1513abaf16
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302967"
---
# <a name="view-classes-windows"></a>视图类 (Windows)

`CView` 及其派生类是表示框架窗口的工作区的子窗口。 视图显示数据并接受文档输入。

视图类与文档类和框架窗口类关联，使用文档模板对象。

[CView](../mfc/reference/cview-class.md)<br/>
文档数据的应用程序特定视图的基类。 视图显示数据并接受用户输入以编辑或选择数据。 从 `CView`派生视图类。

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
具有滚动功能的视图的基类。 从 `CScrollView` 派生视图类以便自动滚动。

## <a name="form-and-record-views"></a>窗体和记录视图

窗体视图还会滚动查看。 它们基于对话框模板。

记录视图派生自窗体视图。 除了对话框模板以外，它们还具有到数据库的连接。

[CFormView](../mfc/reference/cformview-class.md)<br/>
其布局在对话框模板中定义的滚动视图。 从 `CFormView` 中派生一个类，以实现基于对话框模板的用户界面。

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
提供直接连接到数据访问对象（DAO）记录集对象的窗体视图。 与所有窗体视图一样，`CDaoRecordView` 基于对话框模板。 DAO 与 Access 数据库结合使用，并受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供直接连接到开放式数据库连接（ODBC）记录集对象的窗体视图。 与所有窗体视图一样，`CRecordView` 基于对话框模板。

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
提供 WebBrowser HTML 编辑平台功能的窗体视图。

## <a name="control-views"></a>控件视图

控件视图将控件显示为其视图。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
与 Windows 控件关联的所有视图的基类。 下面介绍了基于控件的视图。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows 标准编辑控件的视图（请参阅[CEdit](../mfc/reference/cedit-class.md)）。 编辑控件支持文本编辑、搜索、替换和滚动功能。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
包含 Windows rich edit 控件的视图（请参阅[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)）。 除了编辑控件的功能外，丰富的编辑控件还支持字体、颜色、段落格式和嵌入的 OLE 对象。

[CListView](../mfc/reference/clistview-class.md)<br/>
包含 Windows 列表控件的视图（请参阅[CListCtrl](../mfc/reference/clistctrl-class.md)）。 列表控件显示项的集合，每个项都包含一个图标和一个标签，其方式类似于文件资源管理器的右窗格。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
包含 Windows 树控件的视图（请参阅[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）。 树控件显示图标和标签的层次结构列表，其排列方式类似于文件资源管理器的左窗格。

## <a name="related-classes"></a>相关类

`CSplitterWnd` 允许在单个框架窗口中具有多个视图。 `CPrintDialog` 和 `CPrintInfo` 支持视图的打印和打印预览功能。 `CRichEditDoc` 和 `CRichEditCntrItem` 与 `CRichEditView` 结合使用来实现 OLE 容器功能。

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
一个窗口，用户可以将其拆分为多个窗格。 这些窗格可以按用户或固定大小进行调整。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
提供用于打印文件的标准对话框。

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
包含打印或打印预览作业相关信息的结构。 由 `CView`的打印体系结构使用。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
维护 `CRichEditView`中的 OLE 客户端项的列表。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
提供对存储在 `CRichEditView`中的 OLE 项的客户端访问。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
