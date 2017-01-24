---
title: "何时调用更新处理程序 | Microsoft Docs"
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
  - "命令传送, update 命令"
  - "命令传送, 更新处理程序"
  - "禁用菜单项"
  - "禁用工具栏按钮"
  - "菜单项, 启用"
  - "菜单 [C++], 初始化"
  - "菜单 [C++], 在上下文更改时更新"
  - "工具栏按钮 [C++], 启用"
  - "工具栏控件 [MFC], 在 OnIdle 方法执行过程中更新"
  - "工具栏 [C++], 更新"
  - "更新处理程序"
  - "更新处理程序, 调用"
  - "更新用户界面对象"
ms.assetid: 7359f6b1-4669-477d-bd99-690affed08d9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 何时调用更新处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

假设用户单击"文件"菜单上，将生成 `WM_INITMENUPOPUP` 消息。  框架的更新机制共同更新在"文件"菜单中的所有项，将下在菜单之前，以便用户可以看到它。  
  
 为此，所有菜单项的框架路由更新命令在沿标准命令传送的弹出菜单。  在路由命令的目标有机会通过匹配更新命令并显示一条适当的消息映射项 \( `ON_UPDATE_COMMAND_UI`形式\) 和调用“更新处理程序”函数更新所有菜单项。  因此，与一个菜单项的菜单，六更新命令发出。  如果更新处理程序为菜单项的命令 ID 存在，则调用执行更新。  否则，一框架检查处理程序的现有。命令 ID 并启用或禁用菜单项为相应的。  
  
 在路由命令期间，如果找不到 `ON_UPDATE_COMMAND_UI` 框架项，则会自动启用用户界面对象是否具有 `ON_COMMAND` 类型是具有相同 . 命令 ID  否则，它禁用用户界面对象。  因此，确保用户界面对象启用，需提供对象生成的命令的处理程序或供应它的更新处理程序。  参见主题 [用户界面对象及命令 ID](../mfc/user-interface-objects-and-command-ids.md)的关系图。  
  
 禁用默认禁用用户界面对象是可能的。  有关更多信息，请参见*MFC 参考*中的`CFrameWnd` 类的[m\_bAutoMenuEnable](../Topic/CFrameWnd::m_bAutoMenuEnable.md)成员。  
  
 当应用程序接收 `WM_INITMENUPOPUP` 消息时，菜单初始化是自动的框架中，发生。  在、期间，框架搜索按钮更新处理程序的路由命令，与其为菜单类似的方式执行。  
  
## 请参阅  
 [如何：更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)