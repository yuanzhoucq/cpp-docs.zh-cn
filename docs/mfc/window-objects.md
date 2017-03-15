---
title: "窗口对象 | Microsoft Docs"
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
  - "框架窗口 [C++], C++ 窗口对象"
  - "HWND"
  - "HWND, 窗口对象"
  - "消息 [C++], Windows"
  - "MFC [C++], 窗口"
  - "对象 [C++], 窗口"
  - "Visual C++, 窗口对象"
  - "窗口消息 [C++]"
  - "窗口对象 [C++]"
  - "窗口 [C++], C++ 窗口对象"
  - "Windows 窗口 [C++]"
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 窗口对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供的 `HWND` 类封装 Windows 句柄的 [CWnd](../mfc/reference/cwnd-class.md)。  `CWnd` 对象是一个 C\+\+ 窗口对象，与表示窗口但不包含它的 `HWND`不同。  使用 `CWnd` 派生自己的子窗口使用类或从 `CWnd`派生的大多数 MFC 类之一。  `CWnd` 类是所有窗口的基类，其中包括子框架窗口、对话框、窗口、控件和控件条 ，如工具栏。  很好的了解 [文件 .，窗口 HWND 和 C\+\+ 对象之间的关系](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) 使用 MFC为虚拟化的编程很重要。  
  
 MFC 提供窗口的某些默认功能和管理，但是，可以从 `CWnd` 中派生自己的类并使用其成员函数自定义项提供的功能。  通过使用 `CWnd` 成员函数中，构造 `CWnd` 对象并调用它的成员函数 [创建](../Topic/CWnd::Create.md) 创建子窗口，然后自定义子窗口。  可以将从 [CView](../mfc/reference/cview-class.md)派生的对象，如窗体视图或树视图，在框架窗口。  您可以通过支持文档拆分窗格的多个视图，由该类[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)提供。  
  
 从类派生的每个 `CWnd` 对象都包含消息映射，可以映射 Windows 消息或命令 ID到自己的处理程序。  
  
 有关编程的常规文件窗口中是一个了解如何一个很好的资源使用 `CWnd` 成员函数，该参数封装 `HWND` API。  
  
## 要运行的函数在 CWnd  
 `CWnd` 及其 [窗口派生的类](../mfc/derived-window-classes.md) 提供构造函数、析构函数和成员函数来初始化对象，创建基础结构和 Windows 访问封装的 `HWND`。  `CWnd` 还提供了封装发送的消息窗口访问 API，窗口的状态转换，坐标，更新，滚动，访问剪贴板以及许多其他任务的成员函数。  大多数Windows采用 `HWND` 参数的窗口管理 API 打包为 `CWnd`的成员函数。  函数及其参数的名称位于 `CWnd` 成员函数保留。  有关 `CWnd`封装的 Windows API 的详细信息，请参见类[CWnd](../mfc/reference/cwnd-class.md)。  
  
## CWnd 和窗口消息  
 一个 `CWnd` 的主要用途是用于处理 Windows 消息提供接口，如 `WM_PAINT` 或 `WM_MOUSEMOVE`。  `CWnd` 的许多命令消息成员函数的 \(这些程序处理从标识符 **afx\_msg** 和前缀开头“打开，例如 `OnPaint` 和 **OnMouseMove**的定义。  [消息处理和映射](../mfc/message-handling-and-mapping.md) 介绍消息和详细消息处理。  如果信息同样适用于您为特殊目的创建的和框架的窗口。  
  
### 您想进一步了解什么？  
  
-   [C\+\+ 窗口对象与 HWND 之间的关系](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [派生的窗口类](../mfc/derived-window-classes.md)  
  
-   [创建窗口](../mfc/creating-windows.md)  
  
-   [销毁窗口对象](../mfc/destroying-window-objects.md)  
  
-   [将 CWnd 从其 HWND 中分离出来](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [使用窗口对象](../mfc/working-with-window-objects.md)  
  
-   [设备上下文](../mfc/device-contexts.md):使 Windows 设备无关绘制的对象  
  
-   [图形对象](../mfc/graphic-objects.md):笔，画笔，字体，位图，调色板，区域  
  
## 请参阅  
 [窗口](../mfc/windows.md)