---
title: "控件条 | Microsoft Docs"
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
  - "CControlBar 类, MFC 控件条"
  - "CDialogBar 类, 控件条"
  - "命令栏, 类型"
  - "控件条 [C++]"
  - "控件条 [C++], 类型"
  - "CStatusBar 类, 控件条"
  - "CToolBar 类, 控件条"
  - "对话栏, 控件条"
  - "MFC, 控件条"
  - "状态栏, 控件条"
  - "工具栏 [C++], 控件条"
ms.assetid: 31831910-3d23-4d70-9e71-03cc02f01ec4
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 控件条
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“控件条”是工具栏、状态栏、对话栏的总称。  MFC中的`CToolBar`，`CStatusBar`，`CDialogBar`，`COleResizeBar`和**CReBar** 类都是从实现了通用功能的类[CControlBar](../mfc/reference/ccontrolbar-class.md)派生而来。  
  
 控件条是显示多行控件的窗口，用来给用户选择，执行命令或者得到程序信息。  控件栏类型包含控件条工具栏和状态栏、对话栏的类型。  
  
-   工具栏，在类 [CToolBar](../mfc/reference/ctoolbar-class.md)中。  
  
-   状态栏，在类 [CStatusBar](../mfc/reference/cstatusbar-class.md)中。  
  
-   对话栏，在类[CDialogBar](../mfc/reference/cdialogbar-class.md)中。  
  
-   Rebars，在类[CReBar](../mfc/reference/crebar-class.md)中。  
  
> [!IMPORTANT]
>  MFC 4.0 版，工具栏、状态栏和工具提示，的实现是通过在 comctl32.dll中使用系统函数实现的而不是像之前那样MFC特定的实现。  在 MFC 6.0 版，添加了也包装了comctl32.dll 功能的**CReBar**类。  
  
 随后是控件条类型的简介。  有关的详细信息，请参见以下链接。  
  
## 控件条  
 控件条通过提供一步、快速指令操作，极大提升了程序的可用性。  `CControlBar` 类提供了所有工具栏、状态栏、对话栏的通用功能。  `CControlBar` 用于提供在控件条的父框架窗口中定位它的功能。  由于一个控件条通常是父框架窗口的子窗口，则其是客户端视图或 MDI 框架窗口视图的“兄妹”。  控件条对象使用父窗口客户端矩形的信息来定位自己。  然后它修改父的其余矩形窗口客户端，以便客户端或 MDI 视图窗口客户填充客户端窗口的其余部分。  
  
> [!NOTE]
>  如果控件条上的按钮没有 **COMMAND** 或 **UPDATE\_COMMAND\_UI** 处理程序，框架会自动禁用按钮。  
  
## 工具栏  
 工具栏是显示执行命令行的位图的按钮控件条。  按工具栏按钮等效于选择菜单项；如果该菜单项具有和工具栏按钮有相同的ID，它就会调用映射到菜单项的相同的处理程序。  可将按钮配置为点击按钮、单选按钮或复选框。  工具栏到框架窗口的顶部对齐，但MFC 工具栏可以“停靠”到其父窗口的任何一边或在迷你框架窗口中浮动。  工具栏也同样可以“浮动”，并且你用鼠标拖动改变其大小。  当用户移到鼠标到工具栏的按钮的工具栏上，其显示工具提示。  工具提示是一个小的简单描述按钮作用的弹出窗口。  
  
> [!NOTE]
>  自 MFC 4.0 版，[CToolBar](../mfc/reference/ctoolbar-class.md) 类使用窗口工具栏公共控件。  `CToolBar` 包含了[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)。  但是较早的工具栏仍然被支持。  参见文章 [工具栏](../mfc/mfc-toolbar-implementation.md)。  
  
## 状态栏  
 状态栏是包含文本输出窗格或“指示器”的控件条。输出窗格通常作为状态指示器，用作消息行。  消息行的示例包括了命令帮助消息行，其简短解释了在最左侧的，由MFC应用向导创建的默认状态栏中的选择菜单或工具条命令。  状态指示示例包括 Scroll Lock、Num Lock 和其他键。  状态栏通常对齐到框架窗口的底部。  请参见 [CStatusBar](../mfc/reference/cstatusbar-class.md) 类和[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)类。  
  
## 对话栏  
 对话栏是一个控制条，基于对话框模板资源，使用无模式对话框的功能。  对话栏可以包含 Windows 、自定义的或 ActiveX 控件。  在对话框中，用户可以在控件之间切换。  对话栏可以对齐到框架窗口的顶部，底部，左部或右部，也能在自己的框架窗口中浮动。  参见[CDialogBar](../mfc/reference/cdialogbar-class.md)类。  
  
## Rebars  
 [rebar](../mfc/using-crebarctrl.md)是提供控件布局、持久性和状态信息的控件条。  rebar 对象可以包含各种其他子窗口，通常各种控件，包括编辑框、工具栏和列表框。  rebar 对象可以在在指定的位图上显示其的子窗口。  其可以自动也可以通过单击和拖动手柄栏来调整大小。  参见[CReBar](../mfc/reference/crebar-class.md)类。  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)