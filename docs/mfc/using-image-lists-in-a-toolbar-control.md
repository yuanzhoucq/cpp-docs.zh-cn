---
title: 在工具栏控件中使用图像列表 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3604de0b3b24b638e549c6823ea6c95036543c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401766"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>在工具栏控件中使用图像列表

默认情况下，使用工具栏控件中的按钮的图像存储为单个位图中。 但是，您可以将按钮图像存储一系列图像列表中。 工具栏控件对象可以使用最多三个单独的映像列表：

- 启用当前已启用的工具栏按钮的图像列表包含图像。

- 禁用当前已禁用的工具栏按钮的图像列表包含图像。

- 突出显示当前突出显示的工具栏按钮的图像列表包含图像。 仅当工具栏使用 TBSTYLE_FLAT 样式时使用此图像列表。

这些图像列表由工具栏控件时将其与关联`CToolBarCtrl`对象。 通过调用来实现这种关联[CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist)， [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)，并[SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist)。

默认情况下，MFC 使用`CToolBar`类，以实现 MFC 应用程序工具栏。 但是，`GetToolBarCtrl`成员函数可用于检索嵌入`CToolBarCtrl`对象。 然后可以调用`CToolBarCtrl`使用返回的对象的成员函数。

下面的示例演示此技术通过将分配的已启用 (`m_ToolBarImages`) 和已禁用 (`m_ToolBarDisabledImages`) 到图像列表`CToolBarCtrl`对象 (`m_ToolBarCtrl`)。

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
>  工具栏对象使用图像列表必须是永久对象。 出于此原因，它们通常是数据成员的 MFC 类;在此示例中，主框架窗口类。

图像列表关联与后`CToolBarCtrl`对象，该框架会自动显示正确的按钮图像。

## <a name="see-also"></a>请参阅

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

