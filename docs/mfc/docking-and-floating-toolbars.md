---
title: "停靠和浮动工具栏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CBRS_SIZE_DYNAMIC"
  - "CBRS_SIZE_FIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBRS_ALIGN_ANY 常量"
  - "CBRS_SIZE_DYNAMIC 常量"
  - "CBRS_SIZE_FIXED 常量"
  - "固定大小的工具栏"
  - "浮动调色板"
  - "浮动工具栏"
  - "框架窗口, 工具栏停靠"
  - "调色板, 浮动"
  - "大小"
  - "大小, 工具栏"
  - "工具栏控件 [MFC], 换行"
  - "工具栏 [C++], 停靠"
  - "工具栏 [C++], 浮动"
  - "工具栏 [C++], 大小"
  - "工具栏 [C++], 换行"
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 停靠和浮动工具栏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类 \(MFC\) 库支持停靠工具栏。  可停靠工具栏可以被附加，或停靠到其父窗口的任何一边，或者可以通过在自己的要框窗口中被分离或浮动。  本文在应用程序演示如何使用停靠的工具栏。  
  
 如果使用应用程序向导生成应用程序的主干，会要求您选择是否希望停靠工具栏。  默认情况下，应用程序向导生成应用需要在程序执行三个操作中放置可停靠工具栏的代码：  
  
-   [在框架窗口的停靠](#_core_enabling_docking_in_a_frame_window)。  
  
-   [启用工具栏的停靠](#_core_enabling_docking_for_a_toolbar)。  
  
-   [\(工具栏停靠到框架窗口。\)](#_core_docking_the_toolbar)。  
  
 如果以下任意步骤一个缺少，则应用程序将显示标准工具栏。  后两个步骤对应用程序中的每一个可停靠工具栏都必须执行。  
  
 本文包含的其他主题包括：  
  
-   [浮动工具栏](#_core_floating_the_toolbar)  
  
-   [动态调整工具栏](#_core_dynamically_resizing_the_toolbar)  
  
-   [将固定样式的工具栏的位置](#_core_setting_wrap_positions_for_a_fixed.2d.style_toolbar)  
  
 用于示例参见 MFC 泛型示例 [DOCKTOOL](../top/visual-cpp-samples.md)。  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> 在框架窗口的停靠  
 将要停靠工具栏\) 附加到框架窗口，必须启用框架窗口 \(或目标\) 允许停靠。  使用 [CFrameWnd::EnableDocking](../Topic/CFrameWnd::EnableDocking.md) 函数，这是，采用一个 `DWORD` 参数是一组样式位指示框架窗口的哪一边接受停靠。  如果工具栏将停靠，它具有多端可能会停靠到，参数中指示的端传递给 `EnableDocking` 使用以下顺序：顶部，底部，左侧，权限。  如果希望可以将控制条停靠在任意位置，请将 `CBRS_ALIGN_ANY` 传递给 `EnableDocking`。  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> 启用工具栏的停靠  
 在目标为停靠准备后，必须准备或工具栏类似地 \(源\)。  要停靠的每个工具栏调用 [CControlBar::EnableDocking](../Topic/CControlBar::EnableDocking.md)，指定工具栏应停靠到的目标边。  如果调用指定的边都对 `CControlBar::EnableDocking` 与启用停靠的边中框架窗口，则工具栏无法停靠 \- 它将浮动。  工具栏一旦浮动，将保持为浮动工具栏，不能停靠到框架窗口。  
  
 如果要永久的效果是浮动工具栏，带参数调用 `EnableDocking` 0。  然后调用 [CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md)。  保持为浮动工具栏，不永久任何位置停靠。  
  
##  <a name="_core_docking_the_toolbar"></a> 停靠工具栏  
 框架调用 [CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md)，当用户尝试删除允许停靠在框架窗口中的工具栏。端  
  
 此外，可以随时调用此函数控制条停靠到框架窗口。  这在初始化时通常执行。  多个工具栏可以停靠到框架窗口的一种特例端。  
  
##  <a name="_core_floating_the_toolbar"></a> 浮动工具栏  
 分离。可停靠工具栏同框架窗口浮动工具栏调用。  调用为此的 [CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md)。  指定工具栏将浮动的，则应将的和确定的点对齐样式为浮动工具栏是否为水平还是垂直方向。  
  
 框架将调用此函数，当用户拖动工具栏其停靠的位置并将其停靠在未启用时的位置。  这可以是任意位置或在框架窗口和中。  使用 `DockControlBar`，则可以初始化期间也调用此函数。  
  
 可停靠工具栏的 MFC 实现不提供在支持停靠工具栏的某些应用程序中的某些扩展功能。  如未提供的自定义工具栏功能。  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> 动态调整工具栏  
 自 Visual C\+\+ 4.0 版起，您可以使它成为可以为应用程序的用户动态调整大小的浮动工具栏。  通常情况下，工具栏包含长，线性的形状，水平显示。  但是，可以更改工具栏的方向及其形状。  例如，工具栏停靠，则用户某个框架窗口时垂直的边，形状对垂直布局。  改造工具栏到使用多行按钮的矩形也是可能的。  
  
 您可以：  
  
-   动态指定的大小作为工具栏特性。  
  
-   指定修复了大小作为工具栏特性。  
  
 为了提供此支持，有两个工具栏样式用于调用 [CToolBar::Create](../Topic/CToolBar::Create.md) 成员函数。  它们是：  
  
-   **CBRS\_SIZE\_DYNAMIC** 控件条是动态的。  
  
-   **CBRS\_SIZE\_FIXED** 控件条是固定的。  
  
 范围动态样式允许用户调整工具栏，则浮动时，但没有，在停靠时。  工具栏“包装”必需更改形状用作用户拖动其边缘。  
  
 范围固定样式保留工具栏的换行状态，修复按钮位置的各列中。  应用程序用户无法更改工具栏的形状。  工具栏将在指定的位置，例如在按钮之间的分隔符的位置。  它包含此形状工具栏无论是停靠或浮动。  效果是具有多按钮列固定的调色板。  
  
 还可以使用 [CToolBar::GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md) 返回一个状态和样式按钮的工具栏上。  按钮的样式确定按钮外观，它如何响应用户输入；状态告知按钮是否为换行的状态。  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed.2d.style_toolbar"></a> 将固定样式的工具栏的位置  
 对于带范围固定样式的工具栏，其中指定工具栏按钮索引工具栏将包装。  下面的代码显示如何做在主框架窗口的 `OnCreate` 重写：  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/CPP/docking-and-floating-toolbars_1.cpp)]  
  
 MFC 泛型示例 [DOCKTOOL](../top/visual-cpp-samples.md) 演示如何使用类的成员管理函数 [CToolBar](../mfc/reference/ctoolbar-class.md)[CControlBar](../mfc/reference/ccontrolbar-class.md) 和工具栏的动态布局。  DOCKTOOL 参见中的文件 EDITBAR.CPP。  
  
### 您想进一步了解什么？  
  
-   [工具栏基本法则](../mfc/toolbar-fundamentals.md)  
  
-   [工具栏的工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [使用以前的工具栏](../mfc/using-your-old-toolbars.md)  
  
## 请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)