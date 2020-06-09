---
title: 框架窗口类 (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 1c0a1e1e93433e0fbe07c11eb350216173e74d84
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625842"
---
# <a name="frame-window-classes-windows"></a>框架窗口类 (Windows)

框架窗口是应用程序或应用程序的一部分的窗口。 框架窗口通常包含其他窗口，如视图、工具栏和状态栏。 对于 `CMDIFrameWnd` ，它们可能会 `CMDIChildWnd` 间接包含对象。

[CFrameWnd](reference/cframewnd-class.md)<br/>
SDI 应用程序的主框架窗口的基类。 也是其他所有框架窗口类的基类。

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
MDI 应用程序的主框架窗口的基类。

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
MDI 应用程序的文档框架窗口的基类。

[CMiniFrameWnd](reference/cminiframewnd-class.md)<br/>
通常在浮动工具栏周围出现的半高框架窗口。

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
当正在就地编辑服务器文档时，提供视图的框架窗口。

## <a name="related-class"></a>相关类

类 `CMenu` 提供用于访问应用程序菜单的接口。 它适用于在运行时动态操作菜单;例如，根据上下文添加或删除菜单项时。 尽管菜单最常用于框架窗口，但也可用于对话框和其他 nonchild 窗口。

[CMenu](reference/cmenu-class.md)<br/>
封装 `HMENU` 应用程序的菜单栏和弹出菜单的句柄。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
