---
title: 树控件拖放操作
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 5d2c5aa511844a3d7cbe64d9a15f8ffb46046b29
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510906"
---
# <a name="tree-control-drag-and-drop-operations"></a>树控件拖放操作

当用户开始拖动某个项时, 树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 将发送通知。 当用户使用鼠标左键开始拖动项时, 控件将发送[TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag)通知消息, 当用户使用右按钮开始拖动时, 控件将发送[TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag)通知消息。 可以通过为树控件提供 TVS_DISABLEDRAGDROP 样式来阻止树控件发送这些通知。

在拖动操作过程中, 通过调用[CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage)成员函数来获取要显示的图像。 树控件将基于所拖动的项标签创建一个拖动位图。 然后, 树形控件创建一个图像列表, 向其中添加位图, 并返回指向[CImageList](../mfc/reference/cimagelist-class.md)对象的指针。

必须提供实际拖动项的代码。 这通常涉及使用图像列表函数的拖动功能, 并处理在拖动操作开始后发送的[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)和[WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (或[WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) 消息。 有关图像列表函数的详细信息, 请参阅 Windows SDK 中 " *MFC 参考*" 和 "[图像" 列表](/windows/win32/controls/image-lists)中的[CImageList](../mfc/reference/cimagelist-class.md) 。 有关拖动树控件项的详细信息, 请参阅 "Windows SDK 中的[拖动树视图项](/windows/win32/Controls/tree-view-controls)。

如果树控件中的项是拖放操作的目标，则需要了解鼠标光标何时指向了目标项。 可以通过调用[system.windows.media.visualtreehelper.hittest](../mfc/reference/ctreectrl-class.md#hittest)成员函数来了解。 指定点和整数, 或指定包含鼠标光标当前坐标的[TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo)结构的地址。 当函数返回时，该整数或结构包含一个指示与树控件相关的鼠标光标的位置的标志。 如果光标在树控件中的某个项的上方，则该结构还包含该项的句柄。

可以通过调用[SetItem](../mfc/reference/ctreectrl-class.md#setitem)成员函数将状态设置为`TVIS_DROPHILITED`值, 指示项是拖放操作的目标。 使用用于指示拖放目标的样式绘制具有此状态的项。

## <a name="see-also"></a>请参阅

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
