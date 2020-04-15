---
title: 停靠和浮动工具栏
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: 30113565167b96b0df84a65768a1dfabe92ceffe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369771"
---
# <a name="docking-and-floating-toolbars"></a>停靠和浮动工具栏

Microsoft 基础类库支持可停靠工具栏。 可停靠工具栏可以附加或停靠到其父窗口的任何一侧，也可以在其自己的迷你框架窗口中分离或浮动。 本文介绍如何在应用程序中使用可停靠工具栏。

如果使用应用程序向导生成应用程序的骨架，系统将要求您选择是否需要可停靠工具栏。 默认情况下，应用程序向导生成代码，这些代码执行在应用程序中放置可停靠工具栏所需的三个操作：

- [在框架窗口中启用停靠](#_core_enabling_docking_in_a_frame_window)。

- [启用工具栏的停靠](#_core_enabling_docking_for_a_toolbar)。

- [停靠工具栏（停靠到框架窗口）。](#_core_docking_the_toolbar)

如果缺少这些步骤中的任何一个，则应用程序将显示一个标准工具栏。 必须为应用程序中的每个可停靠工具栏执行最后两个步骤。

本文介绍的其他主题包括：

- [浮动工具栏](#_core_floating_the_toolbar)

- [动态调整工具栏大小](#_core_dynamically_resizing_the_toolbar)

- [设置固定样式工具栏的换行位置](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

有关示例，请参阅 MFC 常规示例[DOCKTOOL。](../overview/visual-cpp-samples.md)

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>在框架窗口中启用停靠

要将工具栏停靠到框架窗口，必须启用框架窗口（或目标）以允许停靠。 这是使用[CFrameWnd：：启用停靠](../mfc/reference/cframewnd-class.md#enabledocking)函数完成的，该函数采用一个*DWORD*参数，该参数是一组样式位，指示帧窗口的哪一侧接受停靠。 如果工具栏即将停靠，并且有多个边可以停靠，则传递给的参数中指示的边`EnableDocking`按以下顺序使用：顶部、底部、左侧、右侧。 如果希望能够停靠控制栏 **，CBRS_ALIGN_ANY传递到**`EnableDocking`。

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>启用工具栏停靠

准备好停靠目标后，必须以类似方式准备工具栏（或源）。 调用[CControlBar：为](../mfc/reference/ccontrolbar-class.md#enabledocking)要停靠的每个工具栏启用停靠，指定工具栏应停靠到的目标边。 如果在调用中指定的任何边数都`CControlBar::EnableDocking`与框架窗口中启用的停靠的边匹配，工具栏将无法停靠 - 它将浮动。 浮动后，它仍然是一个浮动工具栏，无法停靠到框架窗口。

如果所需的效果是永久浮动工具栏，请调用`EnableDocking`参数为 0。 然后调用[CFramewnd：：FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)。 工具栏保持浮动状态，永久无法停靠到任何位置。

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>停靠工具栏

当用户尝试将工具栏放在允许停靠的帧窗口的一侧时，框架将调用[CFrameWnd：:DockControlBar。](../mfc/reference/cframewnd-class.md#dockcontrolbar)

此外，您可以随时调用此功能以将控制条停靠到帧窗口。 这通常在初始化期间完成。 多个工具栏可以停靠到框架窗口的特定侧。

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>浮动工具栏

从框架窗口分离可停靠工具栏称为浮动工具栏。 调用[CFramewnd：：FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)执行此操作。 指定要浮动的工具栏、应放置工具栏的点以及确定浮动工具栏是水平工具栏还是垂直的对齐样式。

当用户将工具栏拖离其停靠位置并将其拖放到未启用停靠的位置时，框架将调用此功能。 这可以位于框架窗口内外的任意位置。 与`DockControlBar`，您还可以在初始化期间调用此函数。

可停靠工具栏的 MFC 实现不提供某些支持可停靠工具栏的应用程序中的扩展功能。 不提供可自定义工具栏等功能。

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>动态调整工具栏大小

从 Visual C++ 版本 4.0 起，您可以让应用程序的用户动态调整浮动工具栏的大小。 通常，工具栏具有长线性形状，水平显示。 但是，您可以更改工具栏的方向和形状。 例如，当用户将工具栏停靠在框架窗口的一个垂直边上时，形状将变为垂直布局。 还可以将工具栏重塑为具有多行按钮的矩形。

可以：

- 指定动态大小调整为工具栏特征。

- 将固定大小调整指定为工具栏特征。

要提供此支持，在调用[CToolBar：：：创建](../mfc/reference/ctoolbar-class.md#create)成员函数时，有两种新的工具栏样式可供使用。 它们分别是：

- **CBRS_SIZE_DYNAMIC**控制栏是动态的。

- **CBRS_SIZE_FIXED**控制栏已固定。

大小动态样式允许用户在工具栏浮动时调整其大小，但在停靠工具栏时不会调整工具栏的大小。 工具栏在用户拖动其边缘时需要更改形状的位置"换行"。

大小固定样式保留工具栏的换行状态，固定按钮在每个列中的位置。 应用程序的用户无法更改工具栏的形状。 工具栏在指定位置进行换行，例如按钮之间的分隔符位置。 无论工具栏是停靠还是浮动，它都保持此形状。 效果是具有多列按钮的固定调色板。

您还可以使用[CToolBar：：GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle)为工具栏上的按钮返回状态和样式。 按钮的样式确定按钮的显示方式以及按钮对用户输入的响应方式;状态指示按钮是否处于包装状态。

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>设置固定样式工具栏的换行位置

对于具有大小固定样式的工具栏，请指定工具栏将换行的工具栏按钮索引。 以下代码演示如何在主框架窗口的`OnCreate`重写中执行此操作：

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 常规示例[DOCKTOOL](../overview/visual-cpp-samples.md)演示如何使用类[CControlBar](../mfc/reference/ccontrolbar-class.md)和[CToolBar](../mfc/reference/ctoolbar-class.md)的成员函数来管理工具栏的动态布局。 请参阅文件 EDITBAR。在 DOCKTOOL 中的 CPP。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [工具栏基础知识](../mfc/toolbar-fundamentals.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [使用旧工具栏](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)
