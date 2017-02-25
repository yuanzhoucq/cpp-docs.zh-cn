---
title: "应用程序向导创建的框架窗口类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CMainFrame"
  - "CMainFrame::PreCreateWindow"
  - "CMainFrame.PreCreateWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序向导 [C++], 框架窗口类创建者"
  - "CFrameWnd 类, 框架窗口"
  - "类 [C++], 框架窗口"
  - "CMainFrame 类"
  - "CMDIChildWnd 类, 框架窗口"
  - "CMDIFrameWnd 类, 框架窗口"
  - "框架窗口类, 由应用程序向导创建"
  - "窗口类"
  - "窗口类, 框架"
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# 应用程序向导创建的框架窗口类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了应用程序、文档和视图类之外时，可以使用 [应用程序向导](../ide/creating-desktop-projects-by-using-application-wizards.md) 创建主干应用程序，否则，应用程序向导创建应用程序主框架窗口的派生的框架窗口类。  类默认情况下，调用 `CMainFrame`，并包含测试的文件名为 MAINFRM.H 和 MAINFRM.CPP。  
  
 如果应用程序是 SDI，`CMainFrame` 类是从类派生。[CFrameWnd](../mfc/reference/cframewnd-class.md)  
  
 如果应用程序比较 MDI，`CMainFrame` 从类派生。[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 在 `CMainFrame` 实现主框架，持有菜单、工具栏和状态栏。  应用程序向导不派生您的新文档框架窗口类。  相反，在 [CMDIChildWnd 类](../mfc/reference/cmdichildwnd-class.md)使用默认实现。  MFC 框架创建子窗口包含可为 `CScrollView`类型，`CEditView`，`CTreeView`，`CListView`的每视图 \(，等\) 应用程序要求。  如果需要自定义文档框架窗口关联，可以创建一个新的文档框架窗口类 \(请参见 [添加类](../ide/adding-a-class-visual-cpp.md)\)。  
  
 如果选择支持工具栏，类还具有和 [CStatusBar](../mfc/reference/cstatusbar-class.md) [CToolBar](../mfc/reference/ctoolbar-class.md) 初始化类型的成员变量和 `OnCreate` 消息处理函数的两 [控件条](../mfc/control-bars.md)。  
  
 这些框架窗口类按创建，但是，引发其功能，必须将变量成员和成员函数。  可能还需要用于排列窗口的其他类处理窗口消息。  有关更多信息，请参见 [更改 MFC 创建窗口的样式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。  
  
## 请参阅  
 [框架窗口类](../mfc/frame-window-classes.md)   
 [MFC 程序或控件的源文件和头文件](../ide/mfc-program-or-control-source-and-header-files.md)