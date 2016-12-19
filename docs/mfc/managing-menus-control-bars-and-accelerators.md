---
title: "管理菜单、控件条和快捷键 | Microsoft Docs"
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
  - "快捷键表 [C++]"
  - "控件条, 在框架窗口中更新"
  - "框架窗口, 更新"
  - "MDI, 框架窗口"
  - "菜单, 在上下文更改时更新"
  - "共享菜单"
  - "状态栏, 更新"
  - "更新用户界面对象"
  - "用户界面对象, 更新"
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 管理菜单、控件条和快捷键
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架窗口管理更新用户界面对象，包括菜单、工具栏按钮、状态栏和快捷键。  还将管理共享在 MDI 应用程序的菜单栏。  
  
## 管理的菜单  
 框架窗口参与更新用户界面项通过在 [如何更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)中描述的 `ON_UPDATE_COMMAND_UI` 机制。  在、期间，在工具栏和其他控件条按钮更新。  在下拉菜单的菜单项之前更新下拉菜单在菜单栏上。  
  
 在 MDI 应用程序中，MDI 框架窗口管理菜单栏和标题。  MDI 框架窗口拥有使用为菜单栏的默认菜单，当没有活动 MDI 子窗口时。  在存在活动时，MDI 子框架窗口的菜单栏。活动 MDI 子窗口的菜单获得。  如果 MDI 应用程序支持多文档类型，如图文档和工作表，每个类型置于其自己的菜单为菜单栏和更改主框架窗口的标题。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 提供标准命令提供默认实现。对 MDI 应用程序窗口显示的菜单。  具体而言，"新建窗口"命令 \(**ID\_WINDOW\_NEW**\) 实现创建新框架窗口和视图在当前文件。  才需要高级的自定义项，则需要重写这些实现。  
  
 同一文档类型的多个 MDI 子窗口共享菜单资源。  如果一些 MDI 子窗口是由相同文档模板创建的，它们都可使用同一个菜单资源，保存在 Windows 的系统资源。  
  
## 显示状态栏。  
 框架窗口还确定在其工作区内的状态栏以及管理状态栏的指示符。  框架窗口状态栏在清除并更新消息大小作为必要性，并且显示提示字符串，在用户选择菜单项或工具栏按钮，如 [如何显示命令信息在状态栏](../mfc/how-to-display-command-information-in-the-status-bar.md)所述。  
  
## 管理的快捷键  
 维护每个框架窗口自动执行您的键盘快捷转换选项的快捷键对应表。  该机制使您可以轻松定义调用菜单命令的快捷键 \(也称为快捷键\)。  
  
## 请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)