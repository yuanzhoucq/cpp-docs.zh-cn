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
ms.openlocfilehash: 46da8fc0cb98406bdf97285d7c6f824afd61c4bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392812"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>应用程序向导创建的框架窗口类

当你创建新的 MFC 项目从**新的项目**对话框中，除了应用程序、 文档和视图类，应用程序向导创建应用程序的主框架窗口的派生的框架窗口类。 默认情况下，此类名为 `CMainFrame`，包含此类的文件名为 MAINFRM.H 和 MAINFRM.CPP。

如果你的应用程序是 SDI，你`CMainFrame`类派生自类[CFrameWnd](../mfc/reference/cframewnd-class.md)。

如果应用程序是 MDI，`CMainFrame`派生自类[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)。 在此情况下，`CMainFrame` 实现保留菜单、工具栏和状态栏的主框架。 应用程序向导不会为您派生新的文档框架窗口类。 相反，它使用中的默认实现[CMDIChildWnd 类](../mfc/reference/cmdichildwnd-class.md)。 MFC 框架会创建一个子窗口以包含应用程序要求的每个视图（可以是 `CScrollView`、`CEditView`、`CTreeView`、`CListView` 等类型）。 如果需要自定义文档框架窗口，可以创建新的文档框架窗口类 (请参阅[添加类](../ide/adding-a-class-visual-cpp.md))。

如果您选择支持工具栏，此类还具有类型的成员变量[CToolBar](../mfc/reference/ctoolbar-class.md)并[CStatusBar](../mfc/reference/cstatusbar-class.md)和一个`OnCreate`消息处理程序函数来初始化两个[控件条](../mfc/control-bars.md)。

这些框架窗口类在创建之后便可以工作，但要增强其功能，您必须添加成员变量和成员函数。 您可能还需要让您的窗口类处理其他 Windows 消息。 有关详细信息，请参阅[更改 MFC 创建的窗口样式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>请参阅

[框架窗口类](../mfc/frame-window-classes.md)<br/>
[MFC 程序或控件的源文件和头文件](../build/reference/mfc-program-or-control-source-and-header-files.md)

