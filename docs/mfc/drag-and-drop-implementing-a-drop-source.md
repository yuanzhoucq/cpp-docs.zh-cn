---
title: 拖放：实现放置源
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
ms.openlocfilehash: 2aa593fa953f7a9874036d48124ae7b92d88e0a6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768635"
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>拖放：实现放置源

本文介绍如何获取应用程序以向拖放操作提供数据。

基本实现放置源是相对简单。 第一步是确定哪些事件开始拖动操作。 建议用户界面指南定义拖动操作开始为选定的数据和一个**WM_LBUTTONDOWN**内所选数据点上发生的事件。 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)并[HIERSVR](../overview/visual-cpp-samples.md)请遵循以下准则。

如果你的应用程序是一个容器，并且所选的数据是某个链接或嵌入的对象的类型`COleClientItem`，调用其`DoDragDrop`成员函数。 否则，构造`COleDataSource`对象，并用所选内容，将其初始化并调用数据源对象的`DoDragDrop`成员函数。 如果你的应用程序服务器，请使用`COleServerItem::DoDragDrop`。 有关自定义标准的拖放行为的信息，请参阅文章[拖放到：自定义](../mfc/drag-and-drop-customizing.md)。

如果`DoDragDrop`将返回**DROPEFFECT_MOVE**，立即删除源文档中的源数据。 从任何其他返回值`DoDragDrop`放置源对任何影响。

有关详细信息，请参见:

- [实现放置目标](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [自定义拖放功能](../mfc/drag-and-drop-customizing.md)

- [创建和销毁 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [操作 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>请参阅

[拖放 (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)<br/>
[COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)<br/>
[CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
