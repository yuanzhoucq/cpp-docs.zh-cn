---
title: 停靠和浮动工具栏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95990ef4f1d2b1c6eb4278f645226e57b67e15e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399012"
---
# <a name="docking-and-floating-toolbars"></a>停靠和浮动工具栏

Microsoft 基础类库支持可停靠工具栏。 可停靠工具栏可以附加，或停靠到其父窗口的任何一侧或被分离或浮动在其自己的微型框架窗口中。 本文介绍如何在您的应用程序中使用可停靠工具栏。

如果你使用应用程序向导生成的应用程序框架，您需要选择是否想要可停靠工具栏。 默认情况下，应用程序向导生成的执行要放置在你的应用程序中可停靠工具栏所需的三个操作的代码：

- [启用停靠在框架窗口中](#_core_enabling_docking_in_a_frame_window)。

- [启用工具栏停靠](#_core_enabling_docking_for_a_toolbar)。

- [将工具栏停靠 （框架窗口中）](#_core_docking_the_toolbar)。

如果缺少任何这些步骤，你的应用程序将显示标准工具栏。 必须在应用程序中每个可停靠工具栏执行最后两个步骤。

本文中所述的其他主题包括：

- [浮动工具栏](#_core_floating_the_toolbar)

- [动态调整大小的工具栏](#_core_dynamically_resizing_the_toolbar)

- [设置换行位置固定样式工具栏](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

请参阅 MFC 常规示例[DOCKTOOL](../visual-cpp-samples.md)有关示例。

##  <a name="_core_enabling_docking_in_a_frame_window"></a> 启用停靠在框架窗口中

若要将工具栏停靠到框架窗口，框架窗口 （或目标） 必须启用以允许停靠。 这是使用[CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking)函数采用一个*DWORD*参数，它是一组样式位，该值指示框架窗口的哪一侧接受停靠。 如果工具栏是以停靠，并有可能停靠的多个方面，各边所指示的参数传递到`EnableDocking`使用按以下顺序： 上、 下、 左、 右。 如果您希望能够以停靠控件条任意位置，则传递**CBRS_ALIGN_ANY**到`EnableDocking`。

##  <a name="_core_enabling_docking_for_a_toolbar"></a> 启用停靠工具栏

准备停靠的目标后，您必须以类似的方式准备工具栏 （或源）。 调用[CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking)为每个你想要停靠的工具栏上，指定的目标边到应停靠工具栏。 如果没有对调用中指定的边，则`CControlBar::EnableDocking`匹配为停靠在框架窗口中启用的方面，不能在停靠工具栏，它将浮动。 一旦浮动，它将保持浮动工具栏，不能将停靠在框架窗口。

如果所需的效果永久浮动工具栏，调用`EnableDocking`参数为 0。 然后调用[CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)。 工具栏将保持浮动，永远不能在任何位置停靠。

##  <a name="_core_docking_the_toolbar"></a> 停靠工具栏

框架将调用[CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar)用户尝试删除工具栏上的允许停靠在框架窗口一侧。

此外，你可以随时停靠控件条的框架窗口调用此函数。 通常这是在初始化过程。 多个工具栏可停靠到框架窗口的特定边。

##  <a name="_core_floating_the_toolbar"></a> 浮动工具栏

分离从框架窗口可停靠工具栏称为浮动工具栏。 调用[CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)若要执行此操作。 指定要浮动工具栏、 它应放置的位置，该点和确定浮动工具栏是水平还是垂直对齐方式。

当用户拖动工具栏离开其停靠位置，并将其放在未启用的停靠的位置，框架将调用此函数。 这可以是任意位置的内部或外部框架窗口。 与使用`DockControlBar`，您还可以在初始化期间调用此函数。

可停靠工具栏的 MFC 实现不提供的一些扩展功能支持可停靠工具栏某些应用程序中。 未提供可自定义工具栏等功能。

##  <a name="_core_dynamically_resizing_the_toolbar"></a> 动态调整大小的工具栏

截至 Visual c + + 4.0 版，你可更加动态重设大小的浮动工具栏应用程序的用户。 通常，工具栏的长、 线性形状，水平显示。 但可以更改工具栏的方向和形状。 例如，当用户将停靠工具栏根据一个框架窗口的垂直边，形状将更改为竖排版式。 还有可能工具栏重塑，一个具有多个行的按钮的矩形。

你可以：

- 为工具栏特性指定动态调整大小。

- 指定固定的大小调整为工具栏特性。

若要提供此支持，有两个调用中将使用的新工具栏样式[CToolBar::Create](../mfc/reference/ctoolbar-class.md#create)成员函数。 它们是：

- **CBRS_SIZE_DYNAMIC**控件栏是动态的。

- **CBRS_SIZE_FIXED**控件条固定。

大小动态样式使用户可以调整浮动，但未同时停靠工具栏的大小。 在工具栏"包装"在需要时更改形状，当用户拖动它的边缘。

修复了样式的大小将保留的换行状态的工具栏上，修复每个列中按钮的位置。 应用程序的用户不能更改工具栏的形状。 工具栏包装在指定的位置，例如在按钮之间的分隔符的位置。 工具栏是否停靠或浮动，它会维护此形状。 结果是与多个列的按钮的固定的调色板。

此外可以使用[CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle)返回您的工具栏上的状态和按钮的样式。 按钮的样式确定按钮的显示方式以及它如何响应用户输入;该状态表示按钮是否处于已包装的状态。

##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> 设置换行位置固定样式工具栏

使用大小固定样式工具栏，指定工具栏按钮在工具栏会换行的索引。 下面的代码演示如何执行此操作在主框架窗口的`OnCreate`重写：

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

MFC 常规示例[DOCKTOOL](../visual-cpp-samples.md)演示如何使用类的成员函数[CControlBar](../mfc/reference/ccontrolbar-class.md)并[CToolBar](../mfc/reference/ctoolbar-class.md)管理工具栏的动态布局。 请参阅文件 EDITBAR。在 DOCKTOOL CPP。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [工具栏基础知识](../mfc/toolbar-fundamentals.md)

- [工具栏工具提示](../mfc/toolbar-tool-tips.md)

- [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)

