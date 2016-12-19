---
title: "控件条类 | Microsoft Docs"
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
  - "vc.classes.control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件条, 类"
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 控件条类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控件条附加到框架窗口。  它们包含按钮、状态窗格或模板。  自由浮动控件条，还调用工具调色板，通过附加类实现到 [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md) 对象。  
  
## Framework 控件条  
 这些控件条是 MFC 框架的一个组成部分。  因为它们已集成到框架，它们可以比 Windows 控件条更易于使用、功能更强大。  大多数 MFC 应用程序使用这些控件条而不是 Window 控件条。  
  
 [CControlBar](../mfc/reference/ccontrolbar-class.md)  
 本节列出 MFC 控件条的基类。  控制条是对齐到框架窗口边缘的窗口。  控件条包含基于 `HWND`的子控件或不基于 `HWND`的控件，如工具栏按钮。  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 基于对话框模板的控件条。  
  
 [CReBar](../mfc/reference/crebar-class.md)  
 在控件窗体支持包含附加子窗口的工具条。  
  
 [CToolBar](../mfc/reference/ctoolbar-class.md)  
 工具栏控件窗口包含位图命令按钮，该按钮不基于 `HWND`。  大多数 MFC 应用程序使用此类而不是 `CToolBarCtrl`。  
  
 [CStatusBar](../mfc/reference/cstatusbar-class.md)  
 状态栏控件窗口的基类。  大多数 MFC 应用程序使用此类而不是 `CStatusBarCtrl`。  
  
## Windows 控件条  
 这些控件条是相应 Windows 控件的简单包装器。  因为它们没有用框架集成，它们可以比以前列出的控件条更难使用。  大多数 MFC 应用程序使用前面列出的控件条。  
  
 [CReBarCtrl（rebar 一种单元属性）](../mfc/reference/crebarctrl-class.md)  
 实现 `CRebar` 对象的内部控制。  
  
 [CStatusBarCtrl（C状态栏按Ctrl）](../mfc/reference/cstatusbarctrl-class.md)  
 水平窗口通常分为窗格，应用程序可在其中显示状态信息。  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具栏公共控件的功能。  
  
## 相关类  
 [CToolTipCtrl（C工具提示按Ctrl）](../mfc/reference/ctooltipctrl-class.md)  
 在应用程序中，小型弹出窗口显示描述工具用途的单行文本。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 句柄永久性存储控件条停靠状态数据。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)