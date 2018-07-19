---
title: 停靠和浮动工具栏 |Microsoft 文档
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
ms.openlocfilehash: 317527d87c12a0c140c4a618ec4500dbe12bb003
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931884"
---
# <a name="docking-and-floating-toolbars"></a>停靠和浮动工具栏
Microsoft 基础类库支持可停靠工具栏。 可以附加或停靠到其父窗口中，任何一边可停靠工具栏或可以分离或浮动在其自己的微型框架窗口中。 此文章介绍了如何在你的应用程序中使用可停靠工具栏。  
  
 如果你使用应用程序向导生成你的应用程序的主干，系统会要求你选择是否希望可停靠工具栏。 默认情况下，应用程序向导生成的代码用于执行你的应用程序置于可停靠工具栏所需的三个操作：  
  
-   [启用在框架窗口中停靠](#_core_enabling_docking_in_a_frame_window)。  
  
-   [启用为工具栏停靠](#_core_enabling_docking_for_a_toolbar)。  
  
-   [将工具栏停靠 （到框架窗口）](#_core_docking_the_toolbar)。  
  
 如果缺少任何这些步骤，你的应用程序将显示标准工具栏。 有关在你的应用程序中每个可停靠工具栏，必须执行最后两个步骤。  
  
 这篇文章中涉及的其他主题包括：  
  
-   [浮动工具栏](#_core_floating_the_toolbar)  
  
-   [动态调整大小工具栏](#_core_dynamically_resizing_the_toolbar)  
  
-   [设置为固定样式工具栏的的换行位置](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)  
  
 请参阅 MFC 常规示例[DOCKTOOL](../visual-cpp-samples.md)有关示例。  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> 启用停靠在框架窗口  
 若要将工具栏停靠到框架窗口，框架窗口 （或目标） 必须启用以允许停靠。 这是使用[CFrameWnd::EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking)函数，其将一个*DWORD*参数是一套样式位，该值指示框架窗口的哪一侧接受停靠。 如果工具栏可停靠，有多个可以停靠的边，四条边所示的参数传递给`EnableDocking`使用按以下顺序： 上、 下、 左、 右。 如果你希望能够停靠控件条任何位置，则传递**CBRS_ALIGN_ANY**到`EnableDocking`。  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> 启用为工具栏停靠  
 准备停靠的目标后，您必须以类似的方式准备的工具栏 （或源）。 调用[CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking)对你想要停靠每一个工具栏，指定目标边到应该停靠工具栏。 如果未对调用中指定的侧边`CControlBar::EnableDocking`匹配四条边启用停靠在框架窗口中，不能停靠工具栏-它将浮动。 一旦浮动，它就会一直浮动工具栏，不能将停靠在框架窗口。  
  
 如果所需的效果是一个永久浮动工具栏，调用`EnableDocking`参数为 0。 然后调用[CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)。 工具栏将保持浮动，永远不能在任何位置停靠。  
  
##  <a name="_core_docking_the_toolbar"></a> 停靠工具栏  
 框架调用[CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar)当用户尝试删除允许停靠框架窗口的一侧上的工具栏。  
  
 此外，你可以随时到框架窗口停靠控件条调用此函数。 这通常可在初始化过程。 多个工具栏可停靠到框架窗口的特定边。  
  
##  <a name="_core_floating_the_toolbar"></a> 浮动工具栏  
 分离从框架窗口可停靠工具栏称为浮动工具栏。 调用[CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar)要这样做。 指定浮动工具栏、 它应将放置到的位置的点和确定浮动工具栏是水平还是垂直对齐方式。  
  
 当用户拖动工具栏离开其停靠位置，并将它放置在未启用停靠的位置，框架将调用此函数。 这可以是任意位置内部或外部框架窗口。 与`DockControlBar`，你还可以在初始化期间调用此函数。  
  
 可停靠工具栏的 MFC 实现不提供的一些扩展功能在某些应用程序支持可停靠工具栏中找到。 未提供可自定义工具栏等功能。  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> 动态调整大小工具栏  
 截至 Visual c + + 4.0 版，你可以使你的应用程序动态调整大小的浮动工具栏的用户。 通常，工具栏具有 long、 线性形状，水平显示。 但你可以更改工具栏的方向和形状。 例如，当用户在框架窗口的垂直侧之一将工具栏停靠，形状将更改为垂直布局。 还有可能以重新定形在一个矩形的具有包含多个行的按钮的工具栏。  
  
 你可以：  
  
-   动态调整大小指定为工具栏特性。  
  
-   指定固定的大小调整为工具栏特性。  
  
 若要提供此支持，有两个新工具栏样式在你调用中使用[CToolBar::Create](../mfc/reference/ctoolbar-class.md#create)成员函数。 它们是：  
  
-   **CBRS_SIZE_DYNAMIC**控件条是动态的。  
  
-   **CBRS_SIZE_FIXED**固定的控件条。  
  
 大小动态样式使用户可以调整大小工具栏时它浮动的但不是停靠时。 工具栏上"包装"在需要时更改形状，当用户拖动其边缘。  
  
 大小固定样式保留一个工具栏，修复按钮的每个列中的位置的换行状态。 应用程序的用户不能更改工具栏的形状。 工具栏包装在指定位置，如按钮之间的分隔符的位置。 这样可保持此形状，工具栏是否停靠或浮动。 其效果是包含多个列的按钮的固定的调色板。  
  
 你还可以使用[CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle)要在您的工具栏中返回的状态和按钮的样式。 按钮的样式确定按钮的显示方式以及它如何响应用户输入;该状态告诉按钮是否换行的状态。  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> 设置为固定样式工具栏的的换行位置  
 使用大小固定样式工具栏，指定工具栏按钮工具栏将换行的索引。 下面的代码演示如何执行此操作在主框架窗口的`OnCreate`重写：  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]  
  
 MFC 常规示例[DOCKTOOL](../visual-cpp-samples.md)演示如何使用类的成员函数[CControlBar](../mfc/reference/ccontrolbar-class.md)和[CToolBar](../mfc/reference/ctoolbar-class.md)管理工具栏的动态布局。 请参阅文件 EDITBAR。在 DOCKTOOL CPP。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [工具栏基础知识](../mfc/toolbar-fundamentals.md)  
  
-   [工具栏工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)

