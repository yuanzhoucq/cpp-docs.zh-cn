---
title: 应用程序向导创建的框架窗口类
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
ms.openlocfilehash: c17ba2b6dd79e8e62baa29bba403c136d16a0d95
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077537"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>应用程序向导创建的框架窗口类

如果要从 "**新建项目**" 对话框创建新的 MFC 项目，则除了应用程序、文档和视图类之外，应用程序向导还会为应用程序的主框架窗口创建一个派生的框架窗口类。 默认情况下，此类名为 `CMainFrame`，包含此类的文件名为 MAINFRM.H 和 MAINFRM.CPP。

如果你的应用程序为 SDI，则 `CMainFrame` 类派生自类[CFrameWnd](../mfc/reference/cframewnd-class.md)。

如果你的应用程序为 MDI，则 `CMainFrame` 派生自类[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)。 在此情况下，`CMainFrame` 实现保留菜单、工具栏和状态栏的主框架。 应用程序向导不会为您派生新的文档框架窗口类。 相反，它使用[CMDIChildWnd 类](../mfc/reference/cmdichildwnd-class.md)中的默认实现。 MFC 框架会创建一个子窗口以包含应用程序要求的每个视图（可以是 `CScrollView`、`CEditView`、`CTreeView`、`CListView` 等类型）。 如果需要自定义文档框架窗口，可以创建新的文档框架窗口类（请参阅[添加类](../ide/adding-a-class-visual-cpp.md)）。

如果选择支持工具栏，则类还具有类型为[CToolBar](../mfc/reference/ctoolbar-class.md)和[CStatusBar](../mfc/reference/cstatusbar-class.md)的成员变量，以及用于初始化两个[控件栏](../mfc/control-bars.md)的 `OnCreate` 消息处理程序函数。

这些框架窗口类在创建之后便可以工作，但要增强其功能，您必须添加成员变量和成员函数。 您可能还需要让您的窗口类处理其他 Windows 消息。 有关详细信息，请参阅[更改 MFC 创建的窗口的样式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>另请参阅

[框架窗口类](../mfc/frame-window-classes.md)<br/>
[MFC 程序或控件的源文件和头文件](../build/reference/mfc-program-or-control-source-and-header-files.md)
