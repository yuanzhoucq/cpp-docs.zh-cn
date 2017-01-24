---
title: "Dialog Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.dialog"
  - "vc.editors.dialog.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource editors, Dialog editor"
  - "editors, dialog boxes"
  - "Dialog editor"
  - "dialog boxes, editing"
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Dialog Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可通过对话框编辑器创建或编辑对话框资源。 可通过双击对话框的资源视图窗口（**“视图 &#124; 资源视图”**）中的 .rc 文件来打开对话框编辑器。 请注意，资源视图在 Express 版本中不可用。  
  
 制作新对话框（或对话框模板）的前期步骤之一就是将控件添加到对话框。 在对话框编辑器中，可以排列控件以适应特定的大小、形状或对齐方式，或可将它们四处移动以在对话框中工作。 删除控件也很容易。  
  
 可将对话框存储为模板以便重复使用。 也可在设计对话框和编辑实现它的代码之间进行轻松切换。  
  
 还可在对话框编辑器中编辑单个或多个控件的属性。 可更改 tab 键顺序，即按下 TAB 键时控件获得焦点的顺序，也可定义允许用户使用键盘来选择控件的访问键（组合键）。 有关预设的访问键列表，请参阅[对话框编辑器的快捷键](../mfc/accelerator-keys-for-the-dialog-editor.md)。  
  
 你还可以通过对话框编辑器使用自定义控件，包括 ActiveX 控件。 此外，可以编辑[窗体视图](../mfc/reference/cformview-class.md)、[记录视图](../data/record-views-mfc-data-access.md)或[对话栏](../mfc/dialog-bars.md)。  
  
 从 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 开始，可使用对话框编辑器定义动态布局，这指定了用户重新调整对话框大小时控件移动及调整大小的方式。 有关详细信息，请参阅 [动态布局](../mfc/dynamic-layout.md)。  
  
-   [创建新对话框](../mfc/creating-a-new-dialog-box.md)  
  
-   [创建用户在运行时无法退出的对话框](../mfc/creating-a-dialog-box-that-users-cannot-exit.md)  
  
-   [显示或隐藏对话框编辑器工具栏](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)  
  
-   [在对话框编辑器和代码之间切换](../mfc/switching-between-dialog-box-controls-and-code.md)  
  
-   [对话框中的控件](../mfc/controls-in-dialog-boxes.md)  
  
-   [添加对话框控件的事件处理程序](../mfc/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [测试对话框](../mfc/testing-a-dialog-box.md)  
  
-   [对话框编辑器的快捷键](../mfc/accelerator-keys-for-the-dialog-editor.md)  
  
-   [对话框编辑器疑难解答](../mfc/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  使用对话框编辑器时，在许多情况下可以单击鼠标右键以显示常用命令的快捷菜单。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Resource Editors](../mfc/resource-editors.md)   
 [控件](../mfc/controls-mfc.md)   
 [控件类](../mfc/control-classes.md)   
 [对话框类](../mfc/dialog-box-classes.md)   
 [对话框控件和变量类型](../ide/dialog-box-controls-and-variable-types.md)