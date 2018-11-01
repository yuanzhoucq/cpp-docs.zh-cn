---
title: 框架窗口
ms.date: 11/04/2016
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame windows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
ms.openlocfilehash: 09db7bab392778297f17c14f7bb807f91af4d896
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619929"
---
# <a name="frame-windows"></a>框架窗口

当应用程序在 Windows 下运行时，用户与文档框架窗口中显示。 文档框架窗口有两个主要组件： 帧和其帧的内容。 文档框架窗口可以是[单文档界面](../mfc/sdi-and-mdi.md)(SDI) 框架窗口或[多文档界面](../mfc/sdi-and-mdi.md)(MDI) 子窗口。 Windows 管理大多数用户的交互与框架窗口： 移动和调整窗口的大小、 关闭它，并最小化和最大化它。 管理在帧内的内容。

## <a name="frame-windows-and-views"></a>帧 Windows 和视图

MFC 框架使用框架窗口来包含视图。 两个组件-框架和内容 — 表示，并由 MFC 中的两个不同的类。 框架窗口类管理框架和视图类管理内容。 视图窗口是框架窗口的子级。 绘制和其他用户与文档交互发生在该视图的客户端区域中，不是框架窗口的工作区。 框架窗口提供了可见边框的视图，包含标题栏和标准窗口控件，如控件菜单中，按钮来最小化和最大化窗口，并控制调整窗口的大小。 完全占用的子窗口的窗口的客户端区域包含"内容"，该视图。 下图显示了一个框架窗口和视图之间的关系。

![框架窗口视图](../mfc/media/vc37fx1.gif "vc37fx1")框架窗口和视图

## <a name="frame-windows-and-splitter-windows"></a>帧 Windows 和拆分器 Windows

框架窗口框架通常使用多个视图是另一个常见的排列方式[拆分器窗口](../mfc/multiple-document-types-views-and-frame-windows.md)。 在拆分器窗口中，框架窗口的工作区都被子拆分窗口中，随后具有多个子窗口，调用窗格是视图。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

**常规框架窗口主题**

- [窗口对象](../mfc/window-objects.md)

- [框架窗口类](../mfc/frame-window-classes.md)

- [应用程序向导创建的框架窗口类](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [框架窗口样式](../mfc/frame-window-styles-cpp.md)

- [框架窗口的作用](../mfc/what-frame-windows-do.md)

**有关使用帧 Windows 主题**

- [使用框架窗口](../mfc/using-frame-windows.md)

- [创建文档框架窗口](../mfc/creating-document-frame-windows.md)

- [销毁框架窗口](../mfc/destroying-frame-windows.md)

- [管理 MDI 子窗口](../mfc/managing-mdi-child-windows.md)

- [管理当前视图](../mfc/managing-the-current-view.md)框架窗口包含多个视图中

- [管理菜单、 控件条和快捷键 （共享框架窗口的空间其他对象）](../mfc/managing-menus-control-bars-and-accelerators.md)

**有关特殊框架窗口功能的主题**

- [拖放文件](../mfc/dragging-and-dropping-files-in-a-frame-window.md)从文件资源管理器或文件管理器到框架窗口

- [响应动态数据交换 (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)

- [半模式状态： 上下文相关 Windows 帮助 （协调其他窗口操作）](../mfc/orchestrating-other-window-actions.md)

- [半模式状态： 打印和打印预览 （协调其他窗口操作）](../mfc/orchestrating-other-window-actions.md)

**在其他类型的 Windows 上的主题**

- [使用视图](../mfc/using-views.md)

- [对话框](../mfc/dialog-boxes.md)

- [控件](../mfc/controls-mfc.md)

## <a name="see-also"></a>请参阅

[Windows](../mfc/windows.md)

