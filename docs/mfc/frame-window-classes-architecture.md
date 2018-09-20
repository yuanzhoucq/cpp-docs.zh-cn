---
title: 框架窗口类 （体系结构） |Microsoft Docs
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
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 117554b2c34853aa166c12d80b4821d3721e5992
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394122"
---
# <a name="frame-window-classes-architecture"></a>框架窗口类（体系结构）

在文档/视图体系结构框架窗口还包含一个视图窗口的窗口中。 它们还支持具有控制条附加到它们。

多文档界面 (MDI) 应用程序，在主窗口派生自`CMDIFrameWnd`。 它间接包含文档的帧，是`CMDIChildWnd`对象。 `CMDIChildWnd`对象，反过来，包含文档的视图。

在单文档界面 (SDI) 应用程序中，主窗口中，派生自`CFrameWnd`，包含当前文档的视图。

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
SDI 应用程序的主框架窗口的基类。 此外用于其他框架窗口类基本的类。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
MDI 应用程序的主框架窗口的基类。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
MDI 应用程序的文档框架窗口的基类。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
正在就地编辑服务器文档时，应提供视图框架窗口。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)

