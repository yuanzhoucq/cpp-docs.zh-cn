---
title: "消息处理和映射 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - "消息处理"
  - "消息映射"
  - "MFC, 消息"
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 消息处理和映射
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 MFC 框架如何处理消息和命令以及如何将它们与处理程序函数相连。  
  
 在 Windows 的传统 Windows 程序，消息在窗口过程的大型 switch 语句进行处理。  MFC 使用 [消息映射](../mfc/message-categories.md) 映射直接消息至不同的类成员函数。  消息映射与虚函数因此效率，并且，它们允许消息由最适合的 C\+\+ 对象处理 \- 应用程序，显示文档，依此类推。  可将唯一消息或范围消息，命令 ID 或控件 ID。  
  
 **WM\_COMMAND** 消息 \(通常会由菜单、工具栏或按钮 \- 快捷键也使用消息映射机制。  MFC 定义标准命令消息 [路由](../mfc/command-routing.md) 在应用程序窗口、帧、视图和活动文档中的程序中。  如果需要，您可以重写此路由。  
  
 消息映射还提供一种更新用户界面对象 \(例如菜单和工具栏按钮\)，禁用或启用这些交互当前上下文。  
  
 有关消息和消息队列的一般信息。窗口，请参见 [消息和消息队列。](http://msdn.microsoft.com/library/windows/desktop/ms632590) [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中。  
  
## 您想进一步了解什么？  
  
-   [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [框架如何搜索消息映射](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)  
  
-   [将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [如何：在状态栏中显示命令信息](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [用户界面对象的动态更新](../mfc/how-to-update-user-interface-objects.md)  
  
-   [如何：为模板类创建消息映射](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)   
 [CWnd 类](../mfc/reference/cwnd-class.md)   
 [CCmdTarget Class](../mfc/reference/ccmdtarget-class.md)