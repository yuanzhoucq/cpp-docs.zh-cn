---
title: "通过视图解释用户输入 | Microsoft Docs"
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
  - "CView 类, 解释用户输入"
  - "input, 视图类"
  - "通过视图解释用户输入"
  - "用户输入, 通过视图类解释"
  - "视图, 用户界面和输入"
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 通过视图解释用户输入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

视图的其他函数然后处理成员解释所有用户输入。  您通常定义消息处理程序在类视图的成员函数处理：  
  
-   窗口鼠标和键盘操作生成的 [消息](../mfc/messages.md)。  
  
-   从菜单、工具栏按钮和快捷的[命令](../mfc/user-interface-objects-and-command-ids.md)。  
  
 这些消息处理程序成员函数说明以下操作为数据输入，或者编辑选择，包括移动数据进出剪贴板：  
  
-   鼠标离开和单击，拖动，然后双击  
  
-   键击  
  
-   菜单命令  
  
 消息视图的窗口处理取决于应用程序的需要。  
  
 [和消息映射处理主题](../mfc/message-handling-and-mapping.md) 解释如何将菜单项和其他用户界面对象。命令和如何将命令绑定到处理程序函数。  [和消息映射处理主题](../mfc/message-handling-and-mapping.md) 还说明 MFC 如何发送命令并将标准 Windows 信息对包含这些数据的处理程序的对象。  
  
 例如，应用程序可能需要实现视图中直接鼠标绘制。  Scribble 示例分别演示如何处理 `WM_LBUTTONDOWN`、`WM_MOUSEMOVE`和 `WM_LBUTTONUP` 消息开始继续，并结束线段的绘图。  另一方面，您可能有时需要说明视图中单击鼠标以选择。  视图的 `OnLButtonDown` 函数处理程序确定用户是否选择绘制或。  如果选择，该处理程序确定单击对象的边界内是否在某些视图中，并且，如果适合，修改显示对象选定状态。  
  
 视图还可以处理某些菜单命令 \(例如，那些从"编辑"菜单，剪切，粘贴复制，使用剪贴板，选择或删除数据。  此处理程序会调用 `CWnd` 类的某些剪贴板关联的成员函数将选定的数据项出入剪贴板。  
  
## 请参阅  
 [使用视图](../mfc/using-views.md)