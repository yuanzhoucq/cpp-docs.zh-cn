---
title: 框架窗口类
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: ffa5b966ee042120213896dc7ad9d81c048ef928
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625815"
---
# <a name="frame-window-classes"></a>框架窗口类

每个应用程序都有一个 "主框架窗口"，它是一个桌面窗口，其标题中通常具有应用程序名称。 每个文档通常具有一个 "文档框架窗口"。 文档框架窗口包含至少一个显示文档数据的视图。

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI 和 MDI 应用程序中的框架窗口

对于 SDI 应用程序，有一个从类[CFrameWnd](reference/cframewnd-class.md)派生的框架窗口。 此窗口同时为主框架窗口和文档框架窗口。 对于 MDI 应用程序，主框架窗口派生自类[CMDIFrameWnd](reference/cmdiframewnd-class.md)，文档框架窗口（MDI 子窗口）派生自类[CMDIChildWnd](reference/cmdichildwnd-class.md)。

## <a name="use-the-frame-window-class-or-derive-from-it"></a>使用框架窗口类或从其派生

这些类提供应用程序所需的大部分框架窗口功能。 正常情况下，它们提供的默认行为和外观将适合你的需求。 如果需要其他功能，请从这些类派生。

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [应用程序向导创建的框架窗口类](frame-window-classes-created-by-the-application-wizard.md)

- [框架窗口样式](frame-window-styles-cpp.md)

- [更改 MFC 创建的窗口的样式](changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>另请参阅

[框架窗口](frame-windows.md)
