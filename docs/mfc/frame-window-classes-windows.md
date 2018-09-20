---
title: 框架窗口类 (Windows) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.frame
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be63dd57900bbbe1691e132cd880d3da60caf4e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431939"
---
# <a name="frame-window-classes-windows"></a>框架窗口类 (Windows)

框架窗口是窗口框架应用程序或应用程序的一部分。 框架窗口通常包含其他窗口，如视图、 工具栏和状态栏。 情况下`CMDIFrameWnd`，它们可能包含`CMDIChildWnd`间接对象。

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
SDI 应用程序的主框架窗口的基类。 此外用于其他框架窗口类基本的类。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
MDI 应用程序的主框架窗口的基类。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
MDI 应用程序的文档框架窗口的基类。

[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)<br/>
通常在浮动工具条周围出现一个半高框架窗口。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
正在就地编辑服务器文档时，应提供视图框架窗口。

## <a name="related-class"></a>相关的类

类`CMenu`提供了一个用来访问应用程序的菜单接口。 它可用于在运行时; 动态操作菜单例如，添加或删除菜单项时根据上下文。 尽管菜单最常与框架窗口，但它们还可使用对话框和其他非子窗口。

[CMenu](../mfc/reference/cmenu-class.md)<br/>
封装`HMENU`到应用程序的菜单栏和弹出菜单的句柄。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

