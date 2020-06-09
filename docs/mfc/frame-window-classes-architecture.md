---
title: 框架窗口类（体系结构）
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: 483112d197b7c7211989ecda8b774deb9f30d49e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624598"
---
# <a name="frame-window-classes-architecture"></a>框架窗口类（体系结构）

在文档/视图体系结构中，框架窗口是包含 "视图" 窗口的窗口。 它们还支持附加控件条。

在多文档界面（MDI）应用程序中，主窗口派生自 `CMDIFrameWnd` 。 它间接包含文档的框架，即 `CMDIChildWnd` 对象。 `CMDIChildWnd`对象反过来也包含文档的视图。

在单文档界面（SDI）应用程序中，从派生的主窗口 `CFrameWnd` 包含当前文档的视图。

[CFrameWnd](reference/cframewnd-class.md)<br/>
SDI 应用程序的主框架窗口的基类。 也是其他所有框架窗口类的基类。

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
MDI 应用程序的主框架窗口的基类。

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
MDI 应用程序的文档框架窗口的基类。

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
当正在就地编辑服务器文档时，提供视图的框架窗口。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
