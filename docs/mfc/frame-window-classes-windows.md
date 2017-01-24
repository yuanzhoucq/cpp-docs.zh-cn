---
title: "框架窗口类 (Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "框架窗口类, 参考"
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架窗口类 (Windows)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架窗口是构成应用程序或应用程序一部分的窗口。  框架窗口通常包含其他窗口，如视图、工具栏和状态栏。  对于 `CMDIFrameWnd`，可以间接包含 `CMDIChildWnd` 对象。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 SDI 应用程序的主框架窗口的基类。  并且基类用于框架窗口类。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 MDI 应用程序主框架窗口的基类。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 MDI 应用程序的文档框架窗口的基类。  
  
 [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)  
 通常表示在浮动工具条周围出现的半高框架窗口。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 当服务器文档采用后，编辑为视图提供框架窗口。  
  
## 相关的类  
 类 `CMenu` 通过访问应用程序菜单提供接口。  在运行时，用于动态操作菜单十分有用；例如，在添加或删除了一个菜单项时可以根据上下文。  尽管菜单通常结合框架窗口，它们也可以与其他对话框和 nonchild 窗口。  
  
 [CMenu](../mfc/reference/cmenu-class.md)  
 封装 `HMENU` 句柄到应用程序的菜单栏和弹出菜单。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)