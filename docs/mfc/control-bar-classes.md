---
title: 控件条类
ms.date: 11/04/2016
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: f89770683edb1f4268b4f19adb74e5c08aa5f109
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620516"
---
# <a name="control-bar-classes"></a>控件条类

控件条附加到框架窗口中。 它们包含按钮、状态窗格或对话框模板。 自由浮动控制条（也称为工具调色板）是通过将它们附加到[CMiniFrameWnd](reference/cminiframewnd-class.md)对象来实现的。

## <a name="framework-control-bars"></a>框架控件栏

这些控制条是 MFC 框架的有机组成部分。 它们比 Windows 控件栏更易于使用且功能更强大，因为它们与框架集成在一起。 大多数 MFC 应用程序都使用这些控制条，而不是 Windows 控件条。

[CControlBar](reference/ccontrolbar-class.md)<br/>
此部分中列出的 MFC 控件条的基类。 控件条是与框架窗口边缘对齐的窗口。 控件条包含基于的 `HWND` 子控件或不基于的控件（ `HWND` 如工具栏按钮）。

[CDialogBar](reference/cdialogbar-class.md)<br/>
基于对话框模板的控件条。

[CReBar](reference/crebar-class.md)<br/>
支持工具栏，该工具栏可包含控件形式的其他子窗口。

[CToolBar](reference/ctoolbar-class.md)<br/>
包含不基于的位图命令按钮的工具栏控件窗口 `HWND` 。 大多数 MFC 应用程序都使用此类，而不是 `CToolBarCtrl` 。

[CStatusBar](reference/cstatusbar-class.md)<br/>
状态栏控件窗口的基类。 大多数 MFC 应用程序都使用此类，而不是 `CStatusBarCtrl` 。

## <a name="windows-control-bars"></a>Windows 控件栏

这些控件条是对应的 Windows 控件的精简包装器。 因为它们不与框架集成，所以比以前列出的控制条更难使用。 大多数 MFC 应用程序都使用前面列出的控制条。

[CRebarCtrl](reference/crebarctrl-class.md)<br/>
实现对象的内部控件 `CRebar` 。

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
水平窗口，通常分为窗格，应用程序可以在其中显示状态信息。

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具栏公共控件的功能。

## <a name="related-classes"></a>相关类

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
一个小的弹出窗口，显示说明应用程序中工具用途的单行文本。

[CDockState](reference/cdockstate-class.md)<br/>
处理控件条的停靠状态数据的持久存储。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
