---
title: "框架窗口类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 窗口"
  - "文档框架窗口, 类"
  - "框架窗口类"
  - "框架窗口类, 关于框架窗口类"
  - "MDI [C++], 框架窗口"
  - "MFC [C++], 框架窗口"
  - "单文档界面 (SDI), 框架窗口"
  - "窗口类, 框架"
  - "窗口 [C++], MDI"
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 框架窗口类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个应用程序都有一“主框架窗口”，通常具有应用程序名称。其标题的桌面窗口。  每个文档通常具有“文档框架窗口”。文档框架窗口包含至少一视图中，显示文档的数据。  
  
## 在 SDI、MDI 应用程序的框架窗口  
 对于 SDI 应用程序，它具有从类派生的一个框架窗口。[CFrameWnd](../mfc/reference/cframewnd-class.md) 此主窗口是框架窗口与文档框架窗口。  在 MDI 应用程序中，主框架窗口。[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)派生类，而且，文档框架窗口，为 MDI 子窗口，请从类派生。[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
  
## 使用框架窗口类或从中派生？  
 这些类提供了对于应用程序所需的大多数功能框架窗口。  在正常情况下，这些提供的默认行为和外观进行交互。  如果需要其他功能，从这些类派生。  
  
### 您想进一步了解什么？  
  
-   [应用程序向导创建的 Windows 类框架](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架窗口样式](../mfc/frame-window-styles-cpp.md)  
  
-   [更改窗口的样式。MFC 创建](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## 请参阅  
 [框架窗口](../mfc/frame-windows.md)