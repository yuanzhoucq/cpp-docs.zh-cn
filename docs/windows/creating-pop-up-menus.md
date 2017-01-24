---
title: "Creating Pop-up Menus | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "context menus, Menu Editor"
  - "pop-up menus, creating"
  - "menus, pop-up"
  - "menus, creating"
  - "shortcut menus, creating"
  - "pop-up menus, displaying"
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating Pop-up Menus
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[弹出菜单](../mfc/menus-mfc.md)显示常用命令。 它们对指针的位置可以区分上下文。 在应用程序中使用弹出菜单需要先生成菜单，然后将菜单连接到应用程序代码。  
  
 创建菜单资源后，应用程序代码需要加载该菜单资源，并使用 [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) 显示该菜单。 用户通过单击弹出菜单之外的位置关闭弹出菜单后，或用户单击某个命令后，该函数将返回。 如果用户选择一个命令，该命令消息将被发送到传递了其句柄的窗口。  
  
### 创建弹出菜单  
  
1.  使用空标题（不提供**标题**）[创建菜单](../windows/creating-a-menu.md)。  
  
2.  [将菜单命令添加到新菜单](../windows/adding-commands-to-a-menu.md)。 移到空白菜单标题下的第一个菜单命令（临时标题显示“在此键入”）。 键入**标题**和任何其他信息。  
  
     对弹出菜单中的任何其他菜单命令重复此过程。  
  
3.  保存菜单资源。  
  
    > [!TIP]
    >  有关查看弹出菜单的详细信息，请参阅[以弹出菜单方式查看菜单](../windows/viewing-a-menu-as-a-pop-up-menu.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Connecting a Pop\-up Menu to Your Application](../windows/connecting-a-pop-up-menu-to-your-application.md)   
 [Menu Editor](../mfc/menu-editor.md)