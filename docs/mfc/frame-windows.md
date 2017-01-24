---
title: "框架窗口 | Microsoft Docs"
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
  - "CFrameWnd 类, 框架窗口"
  - "文档框架窗口"
  - "框架窗口 [C++]"
  - "框架窗口 [C++], 关于框架窗口"
  - "MDI [C++], 框架窗口"
  - "MFC [C++], 框架窗口"
  - "单文档界面 (SDI)"
  - "单文档界面 (SDI), 框架窗口"
  - "拆分窗口, 和框架窗口"
  - "视图 [C++], 和框架窗口"
  - "窗口类 [C++], 框架"
  - "窗口 [C++], MDI"
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当应用程序在 Windows 下运行时，用户与文档框架窗口显示的交互。  文档框架窗口具有两个主要组件：帧及其构成的内容。  文档框架窗口可以是 [单文档界面](../mfc/sdi-and-mdi.md) \(SDI\)\) 框架窗口 \(\) 或 [多文档界面 \(MDI\)](../mfc/sdi-and-mdi.md) MDI 子窗口。  窗口管理大部分与框架窗口的用户进行交互：移动和调整大小的窗口，关闭它和最小化和最大化窗体。  可以管理在帧内的内容。  
  
## 框架窗口和视图  
 视图包含的 MFC 框架使用框架窗口。  两个组件 \(帧和内容 \(由 MFC 中的两个不同的类表示和管理。  框架窗口类管理帧，因此，内容视图类管理。  窗口是框架窗口的子级。  与文档中绘制和其他用户交互在视图的工作区，而不是框架窗口的工作区。  框架窗口提供视图。提供可见帧，完成使用标题栏和标准 Windows 控件菜单，如控制按钮最小化和最大化窗口和控件的大小的窗口。  “内容”以包括窗口的工作区，该子窗口 \(视图完全占用。  下图显示了记录视图的框架窗口和试图之间的关系。  
  
 ![框架窗口视图](../mfc/media/vc37fx1.png "vc37FX1")  
框架窗口和视图  
  
## 框架窗口和拆分窗口  
 另一个常见的排列是让框架窗口构成多个视图，通常使用 [拆分窗口](../mfc/multiple-document-types-views-and-frame-windows.md)。  在拆分窗口，框架窗口的工作区由拆分窗口，它们占据又具有多个子窗口，调用窗格，该视图。  
  
### 您想进一步了解什么？  
 **通用框架窗口主题**  
  
-   [窗口对象](../mfc/window-objects.md)  
  
-   [框架窗口类](../mfc/frame-window-classes.md)  
  
-   [应用程序向导创建的框架窗口类](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架窗口样式](../mfc/frame-window-styles-cpp.md)  
  
-   [框架窗口的作用](../mfc/what-frame-windows-do.md)  
  
 **在使用框架窗口的主题**  
  
-   [使用框架窗口](../mfc/using-frame-windows.md)  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
-   [销毁框架窗口](../mfc/destroying-frame-windows.md)  
  
-   [管理 MDI 子窗口](../mfc/managing-mdi-child-windows.md)  
  
-   在包含多个视图的框架窗口中[管理当前的视图](../mfc/managing-the-current-view.md)  
  
-   [托管、控件条菜单和快捷键共享 \(帧窗口空间中的其他对象\)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **特定框架窗口功能的主题**  
  
-   从文件管理器或文件管理器的[拖放文件](../mfc/dragging-and-dropping-files-in-a-frame-window.md) 到框架窗口中  
  
-   [响应动态数据交换 \(DDE\)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [Semimodal 状态：上下文相关的 Windows 帮助 \(安排其他窗口操作\)](../mfc/orchestrating-other-window-actions.md)  
  
-   [Semimodal 状态：打印和打印预览 \(安排其他窗口操作\)](../mfc/orchestrating-other-window-actions.md)  
  
 **在其他窗口的主题**  
  
-   [使用视图](../mfc/using-views.md)  
  
-   [对话框](../mfc/dialog-boxes.md)  
  
-   [控件](../mfc/controls-mfc.md)  
  
## 请参阅  
 [窗口](../mfc/windows.md)