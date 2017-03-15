---
title: "更新状态栏窗格的文本 | Microsoft Docs"
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
  - "CStatusBar 类, 更新"
  - "ON_UPDATE_COMMAND_UI 宏"
  - "窗格, 状态栏"
  - "SetText 方法"
  - "状态栏, 更新"
  - "文本, 状态栏"
  - "更新用户界面对象"
  - "用户界面对象, 更新"
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 更新状态栏窗格的文本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何更改出现在 MFC 状态栏窗格的文本。  状态栏 \- 一个 [CStatusBar](../mfc/reference/cstatusbar-class.md) 类的窗口对象 \- 包含若干“窗格”。每个窗格为状态栏中用于显示信息的矩形区域。  例如，许多应用程序显示了 CAPS LOCK, NUM LOCK，并在最右侧窗格显示了其它的键的状态。  应用程序通常还在最左侧窗格显示信息文本（窗格 0），有时称作“消息窗格”。例如，默认的 MFC 状态栏使用消息窗格显示解释当前选择的菜单或工具栏按钮项的字符串。  在 [状态栏](../mfc/status-bar-implementation-in-mfc.md) 中的图形演示了从应用程序向导创建的 MFC 应用程序的状态栏。  
  
 默认情况下，在创建窗格时，MFC 不启用 `CStatusBar` 窗格。  若要激活窗格，必须为状态栏上的每个窗格使用 `ON_UPDATE_COMMAND_UI` 宏并更新窗格。  由于窗格不会发送 **WM\_COMMAND** 信息 \(不类似于工具栏按钮\)，必须手动键入代码。  
  
 例如，假设一窗格具有 `ID_INDICATOR_PAGE` 作为命令标识符，并在该文档包含当前页的页码。  下面的过程中描述如何在状态栏中创建新窗格。  
  
### 制作新窗格  
  
1.  定义窗格的命令 ID.  
  
     单击**“视图”**菜单上的**“资源视图”**。  右击项目资源，然后单击**“资源标识”**。  在资源符号”对话框中选择 `“New"`。  键入命令 ID 名称：例如，`ID_INDICATOR_PAGE`。  为 ID 指定值或者接受资源符号对话框的建议值。  例如，对于 `ID_INDICATOR_PAGE`，请接受默认值。  关闭资源符号对话框。  
  
2.  定义一默认字符串显示在窗格。  
  
     打开资源视图，在列出的应用程序的资源类型的窗口中双击 **字符串表**。  打开 **字符串表** 编辑器，从 **插入** 菜单中选择 **新建字符串**。  在字符串属性窗口，请选择窗格的命令 ID \(例如，`ID_INDICATOR_PAGE`\) 并键入一个默认的字符串值，如“Page”。  关闭字符串编辑器。\(您需要默认字符串避免编译器错误。\)  
  
3.  将窗格添加到 **indicators** 数组。  
  
     在文件 MAINFRM.CPP，找到 **indicators** 数组。  此数组从左到右的顺序列出了所有的状态栏指示符的命令 ID 。  在数组的相应合适点，输入窗格的命令 ID，如此处所示为 `ID_INDICATOR_PAGE`:  
  
     [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_1.cpp)]  
  
 在窗格显示文本建议的方法是在更新处理函数中为窗格调用类 `CCmdUI` 的 **SetText** 成员函数。  例如，您可能想要设置包含当前页码的 `m_nPage` 整数变量和使用 **SetText** 设置窗格的文本为该数字的字符串版本 。  
  
> [!NOTE]
>  建议使用 **SetText** 方法。  在稍微低级的层次中执行此任务可以通过调用 `CStatusBar` 成员函数 `SetPaneText`。  尽管如此，您仍需更新处理程序。  没有窗格的处理程序，MFC 自动禁用窗格中，清除其内容。  
  
 以下过程显示如何使用更新处理程序函数在窗格中显示文本。  
  
#### 使窗格显示文本  
  
1.  为命令添加命令更新处理程序。  
  
     请手动添加处理程序的原型，如此处所示为 `ID_INDICATOR_PAGE` \(在 MAINFRM.H 中\):  
  
     [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_2.h)]  
  
2.  在适当的 .CPP 文件中，添加处理程序的定义，如此处所示为 `ID_INDICATOR_PAGE` \(在 MAINFRM.CPP\):  
  
     [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_3.cpp)]  
  
     此处理程序最后三行是显示文本的代码。  
  
3.  在适当的消息映射中，添加 `ON_UPDATE_COMMAND_UI` 宏，如此处所示为 `ID_INDICATOR_PAGE` \(在 MAINFRM.CPP\):  
  
     [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/CPP/updating-the-text-of-a-status-bar-pane_4.cpp)]  
  
 一旦定义 `m_nPage` 成员变量的值 \( `CMainFrame`类\)，此技术会导致在空闲处理时在窗格中显示页数，类似应用程序更新其他指示符的行为。  如果 `m_nPage` 更改，在下一个空循环中显示更改。  
  
### 您想进一步了解什么？  
  
-   [更新用户界面对象 \(当程序条件更改时如何更新工具栏按钮和菜单项\)](../mfc/how-to-update-user-interface-objects.md)  
  
## 请参阅  
 [MFC 中的状态栏实现](../mfc/status-bar-implementation-in-mfc.md)   
 [CStatusBar Class](../mfc/reference/cstatusbar-class.md)