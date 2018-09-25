---
title: 帧 Windows 所执行的操作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], about frame widows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b86b65d43fee16a0a2a8f03353c9700d6f0a5428
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423593"
---
# <a name="what-frame-windows-do"></a>框架窗口的作用

除了简单地构造视图外，框架窗口负责涉及使框架与其视图和应用程序相协调的许多任务。 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)并[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)继承自[CFrameWnd](../mfc/reference/cframewnd-class.md)，因此它们拥有`CFrameWnd`功能，以及它们所添加的新功能。 子窗口示例包括视图、控件（如按钮和列表框）以及控件条，包括工具栏、状态栏和对话栏。

框架窗口负责管理其子窗口的布局。 在 MFC 框架中，框架窗口确定任何控件条、视图及其他子窗口在其工作区中的位置。

框架窗口还将命令转发给其视图，可响应来自控件窗口的通知消息。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [控件条 （如何适应框架窗口）](../mfc/control-bars.md)

- [管理菜单、 控件条和快捷键 （如何适应框架窗口）](../mfc/managing-menus-control-bars-and-accelerators.md)

- [命令路由 （从框架窗口到其视图和其他命令目标）](../mfc/command-routing.md)

- [文档 /View 体系结构](../mfc/document-view-architecture.md)

- [控件条](../mfc/control-bars.md)

- [控件](../mfc/controls-mfc.md)

## <a name="see-also"></a>请参阅

[框架窗口](../mfc/frame-windows.md)

