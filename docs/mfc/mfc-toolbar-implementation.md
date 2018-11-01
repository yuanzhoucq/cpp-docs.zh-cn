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
ms.openlocfilehash: 93cf2f2a11c34b1bbe2d62e4e4cc6afab16e2fd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666786"
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具栏实现

工具栏是[控件条](../mfc/control-bars.md)，其中包含控件的位图图像。 这些映像可以行为类似于普通按钮、 复选框或单选按钮。 MFC 提供类[CToolbar](../mfc/reference/ctoolbar-class.md)管理工具栏。

如果启用该功能，MFC 工具栏的用户可以将它们停靠到窗口的边缘或它们"浮动"任意位置内的应用程序窗口。 MFC 不支持类似于开发环境中的可自定义工具栏。

MFC 还支持工具提示： 将鼠标放在按钮上时描述工具栏按钮的用途的小弹出窗口。 默认情况下，当用户按下工具栏按钮状态字符串将显示在状态栏中 （如果有）。 您可以激活"视窗的"状态栏更新时鼠标而无需按其定位在按钮上显示的状态字符串。

> [!NOTE]
>  从 MFC 4.0 版，开始工具栏和工具提示使用实现 Windows 95 和更高版本的功能而不是特定于 MFC 以前的实现。

为了向后兼容，MFC 将保留在类中的旧工具栏实现`COldToolBar`。 对于早期版本的 MFC 文档介绍`COldToolBar`下`CToolBar`。

通过应用程序向导中选择工具栏选项，在程序中创建第一个工具栏。 此外可以创建其他工具栏。

在这篇文章中引入以下：

- [工具栏按钮](#_core_toolbar_buttons)

- [停靠和浮动工具栏](#_core_docking_and_floating_toolbars)

- [工具栏和工具提示](#_core_toolbars_and_tool_tips)

- [CToolBar 和 CToolBarCtrl 类](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [工具栏位图](#_core_the_toolbar_bitmap)

##  <a name="_core_toolbar_buttons"></a> 工具栏按钮

在工具栏中的按钮是类似于菜单中的项。 这两种类型的用户界面对象生成命令，通过提供处理程序函数来处理您的程序。 工具栏按钮通常复制的菜单命令，提供对相同的功能的备用用户界面的功能。 此类重复排列只需通过为按钮和菜单项提供相同的 id。

您可以进行显示，并且像普通按钮、 复选框或单选按钮在工具栏按钮。 有关详细信息，请参阅类[CToolBar](../mfc/reference/ctoolbar-class.md)。

##  <a name="_core_docking_and_floating_toolbars"></a> 停靠和浮动工具栏

MFC 工具栏可以：

- 保持静止沿其父窗口的一侧。

- 拖动和"停靠，"或附加到任何一侧或两侧您指定的父窗口的用户。

- "浮动"或从框架窗口中，在其自己微型框架窗口，使用户可以移动它到任何方便的位置中分离。

- 浮动时调整大小。

有关详细信息，请参阅文章[停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)。

##  <a name="_core_toolbars_and_tool_tips"></a> 工具栏和工具提示

MFC 工具栏可以也可用于显示"工具提示"— 很小的弹出窗口，包含工具栏按钮的用途的简短文本说明。 用户将鼠标移动工具栏按钮，如工具提示窗口弹出并给出提示。 有关详细信息，请参阅文章[工具栏工具提示](../mfc/toolbar-tool-tips.md)。

##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar 和 CToolBarCtrl 类

管理通过类的应用程序的工具栏[CToolBar](../mfc/reference/ctoolbar-class.md)。 从 MFC 版本 4.0 中，开始`CToolBar`重新实现使用工具栏公共控件可在 Windows 95 或更高版本和 Windows NT 3.51 或更高版本。

因为 MFC 会使这种重新实现结果工具栏，更少 MFC 代码中使用的操作系统支持。 重新实现还改进了功能。 可以使用`CToolBar`成员函数以操作工具栏，或您可以获得对基础的引用[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象并调用其成员函数的自定义工具栏和其他功能。

> [!TIP]
>  如果您有大量投资的较早的 MFC 实现`CToolBar`，仍提供了支持。 请参阅文章[使用旧工具栏](../mfc/using-your-old-toolbars.md)。

另请参阅 MFC 常规示例[DOCKTOOL](../visual-cpp-samples.md)。

##  <a name="_core_the_toolbar_bitmap"></a> 工具栏位图

一旦构建完毕就`CToolBar`对象创建通过加载一个位图，其中包含一个图像可查看每个按钮的工具栏图像。 应用程序向导会使用 Visual c + + 创建可自定义的标准工具栏位图[工具栏编辑器](../windows/toolbar-editor.md)。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [工具栏基础知识](../mfc/toolbar-fundamentals.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)

- [使用旧工具栏](../mfc/using-your-old-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)并[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

## <a name="see-also"></a>请参阅

[工具栏](../mfc/toolbars.md)<br/>
[工具栏编辑器](../windows/toolbar-editor.md)

