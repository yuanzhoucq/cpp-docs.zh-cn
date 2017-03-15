---
title: "Adding Commands to a Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.menu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "menu items, adding to menus"
  - "menus, adding items"
  - "commands, adding to menus"
  - "commands"
  - "menu items"
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Adding Commands to a Menu
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 将命令添加到菜单  
  
1.  [创建菜单](../windows/creating-a-menu.md)。  
  
2.  单击菜单名，例如“文件”。  
  
     每个菜单都将展开，并显示一个新项框让你输入命令。  例如，可以将“新建”、“打开”和“关闭”命令添加到“文件”菜单中。  
  
3.  在新项框中，键入新菜单命令的名称。  
  
    > [!NOTE]
    >  你键入的文本将同时出现在菜单编辑器中以及[属性窗口](../Topic/Properties%20Window.md)内的**“标题”**框中。  你可以在任一位置编辑新菜单的属性。  
  
    > [!TIP]
    >  你可以定义一个允许用户选择菜单命令的助记键（热键）。  在字母前面键入 & 号，将它指定为助记键。  用户可以通过键入该字母来选择菜单命令。  
  
4.  在“属性”窗口中，选择适用的菜单命令属性。  有关详细信息，请参阅[菜单命令属性](../windows/menu-command-properties.md)。  
  
5.  在“属性”窗口的**“提示”**框中，键入希望显示在应用程序状态栏中的提示字符串。  
  
     这将在字符串表中创建一个条目，该条目的资源标识符与你创建的菜单命令相同。  
  
    > [!NOTE]
    >  提示只能应用于**“弹出窗口”**属性为**“True”**的菜单项。  例如，包含子菜单项的顶级菜单项可以有提示。  提示的用途是告诉用户在单击菜单项时会发生什么事。  
  
6.  按**“ENTER”**完成菜单命令。  
  
     将选定新项框，让你可以创建其他菜单命令。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Menu Editor](../mfc/menu-editor.md)   
 [菜单](_win32_Menus)