---
title: "框架窗口类（体系结构） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.frame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "框架窗口类, 文档/视图体系结构"
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 框架窗口类（体系结构）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在文档\/视图体系结构方面，框架窗口是一窗口的窗口。  它们还支持具有控件条附加到它们。  
  
 在多文档界面 \(MDI\) \(MDI\) 应用程序中，主窗口从 `CMDIFrameWnd`派生。  其间接包含文档的框架，它是 `CMDIChildWnd` 对象。  `CMDIChildWnd` 对象，反之亦然，包含文档的视图。  
  
 在单文档界面 \(SDI\) \(SDI\) 应用程序中，主窗口，从 `CFrameWnd`中派生，它包含当前文件的视图。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 SDI 应用程序的主框架窗口的基类。  并且的基类框架窗口类。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 MDI 应用程序的主框架窗口的基类。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 MDI 应用程序的文档框架窗口的基类。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 当服务器文档采用后，编辑为视图提供框架窗口。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)