---
title: 视图类（体系结构）
ms.date: 09/17/2019
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
ms.openlocfilehash: 7235ccfea1f41dd185f0b5b6be9b39ea16250d94
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447176"
---
# <a name="view-classes-architecture"></a>视图类（体系结构）

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

[CHtmlView](../mfc/reference/chtmlview-class.md)<br/>
支持应用程序中的 Web 浏览控件。 控件支持 MFC 中的动态 HTML。

[COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)<br/>
为窗体视图提供 MFC OLE DB 支持。

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
提供直接连接到开放式数据库连接（ODBC）记录集对象的窗体视图。 与所有窗体视图一样，`CRecordView` 基于对话框模板。

## <a name="control-views"></a>控件视图

控件视图将控件显示为其视图。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
与 Windows 控件关联的所有视图的基类。 下面介绍了基于控件的视图。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows 标准编辑控件的视图（请参阅[CEdit](../mfc/reference/cedit-class.md)）。 编辑控件支持文本编辑、搜索、替换和滚动功能。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
包含 Windows rich edit 控件的视图（请参阅[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)）。 除了编辑控件的功能外，丰富的编辑控件还支持字体、颜色、段落格式和嵌入的 OLE 对象。

[CListView](../mfc/reference/clistview-class.md)<br/>
包含 Windows 列表控件的视图（请参阅[CListCtrl](../mfc/reference/clistctrl-class.md)）。 列表控件以类似于文件资源管理器右窗格的方式显示图标和字符串。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
包含 Windows 树控件的视图（请参阅[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）。 树形控件以与文件资源管理器左窗格类似的方式显示在层次结构中排列的图标和字符串。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
