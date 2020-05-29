---
title: 控件条类
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: a050c5d2f7396324c2c380a03fc28e01ab992208
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440966"
---
# <a name="control-bar-classes"></a>控件条类

控件条附加到框架窗口中。 它们包含按钮、状态窗格或对话框模板。 自由浮动控制条（也称为工具调色板）是通过将它们附加到[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)对象来实现的。

## <a name="framework-control-bars"></a>框架控件栏

这些控制条是 MFC 框架的有机组成部分。 它们比 Windows 控件栏更易于使用且功能更强大，因为它们与框架集成在一起。 大多数 MFC 应用程序都使用这些控制条，而不是 Windows 控件条。

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
此部分中列出的 MFC 控件条的基类。 控件条是与框架窗口边缘对齐的窗口。 控件条包含基于 `HWND`的子控件或不基于 `HWND`的控件（如工具栏按钮）。

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
基于对话框模板的控件条。

[CReBar](../mfc/reference/crebar-class.md)<br/>
支持工具栏，该工具栏可包含控件形式的其他子窗口。

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
包含不基于 `HWND`的位图命令按钮的工具栏控件窗口。 大多数 MFC 应用程序都使用此类，而不是 `CToolBarCtrl`。

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
状态栏控件窗口的基类。 大多数 MFC 应用程序都使用此类，而不是 `CStatusBarCtrl`。

## <a name="windows-control-bars"></a>Windows 控件栏

这些控件条是对应的 Windows 控件的精简包装器。 因为它们不与框架集成，所以比以前列出的控制条更难使用。 大多数 MFC 应用程序都使用前面列出的控制条。

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
实现 `CRebar` 对象的内部控件。

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
水平窗口，通常分为窗格，应用程序可以在其中显示状态信息。

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具栏公共控件的功能。

## <a name="related-classes"></a>相关类

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
一个小的弹出窗口，显示说明应用程序中工具用途的单行文本。

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
处理控件条的停靠状态数据的持久存储。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
