---
title: 框架窗口类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac60fb8d1b12708c7e64a91beb224ca436e5005
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404522"
---
# <a name="frame-window-classes"></a>框架窗口类

每个应用程序都有一个"主框架窗口，"桌面窗口通常具有其标题中的应用程序名称。 每个文档通常有一个"文档框架窗口。" 文档框架窗口包含至少一个视图，其中显示文档的数据。

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI 和 MDI 应用程序中的帧 Windows

对于 SDI 应用程序，没有一个框架窗口类派生[CFrameWnd](../mfc/reference/cframewnd-class.md)。 此窗口是主框架窗口和文档框架窗口。 对于 MDI 应用程序，在主框架窗口派生自类[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)，和文档框架窗口是 MDI 子窗口，派生自类[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。

## <a name="use-the-frame-window-class-or-derive-from-it"></a>使用框架窗口类，或从其派生

这些类提供大部分应用程序所需的框架窗口功能。 正常情况下，默认行为和它们提供的外观将满足您的需要。 如果需要其他功能，从这些类派生。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [应用程序向导创建的框架窗口类](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [框架窗口样式](../mfc/frame-window-styles-cpp.md)

- [更改 MFC 创建的窗口样式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>请参阅

[框架窗口](../mfc/frame-windows.md)

