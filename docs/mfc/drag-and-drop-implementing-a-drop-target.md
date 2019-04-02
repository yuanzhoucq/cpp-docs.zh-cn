---
title: 拖放：实现放置目标
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
ms.openlocfilehash: 46501193569d7f3098e23c67c68c76ce20a82ea3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58766672"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>拖放：实现放置目标

本文概述了如何使你的应用程序拖放目标。 实现放置目标采用稍有更多的工作，而不是实现放置源，但是仍然相对简单。 这些技术也适用于非 OLE 应用程序。

#### <a name="to-implement-a-drop-target"></a>若要实现拖放目标

1. 将成员变量添加到你想要作为拖放目标的应用程序中的每个视图。 此成员变量的类型必须为`COleDropTarget`或从其派生的类。

1. 从您的视图类的函数用于处理**WM_CREATE**消息 (通常`OnCreate`)，调用新成员变量的`Register`成员函数。 `Revoke` 将自动为您调用视图时销毁。

1. 重写以下函数。 如果想在整个应用程序相同的行为，重写视图类中的这些函数。 如果你想要修改在个别情况下的行为，或者想要启用删除非`CView`windows 中，重写这些函数中的你`COleDropTarget`-派生的类。

    |替代|若要允许|
    |--------------|--------------|
    |`OnDragEnter`|删除操作发生在窗口中。 当光标首次进入窗口时调用。|
    |`OnDragLeave`|当拖放操作离开指定的窗口的特殊行为。|
    |`OnDragOver`|删除操作发生在窗口中。 当光标拖过窗口时调用。|
    |`OnDrop`|处理的数据要放入指定的窗口。|
    |`OnScrollBy`|需要滚动时在目标窗口中的特殊行为。|

请参阅在 MAINVIEW。文件中的 MFC OLE 示例的 CPP [OCLIENT](../overview/visual-cpp-samples.md)以举例说明这些函数是如何协同工作。

有关详细信息，请参见:

- [实现放置源](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [创建和销毁 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [操作 OLE 数据对象和数据源](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>请参阅

[拖放 (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropTarget 类](../mfc/reference/coledroptarget-class.md)
