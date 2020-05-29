---
title: MFC 中可用的派生视图类
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 12b31074e4fcc2ed6a83e3669e1044f5b9caedab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373507"
---
# <a name="derived-view-classes-available-in-mfc"></a>MFC 中可用的派生视图类

下表显示了 MFC 的视图类及其彼此之间的关系。 视图类的功能取决于它派生自的 MFC 视图类。

### <a name="view-classes"></a>查看类

|类|说明|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|所有视图的基类。|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|的基类`CTreeView` `CListView`，`CEditView`和`CRichEditView`。 这些类允许您使用文档/视图体系结构与指示的 Windows 公共控件。|
|[CEditView](../mfc/reference/ceditview-class.md)|基于 Windows 编辑框控件的简单视图。 允许输入和编辑文本，并可用作简单文本编辑器应用程序的基础。 另请参阅 `CRichEditView`。|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|包含[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)对象的视图。 类类似于`CEditView`，但与 不同`CEditView`，`CRichEditView`处理格式化的文本。|
|[CListView](../mfc/reference/clistview-class.md)|包含[CListCtrl](../mfc/reference/clistctrl-class.md)对象的视图。|
|[CTreeView](../mfc/reference/ctreeview-class.md)|包含[CTreeCtrl](../mfc/reference/ctreectrl-class.md)对象的视图，用于类似于可视化C++中的解决方案资源管理器窗口的视图。|
|[CScrollView](../mfc/reference/cscrollview-class.md)|的基类`CFormView` `CRecordView`，`CDaoRecordView`和 。 实现滚动视图的内容。|
|[CFormView](../mfc/reference/cformview-class.md)|窗体视图，包含控件的视图。 基于表单的应用程序提供一个或多个此类表单接口。|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|应用程序用户可以使用的 Web 浏览器视图浏览万维网上的网站以及本地文件系统和网络上的文件夹。 Web 浏览器视图也可以用作活动文档容器。|
|[CRecordView](../mfc/reference/crecordview-class.md)|在控件中显示 ODBC 数据库记录的窗体视图。 如果在项目中选择 ODBC 支持，则视图的基类为`CRecordView`。 视图连接到对象`CRowset`。|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|在控件中显示 DAO 数据库记录的窗体视图。 如果在项目中选择 DAO 支持，则视图的基类为`CDaoRecordView`。 视图连接到对象`CDaoRecordset`。|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|在控件中显示 OLE DB 记录的窗体视图。 如果在项目中选择 OLE DB 支持，则视图的基类为`COleDBRecordView`。 视图连接到对象`CRowset`。|

> [!NOTE]
> 自 MFC 版本 4.0`CEditView`起`CCtrlView`，派生自 。

要在应用程序中使用这些类，请从这些类派生应用程序的视图类。 有关详细信息，请参阅[滚动和缩放视图](../mfc/scrolling-and-scaling-views.md)。 有关数据库类的详细信息，请参阅[概述：数据库编程](../data/data-access-programming-mfc-atl.md)。

## <a name="see-also"></a>另请参阅

[使用视图](../mfc/using-views.md)
