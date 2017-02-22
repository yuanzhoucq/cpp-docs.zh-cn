---
title: "Defining Mnemonics (Access Keys) | Microsoft Docs"
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
  - "access keys [C++], adding"
  - "keyboard shortcuts [C++], controls"
  - "dialog box controls, mnemonics"
  - "access keys [C++], checking"
  - "mnemonics, checking for duplicate"
  - "mnemonics"
  - "mnemonics, dialog box controls"
  - "keyboard shortcuts [C++], uniqueness checking"
  - "Check Mnemonics command"
  - "controls [C++], access keys"
  - "access keys [C++]"
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Defining Mnemonics (Access Keys)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常，键盘用户使用 Tab 键或箭头键在对话框中将输入焦点从一个控件移动到另一个控件。  然而，可以定义访问键（助记或容易记住的名称）使用户可以通过按单个键来选择控件。  
  
### 定义带可见标题的控件（普通按钮、复选框和单选按钮）的访问键  
  
1.  选择对话框上的控件。  
  
2.  在[“属性”窗口](../Topic/Properties%20Window.md)中，在 **Caption** 属性中键入控件的新名称，在要作为该控件访问键的字母之前键入“and”符 \(**&**\)。  例如 `&Radio1`。  
  
3.  按 **Enter**。  
  
     显示的标题中出现一个下划线以指示访问键，例如，**R**adio1。  
  
### 定义没有可见标题的控件的访问键  
  
1.  使用[工具箱](../Topic/Toolbox.md)中的 **Static Text** 控件为控件指定标题。  
  
2.  在静态文本标题中，在要作为访问键的字母之前键入“and”符 \(**&**\)。  
  
3.  确保静态文本 \(Static Text\) 控件在 Tab 键顺序中紧位于其标记的控件之前。  
  
 对话框中的所有访问键都应是唯一的。  
  
#### 检查重复的访问键  
  
1.  在“格式”菜单上单击“检查助记键”。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)