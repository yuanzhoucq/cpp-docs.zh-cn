---
title: 派生的 MFC 中可用的视图类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f8d058891b361b3747caafd9c4bd279c7626856
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426908"
---
# <a name="derived-view-classes-available-in-mfc"></a>MFC 中可用的派生视图类

下表显示了 MFC 的视图类和它们彼此之间的关系。 视图类的功能依赖于它派生自 MFC 视图类。

### <a name="view-classes"></a>视图类

|类|描述|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|所有视图的基类。|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|基类的`CTreeView`， `CListView`， `CEditView`，和`CRichEditView`。 这些类使你可以使用文档/视图体系结构与所指示的 Windows 公共控件。|
|[CEditView](../mfc/reference/ceditview-class.md)|基于 Windows 的简单视图编辑框控件。 允许输入和编辑文本，并可用作简单的文本编辑器应用程序的基础。 另请参见`CRichEditView`。|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|一个视图，其中包含[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)对象。 此类是类似于`CEditView`，但不同于`CEditView`，`CRichEditView`句柄的格式化文本。|
|[CListView](../mfc/reference/clistview-class.md)|一个视图，其中包含[CListCtrl](../mfc/reference/clistctrl-class.md)对象。|
|[Ctreeview 类](../mfc/reference/ctreeview-class.md)|一个视图，其中包含[CTreeCtrl](../mfc/reference/ctreectrl-class.md)对象，类似于 Visual c + + 中的解决方案资源管理器窗口的视图。|
|[CScrollView](../mfc/reference/cscrollview-class.md)|基类的`CFormView`， `CRecordView`，和`CDaoRecordView`。 实现滚动视图的内容。|
|[CFormView](../mfc/reference/cformview-class.md)|窗体视图中，包含控件的视图。 基于窗体的应用程序提供了一个或多个此类窗体接口。|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Web 浏览器视图与其应用程序的用户可以浏览万维网，以及文件夹上的站点本地文件系统中和在网络上。 在 Web 浏览器视图还可以为活动文档容器。|
|[CRecordView](../mfc/reference/crecordview-class.md)|窗体视图显示在控件中的 ODBC 数据库记录。 如果在项目中选择的 ODBC 支持，该视图的基类是`CRecordView`。 查看连接到`CRowset`对象。|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|在控件中显示 DAO 数据库记录窗体视图。 如果在项目中选择 DAO 支持，该视图的基类是`CDaoRecordView`。 查看连接到`CDaoRecordset`对象。|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|在控件中显示 OLE DB 记录窗体视图。 如果在项目中选择 OLE DB 的支持，该视图的基类是`COleDBRecordView`。 查看连接到`CRowset`对象。|

> [!NOTE]
>  从 MFC 版本 4.0 中，开始`CEditView`派生自`CCtrlView`。

若要在应用程序中使用这些类，请从它们派生应用程序的视图类。 有关相关信息，请参阅[滚动和缩放视图](../mfc/scrolling-and-scaling-views.md)。 数据库类的详细信息，请参阅[概述： 数据库编程](../data/data-access-programming-mfc-atl.md)。

## <a name="see-also"></a>请参阅

[使用视图](../mfc/using-views.md)

