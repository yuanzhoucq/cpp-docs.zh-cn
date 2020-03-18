---
title: 框架窗口类（体系结构）
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: e3ae432c1adc881a5c67d6a6c292dc1f6a583ab3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441250"
---
# <a name="frame-window-classes-architecture"></a>框架窗口类（体系结构）

在文档/视图体系结构中，框架窗口是包含 "视图" 窗口的窗口。 它们还支持附加控件条。

在多文档界面（MDI）应用程序中，主窗口派生自 `CMDIFrameWnd`。 它间接包含文档的框架，这些框架是 `CMDIChildWnd` 对象。 `CMDIChildWnd` 对象又包含文档的视图。

在单文档界面（SDI）应用程序中，从 `CFrameWnd`派生的主窗口包含当前文档的视图。

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
SDI 应用程序的主框架窗口的基类。 也是其他所有框架窗口类的基类。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
MDI 应用程序的主框架窗口的基类。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
MDI 应用程序的文档框架窗口的基类。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
当正在就地编辑服务器文档时，提供视图的框架窗口。

## <a name="see-also"></a>另请参阅

[类概述](../mfc/class-library-overview.md)
