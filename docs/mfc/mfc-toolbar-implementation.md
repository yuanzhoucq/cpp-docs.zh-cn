---
title: MFC 工具栏实现
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 38811be765d4427c4083b8f142b54fb67b9076a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359322"
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具栏实现

工具栏是包含控件的位图图像的控制[栏](../mfc/control-bars.md)。 这些图像可以像按钮、复选框或单选按钮一样。 MFC 提供[CToolbar](../mfc/reference/ctoolbar-class.md)类来管理工具栏。

如果启用它，MFC 工具栏的用户可以将它们停靠到窗口边缘，或将其"浮动"到应用程序窗口中的任意位置。 MFC 不支持开发环境中的可自定义工具栏。

MFC 还支持工具提示：在将鼠标放在按钮上时描述工具栏按钮用途的小弹出窗口。 默认情况下，当用户按下工具栏按钮时，状态栏中将显示一个状态字符串（如果有）。 您可以激活"飞过"状态栏更新，以在鼠标位于按钮上时显示状态字符串，而无需按按它。

> [!NOTE]
> 自 MFC 版本 4.0 起，工具栏和工具提示使用 Windows 95 和更高版本的功能实现，而不是特定于 MFC 的先前实现。

对于向后兼容性，MFC 在 类`COldToolBar`中保留较旧的工具栏实现。 MFC 早期版本的文档在 下`COldToolBar``CToolBar`描述。

通过在"应用程序向导"中选择工具栏选项，创建程序中的第一个工具栏。 您还可以创建其他工具栏。

本文介绍了以下内容：

- [工具栏按钮](#_core_toolbar_buttons)

- [停靠和浮动工具栏](#_core_docking_and_floating_toolbars)

- [工具栏和工具提示](#_core_toolbars_and_tool_tips)

- [CToolBar 和 CToolBarCtrl 类](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [工具栏位图](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>工具栏按钮

工具栏中的按钮与菜单中的项目类似。 这两种用户界面对象都会生成命令，程序通过提供处理程序函数来处理这些命令。 通常工具栏按钮复制菜单命令的功能，为相同的功能提供替代用户界面。 这种重复只需为按钮和菜单项提供相同的 ID 即可进行排列。

您可以使工具栏中的按钮显示并显示为按钮、复选框或单选按钮。 有关详细信息，请参阅类[CToolBar](../mfc/reference/ctoolbar-class.md)。

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>停靠和浮动工具栏

MFC 工具栏可以：

- 沿其父窗口的一侧保持静止。

- 由用户拖动并"停靠"或附加到您指定的父窗口的任何一侧或侧面。

- 在自己的迷你框架窗口中"浮动"或脱离框架窗口，以便用户可以将其移动到任何方便的位置。

- 浮动时调整大小。

有关详细信息，请参阅文章[停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)。

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>工具栏和工具提示

MFC 工具栏也可以显示"工具提示" - 包含工具栏按钮用途的简短文本说明的微小弹出窗口。 当用户将鼠标移到工具栏按钮上时，工具提示窗口将弹出以提供提示。 有关详细信息，请参阅文章[工具栏工具提示](../mfc/toolbar-tool-tips.md)。

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>CToolBar 和 CToolBarCtrl 类

您可以通过[CToolBar](../mfc/reference/ctoolbar-class.md)类管理应用程序的工具栏。 自 MFC 版本 4.0 起，`CToolBar`已重新实现，以使用 Windows 95 或更高版本下可用的工具栏通用控件以及 Windows NT 版本 3.51 或更高版本。

这种重新实现会导致工具栏的 MFC 代码减少，因为 MFC 利用了操作系统支持。 重新实现还可以提高功能。 您可以使用`CToolBar`成员函数操作工具栏，也可以获取对基础[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象的引用，并调用其成员函数进行工具栏自定义和其他功能。

> [!TIP]
> 如果您已投入大量资金对 的旧 MFC 实现`CToolBar`，则该支持仍然可用。 请参阅[使用旧工具栏](../mfc/using-your-old-toolbars.md)的文章。

另请参阅 MFC 一般示例[DOCKTOOL](../overview/visual-cpp-samples.md)。

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>工具栏位图

构造后，`CToolBar`对象通过加载单个位图来创建工具栏图像，该位图包含每个按钮的一个图像。 应用程序向导创建一个标准工具栏位图，您可以使用可视化C++[工具栏编辑器](../windows/toolbar-editor.md)进行自定义。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [工具栏基础知识](../mfc/toolbar-fundamentals.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)

- [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

## <a name="see-also"></a>另请参阅

[工具栏](../mfc/toolbars.md)<br/>
[工具栏编辑器](../windows/toolbar-editor.md)
