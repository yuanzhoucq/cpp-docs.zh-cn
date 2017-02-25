---
title: "Creating a Menu | Microsoft Docs"
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
  - "mnemonics, associating menu items"
  - "menus, associating commands with mnemonic keys"
  - "menus, creating"
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Creating a Menu
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  资源窗口在 Express 版本中不可用。  
  
### 创建标准菜单  
  
1.  从**“视图”**菜单单击**“资源视图”**，然后右键单击**“菜单”**标题并选择**“添加资源”**。 选择**“菜单”**。  
  
2.  选择菜单栏上的“新建项目”框（包含“请在此处输入”的矩形）。  
  
     ![菜单编辑器中的“新建项”框](../Image/vcMenuEditorNewItemBox.gif "vcMenuEditorNewItemBox")  
新建项目框  
  
3.  键入新菜单的名称，例如“文件”。  
  
     键入的文本将同时出现在菜单编辑器以及[属性窗口](../Topic/Properties%20Window.md)中的“标题”框中。 你可以在任一位置编辑新菜单的属性。  
  
     为菜单栏上的新菜单指定名称后，新项目框移到右边（允许你添加另一菜单），并且另一个新项目框在第一个菜单下面打开，以便可以向其添加菜单命令。  
  
     ![展开的“新建项”框](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")  
新项目框的焦点在键入菜单名称后转移  
  
    > [!NOTE]
    >  要在菜单栏上创建单项菜单，请将“弹出”属性设置为 False。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Menu Editor](../mfc/menu-editor.md)