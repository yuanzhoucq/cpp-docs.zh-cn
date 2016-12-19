---
title: "Associating a Menu Command with an Accelerator Key | Microsoft Docs"
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
  - "keyboard shortcuts, menu association"
  - "commands, associating menu commands with accelerator keys"
  - "menu commands, associating with keyboard shortcuts"
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associating a Menu Command with an Accelerator Key
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你经常希望某一菜单命令和某一键盘组合可以发出相同的程序命令。 你可以通过使用“菜单”编辑器为该菜单命令和应用程序快捷键对应表中的条目分配相同的资源标识符，来达到这个目的。 接着你可以编辑该菜单命令的[标题](../windows/menu-command-properties.md)，以显示快捷键的名称。  
  
### 将菜单命令与快捷键关联  
  
1.  在“菜单”编辑器中，选择所需菜单命令。  
  
2.  在“属性窗口”[](../Topic/Properties%20Window.md)中，向“标题”属性添加快捷键的名称：  
  
    -   在菜单标题后面，输入制表符 \(\\t\) 的转义序列，以使所有菜单的快捷键都左对齐。  
  
    -   输入修改键的名称（**CTRL**、**ALT** 或 **SHIFT**），后跟一个加号 \(**\+**\) 和附加键的名称、字母或符号。  
  
         例如，若要将 **CTRL\+O** 分配给“文件”菜单上的“打开”命令，请修改该菜单命令的“标题”，以便它如下所示：  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         在你输入时，“菜单”编辑器中的菜单命令会进行更新以反映新标题。  
  
3.  在“快捷键”编辑器中[创建快捷键对应表条目](../windows/adding-an-entry-to-an-accelerator-table.md)并向它分配与菜单命令相同的标识符。 使用你认为易于记住的组合键。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Adding Commands to a Menu](../windows/adding-commands-to-a-menu.md)   
 [Menu Editor](../mfc/menu-editor.md)