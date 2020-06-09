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
ms.openlocfilehash: f40d8860f2e514bf3c9e9364a664326250c9627a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615834"
---
# <a name="docking-and-floating-toolbars"></a>停靠和浮动工具栏

Microsoft 基础类库支持可停靠工具栏。 可停靠工具栏可以附加或停靠在其父窗口的任何一侧，也可以在其自身的小型框架窗口中分离或浮动。 本文介绍如何在应用程序中使用可停靠工具栏。

如果使用应用程序向导生成应用程序的主干，系统会要求你选择是否希望可停靠工具栏。 默认情况下，应用程序向导将生成执行以下三个操作所需的三个操作：

- [在框架窗口中启用停靠](#_core_enabling_docking_in_a_frame_window)。

- [为工具栏启用停靠](#_core_enabling_docking_for_a_toolbar)。

- [停靠工具栏（到框架窗口）](#_core_docking_the_toolbar)。

如果缺少这些步骤中的任何一个，应用程序将显示标准工具栏。 必须为应用程序中的每个可停靠工具栏执行最后两个步骤。

本文中介绍的其他主题包括：

- [浮动工具栏](#_core_floating_the_toolbar)

- [动态调整工具栏大小](#_core_dynamically_resizing_the_toolbar)

- [设置固定样式的工具栏的环绕位置](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

有关示例，请参阅 MFC 常规示例[DOCKTOOL](../overview/visual-cpp-samples.md) 。

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>在框架窗口中启用停靠

若要将工具栏停靠到框架窗口，必须启用框架窗口（或目标）以允许停靠。 这是通过使用[CFrameWnd：： EnableDocking](reference/cframewnd-class.md#enabledocking)函数实现的，该函数采用一个*DWORD*参数，该参数是一组样式位，指示框架窗口的哪一侧接受停靠。 如果工具栏即将停靠并且有多个边可以停靠到，则按以下顺序使用在参数中指定的边 `EnableDocking` ：上、下、左、右。 如果希望能够在任何位置停靠控制条，请将**CBRS_ALIGN_ANY**传递给 `EnableDocking` 。

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>启用工具栏停靠

为停靠准备好目标后，必须以类似的方式准备工具栏（或源）。 为每个要停靠的工具栏调用[CControlBar：： EnableDocking](reference/ccontrolbar-class.md#enabledocking) ，同时指定工具栏应停靠到的目标端。 如果在调用中指定的两侧都 `CControlBar::EnableDocking` 不与框架窗口中为停靠启用的边匹配，则工具栏无法停靠，它将浮动。 当它浮动后，它仍是一个浮动工具栏，无法停靠到框架窗口中。

如果所需的效果是永久性浮动工具栏，请 `EnableDocking` 使用参数0进行调用。 然后调用[CFrameWnd：： FloatControlBar](reference/cframewnd-class.md#floatcontrolbar)。 工具栏保持浮动，不能在任何位置停靠。

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>停靠工具栏

当用户尝试将工具栏置于允许停靠的框架窗口的一侧时，框架将调用[CFrameWnd：:D ockcontrolbar](reference/cframewnd-class.md#dockcontrolbar) 。

此外，您可以随时调用此函数以将控件条停靠到框架窗口中。 这通常是在初始化过程中完成的。 多个工具栏可停靠到框架窗口的特定侧。

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>浮动工具栏

从框架窗口分离可停靠工具栏称为 "浮动工具栏"。 调用[CFrameWnd：： FloatControlBar](reference/cframewnd-class.md#floatcontrolbar)来执行此操作。 指定要浮动的工具栏、应放置它的位置和确定浮动工具栏是水平还是垂直的对齐样式。

当用户将工具栏拖离停靠位置，并将其放置在未启用停靠的位置时，框架会调用此函数。 这可以是框架窗口内部或外部的任何位置。 与一样 `DockControlBar` ，您也可以在初始化期间调用此函数。

可停靠工具栏的 MFC 实现不提供某些支持可停靠工具栏的应用程序中的某些扩展功能。 不提供可自定义工具栏等功能。

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>动态调整工具栏大小

从 Visual C++ 版本4.0，你可以让应用程序的用户动态调整浮动工具栏的大小。 通常，工具栏有一个水平显示的长线性形状。 但可以更改工具栏的方向和形状。 例如，当用户将工具栏停靠在框架窗口的垂直边时，形状将更改为垂直布局。 还可以将工具栏调整为包含多行按钮的矩形。

方法：

- 将动态调整大小指定为工具栏特征。

- 将固定大小指定为工具栏特征。

为了提供此支持，在对[CToolBar：： Create](reference/ctoolbar-class.md#create)成员函数的调用中使用了两个新的工具栏样式。 它们分别是：

- **CBRS_SIZE_DYNAMIC**控件条是动态的。

- **CBRS_SIZE_FIXED**控制条是固定的。

大小动态样式使用户能够在工具栏浮动时调整其大小，但不能在停靠时进行调整。 工具栏在用户拖动其边缘时需要更改形状的位置 "换行"。

大小固定样式保留工具栏的换行状态，修复每个列中按钮的位置。 应用程序的用户不能更改工具栏的形状。 工具栏在指定位置（如按钮之间的分隔符位置）换行。 不管工具栏是停靠还是浮动，它都能保持此形状。 该效果是一个固定调色板，其中包含多个按钮列。

还可以使用[CToolBar：： GetButtonStyle](reference/ctoolbar-class.md#getbuttonstyle)为工具栏上的按钮返回状态和样式。 按钮的样式确定按钮的显示方式以及它如何响应用户输入;状态指示按钮是否处于已包装状态。

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>设置固定样式的工具栏的环绕位置

对于大小固定样式的工具栏，指定工具栏将环绕的工具栏按钮索引。 下面的代码演示如何在主框架窗口的重写中执行此 `OnCreate` 操作：

[!code-cpp[NVC_MFCDocViewSDI#10](codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 常规示例[DOCKTOOL](../overview/visual-cpp-samples.md)演示如何使用[CControlBar](reference/ccontrolbar-class.md)和[CToolBar](reference/ctoolbar-class.md)类的成员函数来管理工具栏的动态布局。 请参阅文件 EDITBAR。DOCKTOOL 中的 CPP。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [工具栏基础知识](toolbar-fundamentals.md)

- [工具栏工具提示](toolbar-tool-tips.md)

- [使用旧工具栏](using-your-old-toolbars.md)

## <a name="see-also"></a>另请参阅

[MFC 工具栏实现](mfc-toolbar-implementation.md)
