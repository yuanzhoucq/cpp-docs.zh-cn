---
title: "框架窗口的作用 | Microsoft Docs"
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
  - "框架窗口, 关于框架窗口"
  - "框架窗口, 任务"
  - "MFC, 框架窗口"
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 框架窗口的作用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除了简单地配置视图外，框架窗口负责涉及视图和应用程序框架协调的许多任务。  [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 和从[CFrameWnd](../mfc/reference/cframewnd-class.md)继承的[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) ，它们具有自己添加的 `CFrameWnd` 功能以及一些新功能。  子窗口示例包括视图、控件，例如：按钮、列表框、控件条，包含工具栏、状态栏、对话栏。  
  
 框架窗口负责管理其子窗口布局。  在 MFC 框架中，框架窗口确定任何控件条、视图及其他子窗口在其工作区中的位置。  
  
 框架窗口还寄命令给其视图，并响应从控制窗口的通知消息。  
  
## 您想进一步了解什么？  
  
-   [控件条 \(如何适应框架窗口\)](../mfc/control-bars.md)  
  
-   [托管菜单、控件条和快捷键 \(如何适应框架窗口\)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [命令传送 \(从框架窗口到其视图和其他命令目标\)](../mfc/command-routing.md)  
  
-   [文档\/视图体系结构](../mfc/document-view-architecture.md)  
  
-   [控件条](../mfc/control-bars.md)  
  
-   [控件](../mfc/controls-mfc.md)  
  
## 请参阅  
 [框架窗口](../mfc/frame-windows.md)