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
ms.openlocfilehash: 7876e9403389c19a24e5a482534d0f223eaa4bf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626113"
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具栏实现

工具栏是包含控件的位图图像的[控件条](control-bars.md)。 这些图像的行为可能与普通按钮、复选框或单选按钮相同。 MFC 提供类[CToolbar](reference/ctoolbar-class.md)来管理工具栏。

如果启用，MFC 工具栏的用户可将其停靠到窗口边缘，或在应用程序窗口中的任意位置 "浮动"。 MFC 不支持类似于开发环境中的自定义工具栏。

MFC 还支持工具提示：当你将鼠标悬停在按钮上时，用于描述工具栏按钮用途的小的弹出窗口。 默认情况下，当用户按下工具栏按钮时，状态栏（如果有）中会显示一个状态字符串。 当鼠标置于按钮上但未按下时，可通过状态栏更新来激活 "动态"。

> [!NOTE]
> 从 MFC 版本4.0，使用 Windows 95 和更高版本的功能而不是特定于 MFC 的以前的实现实现了工具栏和工具提示。

为了向后兼容，MFC 在类中保留了较旧的工具栏实现 `COldToolBar` 。 早期版本的 MFC 的文档 `COldToolBar` 在下进行说明 `CToolBar` 。

在应用程序向导中选择 "工具栏" 选项，以创建程序中的第一个工具栏。 你还可以创建其他工具栏。

本文介绍了以下内容：

- [工具栏按钮](#_core_toolbar_buttons)

- [停靠和浮动工具栏](#_core_docking_and_floating_toolbars)

- [工具栏和工具提示](#_core_toolbars_and_tool_tips)

- [CToolBar 和 CToolBarCtrl 类](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [工具栏位图](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>工具栏按钮

工具栏中的按钮类似于菜单中的项。 两种用户界面对象都生成命令，程序通过提供处理程序函数来处理这些命令。 工具栏按钮通常会复制菜单命令的功能，并为相同的功能提供一个替代的用户界面。 此类复制只是通过提供相同 ID 的按钮和菜单项来进行排列。

您可以使工具栏上的按钮显示为按钮、复选框或单选按钮，并表现为按钮。 有关详细信息，请参阅类[CToolBar](reference/ctoolbar-class.md)。

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>停靠和浮动工具栏

MFC 工具栏可以：

- 保持在其父窗口的一侧。

- 由用户拖动到您指定的父窗口的任意一侧或两侧。

- "浮动" 或从框架窗口中分离，它位于其自身的袖珍框架窗口中，因此用户可以将其移到任何方便的位置。

- 在浮动时调整大小。

有关详细信息，请参阅文章[停靠和浮动工具栏](docking-and-floating-toolbars.md)。

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>工具栏和工具提示

还可以使用 MFC 工具栏来显示 "工具提示"，其中包含工具栏按钮用途的简短文本说明的小弹出窗口。 当用户将鼠标指针移到工具栏按钮上时，工具提示窗口会弹出以提供提示。 有关详细信息，请参阅文章[工具栏工具提示](toolbar-tool-tips.md)。

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>CToolBar 和 CToolBarCtrl 类

通过类[CToolBar](reference/ctoolbar-class.md)管理应用程序的工具栏。 从 MFC 版本4.0 起，已 `CToolBar` 重新实现使用 windows 95 或更高版本下的工具栏公共控件以及 WINDOWS NT 3.51 或更高版本。

此重新实现导致工具栏的 MFC 代码更少，因为 MFC 利用操作系统支持。 重新实现还改进了功能。 您可以使用 `CToolBar` 成员函数来操作工具栏，或者可以获取对基础[CToolBarCtrl](reference/ctoolbarctrl-class.md)对象的引用，并调用其成员函数以便进行工具栏自定义和其他功能。

> [!TIP]
> 如果你已在的较早的 MFC 实现中投入了大量资金 `CToolBar` ，则该支持仍可用。 请参阅[使用旧工具栏](using-your-old-toolbars.md)的文章。

另请参阅 MFC 常规示例[DOCKTOOL](../overview/visual-cpp-samples.md)。

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>工具栏位图

构造后， `CToolBar` 对象通过加载每个按钮都包含一个图像的单个位图来创建工具栏图像。 应用程序向导创建可使用 Visual C++[工具栏编辑器](../windows/toolbar-editor.md)自定义的标准工具栏位图。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [工具栏基础知识](toolbar-fundamentals.md)

- [停靠和浮动工具栏](docking-and-floating-toolbars.md)

- [工具栏工具提示](toolbar-tool-tips.md)

- [使用 Toolbar 控件](working-with-the-toolbar-control.md)

- [使用您的旧工具栏](using-your-old-toolbars.md)

- [CToolBar](reference/ctoolbar-class.md)和[CToolBarCtrl](reference/ctoolbarctrl-class.md)类

## <a name="see-also"></a>另请参阅

[工具栏](toolbars.md)<br/>
[工具栏编辑器](../windows/toolbar-editor.md)
