---
title: "服务器：实现就地框架窗口 | Microsoft Docs"
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
  - "框架窗口, 实现"
  - "框架窗口, 就地"
  - "就地框架窗口"
  - "OLE 服务器应用程序, 框架窗口"
  - "服务器, 就地框架窗口"
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 服务器：实现就地框架窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明了必须实现执行在可视化编辑服务器应用的就地框架窗口，则可以不使用应用程序向导创建应用服务器。  代替使用本文所述的过程位置，可以使用从应用程序向导生成的应用程序或的现有框架窗口就地类 Visual C\+\+ 附带。  
  
#### 声明一就地框架窗口类  
  
1.  从 `COleIPFrameWnd`派生一就地框架窗口类。  
  
    -   使用 `DECLARE_DYNCREATE` 宏。类的头文件。  
  
    -   使用 `IMPLEMENT_DYNCREATE` 宏。类实现 \(.cpp\) 文件。  这使得此类对象由框架创建。  
  
2.  声明框架窗口类的 `COleResizeBar` 成员。  如果要支持在服务器应用的就地，调整这是需要的。  
  
     `OnCreate` 消息声明处理程序 \(使用 **属性** 窗口\)，并调用 `COleResizeBar` 的 **创建** 成员，因此，如果定义其。  
  
3.  如果有一个工具栏，请声明框架窗口类的 `CToolBar` 成员。  
  
     当服务器活动发生时，请重写 `OnCreateControlBars` 成员函数创建工具栏。  例如：  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/CPP/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     在步骤 5. 后此讨论，请参见代码的讨论。  
  
4.  就地此框架窗口类的将头文件包括在主 .cpp 文件。  
  
5.  在应用程序类的 `InitInstance`，请调用文档模板对象的 `SetServerInfo` 函数指定在打开和就地编辑和就地框架窗口的资源。  
  
 函数调用序列。**if** 语句创建提供从服务器资源的工具栏。  此时，窗口工具栏是容器的层次结构的一部分。  由于此工具栏是从 `CToolBar`派生的，它会将其消息给其所有者，容器应用程序的框架窗口，因此，除非更改所有者。  因此对 `SetOwner` 的调用是必需的。  此调用将命令发送是服务器的就地框架窗口的窗口消息，使传递到服务器。  这样服务器响应上了工具栏的操作。  
  
 工具栏的位图 ID 应与在服务器应用就地定义的其他资源。  参见 [菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)。有关详细信息。  
  
 有关更多信息，请参见、[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)[COleResizeBar](../mfc/reference/coleresizebar-class.md)[CDocTemplate::SetServerInfo](../Topic/CDocTemplate::SetServerInfo.md) 和在 *类库引用*。  
  
## 请参阅  
 [服务器](../mfc/servers.md)   
 [服务器：实现服务器](../mfc/servers-implementing-a-server.md)   
 [服务器：实现服务器文档](../mfc/servers-implementing-server-documents.md)   
 [服务器：服务器项](../mfc/servers-server-items.md)