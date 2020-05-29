---
title: 在工具栏控件中使用图像列表
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: 81468528c15300a7e9ace6b20fd9fb34818f1928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366495"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>在工具栏控件中使用图像列表

默认情况下，工具栏控件中按钮使用的图像将存储为单个位图。 但是，您还可以将按钮图像存储在一组图像列表中。 工具栏控件对象最多可以使用三个单独的图像列表：

- 已启用的图像列表 包含当前启用的工具栏按钮的图像。

- 禁用的图像列表 包含当前禁用的工具栏按钮的图像。

- 突出显示的图像列表 包含当前突出显示的工具栏按钮的图像。 仅当工具栏使用TBSTYLE_FLAT样式时，才会使用此图像列表。

当您将它们与`CToolBarCtrl`对象关联时，工具栏控件会使用这些图像列表。 此关联是通过调用[CToolBarCtrl：：设置图像列表](../mfc/reference/ctoolbarctrl-class.md#setimagelist)、[设置禁用图像列表](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)和[SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)来实现的。

默认情况下，MFC 使用`CToolBar`该类来实现 MFC 应用程序工具栏。 但是，`GetToolBarCtrl`成员函数可用于检索嵌入`CToolBarCtrl`的对象。 然后，可以使用返回的对象对`CToolBarCtrl`成员函数进行调用。

下面的示例通过将已启用的`m_ToolBarImages`（ ） 和禁用 （`m_ToolBarDisabledImages`） 映像列表分配给`CToolBarCtrl`对象`m_ToolBarCtrl`（ ） 演示此技术。

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> 工具栏对象使用的图像列表必须是永久对象。 因此，它们通常是 MFC 类的数据成员;在此示例中，主框架窗口类。

一旦图像列表与`CToolBarCtrl`对象关联，框架将自动显示正确的按钮图像。

## <a name="see-also"></a>另请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
