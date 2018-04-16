---
title: "框架窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame widows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 14dabd345f47b064f78a4e9a3dede834bddeb9d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="frame-windows"></a>框架窗口
应用程序运行时在 Windows 下，在用户交互的文档框架窗口中显示。 文档框架窗口包含两个主要组件： 框架和框架的内容。 文档框架窗口可以是[单文档界面](../mfc/sdi-and-mdi.md)(SDI) 框架窗口或[多文档界面](../mfc/sdi-and-mdi.md)(MDI) 子窗口。 Windows 管理大部分与框架窗口的用户的交互： 移动和调整窗口的大小、 关闭它，并将降至最低和最大化。 管理在框架内的内容。  
  
## <a name="frame-windows-and-views"></a>框架窗口和视图  
 MFC 框架将使用框架窗口包含视图。 两个组件-框架和内容-表示，并由 MFC 中的两个不同类。 框架窗口类管理框架，和视图类管理内容。 视图窗口是框架窗口的子级。 绘制和其他与文档的用户交互发生在视图的客户端区域中，不框架窗口的工作区。 框架窗口提供的视图，完成，但标题栏和标准窗口控件控件菜单中，按钮，以最小化和最大化窗口，如可见边框，并控制调整窗口的大小。 "内容"包含窗口的工作区，其中完全由子窗口占用 — 视图。 下图显示框架窗口和视图之间的关系。  
  
 ![框架窗口视图](../mfc/media/vc37fx1.gif "vc37fx1")  
框架窗口和视图  
  
## <a name="frame-windows-and-splitter-windows"></a>框架窗口和拆分窗口  
 另一个常见的排列方式是框架窗口框架多个视图，通常使用[拆分窗口](../mfc/multiple-document-types-views-and-frame-windows.md)。 在拆分器窗口中，框架窗口的工作区由拆分窗口中，而后者拥有多个子窗口，调用窗格，是视图，它们占用。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
 **常规框架窗口主题**  
  
-   [窗口对象](../mfc/window-objects.md)  
  
-   [框架窗口类](../mfc/frame-window-classes.md)  
  
-   [应用程序向导创建的框架窗口类](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架窗口样式](../mfc/frame-window-styles-cpp.md)  
  
-   [框架窗口的作用](../mfc/what-frame-windows-do.md)  
  
 **使用框架窗口的主题**  
  
-   [使用框架窗口](../mfc/using-frame-windows.md)  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
-   [销毁框架窗口](../mfc/destroying-frame-windows.md)  
  
-   [管理 MDI 子窗口](../mfc/managing-mdi-child-windows.md)  
  
-   [管理当前视图](../mfc/managing-the-current-view.md)框架窗口包含多个视图中  
  
-   [管理菜单、 控件条和快捷键 （其他对象的共享框架窗口的空间）](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **有关特殊框架窗口功能的主题**  
  
-   [拖放文件](../mfc/dragging-and-dropping-files-in-a-frame-window.md)从文件资源管理器或文件管理器到框架窗口  
  
-   [响应动态数据交换 (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [半模式状态： 上下文相关 Windows 帮助 （协调其他窗口操作）](../mfc/orchestrating-other-window-actions.md)  
  
-   [半模式状态: （协调其他窗口操作） 的打印和打印预览](../mfc/orchestrating-other-window-actions.md)  
  
 **其他类型的 Windows 上的主题**  
  
-   [使用视图](../mfc/using-views.md)  
  
-   [对话框](../mfc/dialog-boxes.md)  
  
-   [控件](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>请参阅  
 [Windows](../mfc/windows.md)

