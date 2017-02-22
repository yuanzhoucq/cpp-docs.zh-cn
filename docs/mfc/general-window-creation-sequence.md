---
title: "常用窗口创建序列 | Microsoft Docs"
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
  - "框架窗口 [C++], 创建"
  - "序列 [C++]"
  - "序列 [C++], 窗口创建"
  - "窗口 [C++], 创建"
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 常用窗口创建序列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当创建时一个窗口拥有，如子窗口，框架使用进程并在 [文档\/视图创建](../mfc/document-view-creation.md)描述的相同。  
  
 MFC 提供的所有类使用 Windows [构造两个阶段](../mfc/one-stage-and-two-stage-construction-of-objects.md)。  即在 C\+\+ **new** 运算符的调用时，构造函数将分配并初始化 C.C\+\+ 对象，但不会创建相应的 Windows 窗口。  该窗口对象的成员函数。之后立即调用 [创建](../Topic/CWnd::Create.md)  
  
 **创建** 成员函数使 Windows 窗口并存储其在 C\+\+ 对象的公共数据成员 [m\_hWnd](../Topic/CWnd::m_hWnd.md)的 `HWND`。  **创建** 提供在创建参数的完整灵活性。  在调用 **创建**前，可能需要注册与全局函数 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 的窗口类才能将框架的图标以及类样式。  
  
 对于框架窗口，则可以使用 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 成员函数而不是 **创建**。  使用较少形参`LoadFrame`，使 Windows 窗口。  从资源获取其许多默认值，其中包括标题、图标、帧的快捷键对应表和菜单。  
  
> [!NOTE]
>  图标和菜单、快捷键表资源必须具有公共资源 ID，如。**IDR\_MAINFRAME**，LoadFrame 要加载的方法。  
  
## 您想进一步了解什么？  
  
-   [窗口对象](../mfc/window-objects.md)  
  
-   [注册窗口类](../mfc/registering-window-classes.md)  
  
-   [销毁窗口对象](../mfc/destroying-window-objects.md)  
  
-   [创建文档框架窗口](../mfc/creating-document-frame-windows.md)  
  
## 请参阅  
 [创建窗口](../mfc/creating-windows.md)