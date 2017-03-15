---
title: "Changing the Tab Order of Controls | Microsoft Docs"
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
  - "controls [C++], tab order"
  - "focus, tab order"
  - "tab controls, tab order"
  - "Tabstop property for controls"
  - "controls [C++], focus"
  - "dialog box controls, tab order"
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Changing the Tab Order of Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tab 键顺序是 TAB 键在对话框中将输入焦点从一个控件移动到另一个控件的顺序。  Tab 键顺序在对话框中通常是从左到右，从上到下。  每个控件均具有 **Tabstop** 属性，该属性确定控件是否接收输入焦点。  
  
### 设置控件的输入焦点  
  
1.  在[“属性”窗口](../Topic/Properties%20Window.md)中，选择 **Tabstop** 属性中的 **True** 或 **False**。  
  
 即使控件未将 Tabstop 属性设置为 True，也需要作为 Tab 键顺序的一部分。  这在某些情况下可能很重要，例如，在为没有标题的控件[定义访问键（助记键）](../mfc/defining-mnemonics-access-keys.md)时。  包含相关控件访问键的静态文本在 Tab 键顺序中必须紧邻相关控件放在其前面。  
  
> [!NOTE]
>  如果对话框包含重叠控件，则更改 Tab 键顺序可能会更改控件的显示方式。  Tab 键顺序靠后的控件总是显示在 Tab 键顺序在它们前面的任何重叠控件之上。  
  
#### 查看对话框中所有控件的当前 Tab 键顺序  
  
1.  在**“格式”**菜单上单击**“Tab 键顺序”**。  
  
 \- 或 \-  
  
-   按 Ctrl \+ D。  
  
#### 更改对话框中所有控件的 Tab 键顺序  
  
1.  在**“格式”**菜单上单击**“Tab 键顺序”**。  
  
     每个控件左上角的数字显示它在当前 Tab 键顺序中的位置。  
  
2.  按希望 Tab 键遵循的顺序单击每个控件以设置 Tab 键顺序。  
  
3.  按 **Enter**退出**“Tab 键顺序”**模式。  
  
    > [!TIP]
    >  进入“Tab 键顺序”模式后，可以按 Esc 或 Enter 键禁用更改 Tab 键顺序的能力。  
  
#### 更改两个或两个以上控件的 Tab 键顺序  
  
1.  从**“格式”**菜单中选择**“Tab 键顺序”**。  
  
2.  指定从哪里开始更改顺序。  为此，按住 Ctrl 键并单击位于希望开始更改其顺序的控件之前的控件。  
  
     例如，如果想更改控件 7 至 9 的顺序，请按住 Ctrl 键并首先选择控件 6。  
  
    > [!NOTE]
    >  若要将特定的控件设置为数字 1（在 Tab 键顺序中位于第一位），请双击该控件。  
  
3.  释放 Ctrl 键，然后按希望 Tab 键从该点起遵循的顺序单击控件。  
  
4.  按 **Enter**退出**“Tab 键顺序”**模式。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 Win32  
  
## 请参阅  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)