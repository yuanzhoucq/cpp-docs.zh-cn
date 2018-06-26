---
title: MFC 工具栏实现 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d21bfa1dcc39e00de852203d05a2eae743b8a2f6
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929220"
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具栏实现
工具栏是[控件条](../mfc/control-bars.md)包含控件的位图图像。 这些映像可以行为类似于普通按钮、 复选框或单选按钮。 MFC 还提供类[CToolbar](../mfc/reference/ctoolbar-class.md)管理工具栏。  
  
 如果你启用它，MFC 工具栏的用户可以将它们固定到窗口的边缘或者"float"它们任意位置在应用程序窗口中。 MFC 不支持类似于开发环境中的可自定义工具栏。  
  
 MFC 还支持工具提示： 当你将鼠标放在按钮描述工具栏按钮的用途的小型弹出窗口。 默认情况下，当用户按工具栏按钮，状态字符串显示在状态栏中 （如果有）。 你可以激活"即时通过"状态栏更新鼠标而无需按其定位在按钮上时显示的状态字符串。  
  
> [!NOTE]
>  从 MFC 4.0 版开始工具栏和工具提示实现而不特定于 MFC 以前的实现中使用 Windows 95 和更高版本的功能。  
  
 为了向后兼容，MFC 将保留在类中的旧工具栏实现`COldToolBar`。 对于早期版本的 MFC 文档介绍`COldToolBar`下`CToolBar`。  
  
 在程序中创建第一个工具栏，通过在应用程序向导选择工具栏上的选项。 你还可以创建其他的工具栏。  
  
 在本文中引入以下：  
  
-   [工具栏按钮](#_core_toolbar_buttons)  
  
-   [停靠和浮动工具栏](#_core_docking_and_floating_toolbars)  
  
-   [工具栏和工具提示](#_core_toolbars_and_tool_tips)  
  
-   [CToolBar 和 CToolBarCtrl 类](#_core_the_ctoolbar_and_ctoolbarctrl_classes)  
  
-   [工具栏位图](#_core_the_toolbar_bitmap)  
  
##  <a name="_core_toolbar_buttons"></a> 工具栏按钮  
 在工具栏按钮，类似于菜单中的项。 这两种用户界面对象生成命令，通过提供处理程序函数处理程序。 工具栏按钮通常复制的菜单命令，提供对相同的功能的备用用户界面的功能。 实现这种复制排列只需通过为按钮和菜单项提供相同的 id。  
  
 你可以在工具栏中的按钮显示为并用作普通按钮、 复选框或单选按钮。 有关详细信息，请参阅类[CToolBar](../mfc/reference/ctoolbar-class.md)。  
  
##  <a name="_core_docking_and_floating_toolbars"></a> 停靠和浮动工具栏  
 MFC 工具栏可以：  
  
-   保持静止沿其父窗口的一侧。  
  
-   拖放和"停靠，"或附加，用户向任何一侧或两侧您指定的父窗口。  
  
-   "浮动，"或从框架窗口中，在其自己的微型框架窗口以便用户可以将它移动到任何方便的位置中分离。  
  
-   浮动时调整大小。  
  
 有关详细信息，请参阅文章[停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)。  
  
##  <a name="_core_toolbars_and_tool_tips"></a> 工具栏和工具提示  
 MFC 工具栏也可以做出以显示"工具提示"-包含工具栏按钮的用途的简短文本说明的小型弹出窗口。 当用户移动工具栏按钮上方时鼠标，工具提示窗口弹出并给出提示。 有关详细信息，请参阅文章[工具栏工具提示](../mfc/toolbar-tool-tips.md)。  
  
##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar 和 CToolBarCtrl 类  
 管理你的应用程序工具栏，通过类[CToolBar](../mfc/reference/ctoolbar-class.md)。 从 MFC 4.0 版本后，开始`CToolBar`已根据要使用的 Windows 95 下提供或更高版本工具栏公共控件和 Windows NT 版本 3.51 或更高版本。  
  
 此重新实现导致更少的 MFC 代码关于工具栏的因为 MFC 会显著提高的操作系统支持的使用。 重新实现还改进了功能。 你可以使用`CToolBar`成员函数以操作工具栏，也可以获得对基础的引用[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象并调用其成员函数以自定义工具栏和其他功能。  
  
> [!TIP]
>  如果你已投入了大量的较旧的 MFC 实现中`CToolBar`，仍提供了支持。 请参阅文章[使用你的旧工具栏](../mfc/using-your-old-toolbars.md)。  
  
 另请参阅 MFC 常规示例[DOCKTOOL](../visual-cpp-samples.md)。  
  
##  <a name="_core_the_toolbar_bitmap"></a> 工具栏位图  
 一次构造，`CToolBar`对象通过加载一个位图，其中包含每个按钮的一个映像创建工具栏图像。 应用程序向导会使用 Visual c + + 创建可以自定义的标准工具栏位图[工具栏编辑器](../windows/toolbar-editor.md)。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [工具栏基础知识](../mfc/toolbar-fundamentals.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具栏工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用旧工具栏](../mfc/using-your-old-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类  
  
## <a name="see-also"></a>请参阅  
 [工具栏](../mfc/toolbars.md)   
 [工具栏编辑器](../windows/toolbar-editor.md)

