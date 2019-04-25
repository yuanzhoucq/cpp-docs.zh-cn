---
title: 树控件拖放操作
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: c7febeec513d8004df2bd1cc42e4e97e027e9f17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167694"
---
# <a name="tree-control-drag-and-drop-operations"></a>树控件拖放操作

树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 在用户开始拖动项时发送通知。 该控件发送[TVN_BEGINDRAG](/windows/desktop/Controls/tvn-begindrag)通知消息，当用户开始拖动鼠标左键的项和一个[TVN_BEGINRDRAG](/windows/desktop/Controls/tvn-beginrdrag)通知消息，当用户开始拖动与右侧的按钮。 您可以防止树控件通过提供 TVS_DISABLEDRAGDROP 样式的树控件发送这些通知。

获取通过调用在拖动操作期间显示的图像[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage)成员函数。 树控件将基于所拖动的项标签创建一个拖动位图。 然后，树控件创建图像列表中，将位图添加到它，并返回一个指向[CImageList](../mfc/reference/cimagelist-class.md)对象。

必须提供实际拖动项的代码。 这通常涉及到使用图像列表函数的拖动功能和处理[WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove)并[WM_LBUTTONUP](/windows/desktop/inputdev/wm-lbuttonup) (或[WM_RBUTTONUP](/windows/desktop/inputdev/wm-rbuttonup))拖动操作开始之后发送的消息。 有关图像列表函数的详细信息，请参阅[CImageList](../mfc/reference/cimagelist-class.md)中*MFC 参考*并[图像列表](/windows/desktop/controls/image-lists)Windows SDK 中。 有关拖动树控件项的详细信息，请参阅[拖动树视图项](/windows/desktop/Controls/tree-view-controls)，还会在 Windows SDK。

如果树控件中的项是拖放操作的目标，则需要了解鼠标光标何时指向了目标项。 您可以通过调用查明[HitTest](../mfc/reference/ctreectrl-class.md#hittest)成员函数。 指定一个点和整数或的地址[TVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvhittestinfo)结构，其中包含鼠标光标的当前坐标。 当函数返回时，该整数或结构包含一个指示与树控件相关的鼠标光标的位置的标志。 如果光标在树控件中的某个项的上方，则该结构还包含该项的句柄。

您可以指示项是拖放操作的目标，通过调用[SetItem](../mfc/reference/ctreectrl-class.md#setitem)成员函数以将状态设置为`TVIS_DROPHILITED`值。 使用用于指示拖放目标的样式绘制具有此状态的项。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
