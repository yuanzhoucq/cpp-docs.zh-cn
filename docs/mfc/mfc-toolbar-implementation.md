---
title: "MFC 工具栏实现 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - " [C++], 工具栏"
  - "按钮 [C++], MFC 工具栏"
  - "CToolBar 类, 创建工具栏"
  - "CToolBarCtrl 类, 实现工具栏"
  - "停靠工具栏"
  - "浮动工具栏"
  - "MFC 工具栏"
  - "工具提示 [C++], 启用"
  - "工具栏控件 [MFC]"
  - "工具栏 [C++]"
  - "工具栏 [C++], 创建"
  - "工具栏 [C++], 停靠"
  - "工具栏 [C++], 浮动"
  - "工具栏 [C++], 实现 MFC 工具栏"
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 工具栏实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

工具栏是包含控件位图的[控件条](../mfc/control-bars.md)。  这些图像可以正常运行如按钮、选定框、单选按钮。  MFC提供类[CToolbar](../mfc/reference/ctoolbar-class.md)用来管理工具栏。  
  
 如果启用它，MFC 工具栏的用户在应用程序窗口中可以停靠到窗口的边缘或“的任意位置。  MFC在开发环境中不支持自定义的工具栏。  
  
 MFC 还支持工具提示：在你鼠标经过按钮时描述工具栏按钮的作用的小型弹出窗口会弹出。  默认情况下，当用户按一个工具栏按钮时，状态字符串会出现在状态栏 \(如果有\)。  可以激活“更随”状态栏航班显示状态字符串，当鼠标位于按钮时显示，而不按它。  
  
> [!NOTE]
>  基于 MFC 4.0 版中，工具栏和工具提示的实现使用 Windows 95 和更高版本的功能而不是以前执行特定于 MFC。  
  
 但为了向后兼容，MFC在 **COldToolBar**类中将仍然保留旧的控件。  MFC描述**COldToolBar**的早期文档位于`CToolBar`。  
  
 在你的程序中创建第一个工具栏在应用程序向导中通过选择工具栏选项。  还可以创建其他的工具栏。  
  
 以下在本文中有介绍：  
  
-   [工具栏按钮](#_core_toolbar_buttons)  
  
-   [停靠和浮动工具栏](#_core_docking_and_floating_toolbars)  
  
-   [工具栏和工具提示](#_core_toolbars_and_tool_tips)  
  
-   [CToolBar 和 CToolBarCtrl 类](#_core_the_ctoolbar_and_ctoolbarctrl_classes)  
  
-   [工具栏位图](#_core_the_toolbar_bitmap)  
  
##  <a name="_core_toolbar_buttons"></a> 工具栏按钮  
 工具栏上的按钮类似于在菜单中的项。  所有用户界面对象生成命令，程序通过提供处理程序函数来处理程序。  通常工具栏按钮重复菜单命令的功能，对同一中功能提供另一种交替的用户界面。  通过给予菜单项和按钮相同的ID会让相同功能很容易整理。  
  
 您可以在工具栏上显示和是实现行为，就如同按钮、选定框、单选按钮。  有关更多信息，请参见类 [CToolBar](../mfc/reference/ctoolbar-class.md)。  
  
##  <a name="_core_docking_and_floating_toolbars"></a> 停靠和浮动工具栏  
 MFC 工具栏中能够：  
  
-   沿其父窗口一侧的保持其固定样式  
  
-   通过指定父窗口的任何一边，让用户拖动和“停靠，”或附加。  
  
-   浮动或者从窗口中分离，在其自己的微型框窗口中，以便用户可以移动到任何方便的位置。  
  
-   浮动时请调整大小浮动时。  
  
 有关详细信息，参见文章 [Docking and Floating Toolbars](../mfc/docking-and-floating-toolbars.md)。  
  
##  <a name="_core_toolbars_and_tool_tips"></a> 工具栏和工具提示  
 MFC 工具栏还可以进行工具提示，包含工具栏按钮的用途的简短说明的工具提示”—微小的弹出窗口。  当用户移动到工具栏按钮上，工具提示窗口会弹出提供一个提示。  有关详细信息，请参见文章[Toolbar Tool Tips](../mfc/toolbar-tool-tips.md)。  
  
##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar 和 CToolBarCtrl 类  
 [CToolbar](../mfc/reference/ctoolbar-class.md)类用来管理工具栏。  基于 MFC 4.0 版中，`CToolBar`由工具栏公共控件重新实现，它在Windows 95或者以后的版本以及Windows NT 3.51版以及后期版本中可用。  
  
 因为 MFC 利用操作系统支持，此 reimplementation 导致工具栏的少 MFC 代码。  新的实现还增强功能。  你可以使用`CToolBar`成员方法来操作工具栏，或者你可以从[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)中获得一个引用对象。并且使用它的成员函数来定制工具栏和增加功能。  
  
> [!TIP]
>  如果你花费大量时间在老版本的MFC`CToolBar`实现上，他依然是可被支持的。  参见文章[Using Your Old Toolbars](../mfc/using-your-old-toolbars.md)。  
  
 也可以查看MFC的一般实例[DOCKTOOL](../top/visual-cpp-samples.md)。  
  
##  <a name="_core_the_toolbar_bitmap"></a> 工具栏位图  
 一旦构建，一个`CToolBar`对象会通过导入一个图片的位图来创建一个工具栏图像。  应用程序向导创建一个标准的工具栏位图，你可以使用Visual C\+\+ [工具栏编辑器](../mfc/toolbar-editor.md)来自定义它。  
  
### 您想进一步了解什么？  
  
-   [工具栏基本法则](../mfc/toolbar-fundamentals.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具栏的工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 类  
  
## 请参阅  
 [工具栏](../mfc/toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)