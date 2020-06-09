---
title: 框架窗口
ms.date: 11/19/2018
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
ms.openlocfilehash: 39c0b4b866fa123d8bcae639342c925570d96e1b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625827"
---
# <a name="frame-windows"></a>框架窗口

当应用程序在 Windows 下运行时，用户与框架窗口中显示的文档交互。 文档框架窗口具有两个主要组件：框架和它所框架的内容。 文档框架窗口可以是[单文档界面](sdi-and-mdi.md)（SDI）框架窗口，也可以是[多文档界面](sdi-and-mdi.md)（MDI）子窗口。 Windows 管理大多数用户与框架窗口的交互：移动窗口并调整窗口大小，将其关闭，然后最小化和最大化。 您可以管理框架内的内容。

## <a name="frame-windows-and-views"></a>框架窗口和视图

MFC 框架使用框架窗口来包含视图。 两个组件（框架和内容）由 MFC 中的两个不同类表示和管理。 框架窗口类管理框架，视图类管理内容。 "视图" 窗口是框架窗口的子窗口。 绘图和其他用户与文档的交互发生在视图的工作区中，而不是框架窗口的工作区中。 框架窗口在视图周围提供一个可视框架，并使用标题栏和标准窗口控件（如 "控制" 菜单）、"最小化" 和 "最大化" 窗口的按钮以及用于调整窗口大小的控件。 "内容" 由窗口的工作区（它由子窗口完全占用）（视图）组成。 下图显示框架窗口和视图之间的关系。

![框架窗口视图](../mfc/media/vc37fx1.gif "框架窗口视图") <br/>
框架窗口和视图

## <a name="frame-windows-and-splitter-windows"></a>框架窗口和拆分窗口

另一种常见的布局是，框架窗口通常使用[拆分窗口](multiple-document-types-views-and-frame-windows.md)来框架多个视图。 在拆分窗口中，框架窗口的工作区由拆分器窗口占用，拆分器窗口又具有多个称为 "窗格" 的子窗口。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

**常规框架窗口主题**

- [窗口对象](window-objects.md)

- [框架窗口类](frame-window-classes.md)

- [应用程序向导创建的框架窗口类](frame-window-classes-created-by-the-application-wizard.md)

- [框架窗口样式](frame-window-styles-cpp.md)

- [框架窗口的作用](what-frame-windows-do.md)

**有关使用框架窗口的主题**

- [使用框架窗口](using-frame-windows.md)

- [创建文档框架窗口](creating-document-frame-windows.md)

- [销毁框架窗口](destroying-frame-windows.md)

- [管理 MDI 子窗口](managing-mdi-child-windows.md)

- 在包含多个视图的框架窗口中[管理当前视图](managing-the-current-view.md)

- [管理菜单、控件条和快捷键（共享框架窗口空间的其他对象）](managing-menus-control-bars-and-accelerators.md)

**有关特殊框架窗口功能的主题**

- 将文件从文件资源管理器或文件管理器[拖放](dragging-and-dropping-files-in-a-frame-window.md)到框架窗口

- [响应动态数据交换（DDE）](responding-to-dynamic-data-exchange-dde.md)

- [半模式状态：上下文相关的 Windows 帮助（协调其他窗口操作）](orchestrating-other-window-actions.md)

- [半模式状态：打印和打印预览（协调其他窗口操作）](orchestrating-other-window-actions.md)

**有关其他类型的窗口的主题**

- [使用视图](using-views.md)

- [对话框](dialog-boxes.md)

- [控件](controls-mfc.md)

## <a name="see-also"></a>另请参阅

[Windows](windows.md)
