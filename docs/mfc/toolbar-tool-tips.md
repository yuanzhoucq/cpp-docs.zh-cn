---
title: "工具栏工具提示 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBRS_FLYBY 常量"
  - "CBRS_TOOLTIPS 常量"
  - "越过状态栏更新"
  - "状态栏, 工具提示"
  - "工具提示 [C++]"
  - "工具提示 [C++], 激活"
  - "工具提示 [C++], 添加文本"
  - "更新"
  - "更新, 状态栏消息"
  - "更新状态栏消息"
ms.assetid: d1696305-b604-4fad-9f09-638878371412
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 工具栏工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

工具提示是存在工具栏按钮的作用的简短说明的微小的弹出窗口，在一段时确定鼠标移到按钮。  当您创建一个工具栏。应用程序向导"应用程序时，工具提示提供了支持。  本文说明两个应用程序向导创建的工具提示以及支持如何将工具提示添加对其他程序。  
  
 本文包含：  
  
-   [活动工具提示](#_core_activating_tool_tips)  
  
-   [定点飞越更新状态栏](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> 活动工具提示  
 若要激活应用程序的工具提示，必须执行两项操作：  
  
-   将 `CBRS_TOOLTIPS` 样式。为 `dwStyle` 参数 \(如 **WS\_CHILD**、**WS\_VISIBLE**和 **CBRS\_** \) 传递其他样式的其他样式的函数 [CToolBar::Create](../Topic/CToolBar::Create.md) 中或 [SetBarStyle](../Topic/CControlBar::SetBarStyle.md)。  
  
-   如以下过程所述，请追加工具栏提示文本，由换行符分隔字符 \(“\\ n”\)，指向包含命令行提示工具栏命令的字符串资源。  字符串资源共享工具栏按钮的 ID。  
  
#### 添加工具提示文本  
  
1.  当您编辑在工具栏编辑器中的工具栏，请打开特定按钮的 **Toolbar Button Properties** 窗口。  
  
2.  在 **提示** 框中，指定要显示该按钮的工具提示的文本。  
  
> [!NOTE]
>  设置文本编辑器为工具栏的按钮属性替换上一过程，您必须打开并编辑字符串资源。  
  
 如果启用了工具提示的控件条对此中的子控件，将显示控件条每个控件的工具提示。控件条，只要满足以下条件：  
  
-   控件的 ID 不是" 1。  
  
-   具有 ID 的字符串表项并在资源文件的子控件一样具有工具提示字符串。  
  
##  <a name="_core_fly_by_status_bar_updates"></a> 定点飞越更新状态栏  
 功能与工具提示是“状态栏”飞越定点更新。  默认情况下，自，当按钮被激活时，状态栏上的消息只介绍特定工具栏按钮。  通过包含 `CBRS_FLYBY` 中样式列表传递给 `CToolBar::Create`，可让这些消息的更新，当鼠标光标传递此工具栏，而实际激活按钮。  
  
### 您想进一步了解什么？  
  
-   [MFC 工具栏实现 \(在工具栏的概述信息\)](../mfc/mfc-toolbar-implementation.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 类  
  
-   [与工具栏控件。](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用以前的工具栏](../mfc/using-your-old-toolbars.md)  
  
## 请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)