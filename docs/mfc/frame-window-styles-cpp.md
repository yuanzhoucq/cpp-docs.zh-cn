---
title: "框架窗口样式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "框架窗口 [C++], 样式"
  - "MFC [C++], 框架窗口"
  - "PreCreateWindow 方法, 设置窗口样式"
  - "样式, 窗口"
  - "窗口样式 [C++]"
  - "窗口 [C++], MFC"
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架窗口样式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获得与框架的框架窗口适合大多数程序，使用最新机能 [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) 和 MFC 全局函数 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md)，但是，可以获得额外的灵活性。  `PreCreateWindow` 是 `CWnd`的成员函数。  
  
 如果适用于 **WS\_HSCROLL** 和 **WS\_VSCROLL** 样式主框架窗口，则应用于 **MDICLIENT** 窗口，以便用户能滚动 **MDICLIENT** 区域。  
  
 如果窗口的 **FWS\_ADDTOTITLE** 设置样式位 \(它是默认情况\)，视图通知框架窗口的标题显示在窗口的标题栏。文档视图的名称。  
  
## 您想进一步了解什么？  
  
-   [管理的 MDI 子窗口 \(MDICLIENT\)](../mfc/managing-mdi-child-windows.md)，在包含 MDI 子窗口的 MDI 框架窗口中  
  
-   [更改窗口的样式。MFC 创建](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [窗口样式](../mfc/reference/window-styles.md)  
  
## 请参阅  
 [框架窗口](../mfc/frame-windows.md)