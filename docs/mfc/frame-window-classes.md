---
title: "框架窗口类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5e67ef155c029285d0b306ca2d05179e993de78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-classes"></a>框架窗口类
每个应用程序都有一个"主框架窗口，"一个桌面窗口，通常在其标题中具有的应用程序名称。 每个文档通常有一个"文档框架窗口。" 文档框架窗口包含至少一个视图，它显示了文档的数据。  
  
## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI 和 MDI 应用程序中的框架窗口  
 对于 SDI 应用程序，没有一个派生自类的框架窗口[CFrameWnd](../mfc/reference/cframewnd-class.md)。 此窗口是主框架窗口和文档框架窗口。 对于 MDI 应用程序中，主框架窗口派生自类[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)，并且是 MDI 子窗口，文档框架窗口派生自类[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。  
  
## <a name="use-the-frame-window-class-or-derive-from-it"></a>使用框架窗口类，或从其派生  
 这些类提供大部分需要你的应用程序的框架窗口功能。 在正常情况下，默认行为和它们提供的外观将满足你的需求。 如果你需要其他功能，派生自这些类。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [应用程序向导创建的框架窗口类](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架窗口样式](../mfc/frame-window-styles-cpp.md)  
  
-   [更改 mfc 创建的窗口样式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## <a name="see-also"></a>请参阅  
 [框架窗口](../mfc/frame-windows.md)

