---
title: "Creating a New Toolbar Button | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.toolbar"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Toolbar editor, creating buttons"
  - "toolbar buttons (in Toolbar editor), button image"
  - "toolbar buttons (in Toolbar editor), creating"
  - "toolbar buttons (in Toolbar editor)"
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a New Toolbar Button
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 创建新的工具栏按钮  
  
1.  在[资源视图](../windows/resource-view-window.md)中展开资源文件夹（如 Project1.rc）。  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  展开“工具栏”文件夹，并选择要编辑的工具栏。  
  
3.  为工具栏右端的空白按钮分配 ID。  可以通过在[“属性”窗口](../Topic/Properties%20Window.md)中编辑“ID”属性来实现。  例如，可能需要为工具栏按钮提供与菜单选项相同的 ID。  在这种情况下，使用下拉列表框选择菜单选项的 **ID**。  
  
     \- 或 \-  
  
     选择工具栏右端（在工具栏视图窗格中）的空白按钮并开始绘制。  将分配一个默认按钮命令 ID \(ID\_BUTTON\<n\>\)。  
  
 也可将图像作为新按钮复制并粘贴到工具栏上。  
  
#### 将图像作为按钮添加到工具栏  
  
1.  在[资源视图](../windows/resource-view-window.md)中，双击工具栏打开它。  
  
2.  接下来，打开要添加到工具栏中的图像。  
  
    > [!NOTE]
    >  如果在 Visual Studio 中打开图像，它将在图像编辑器中打开。  也可以在其他图形程序中打开图像。  
  
3.  从“编辑”菜单中选择“复制”。  
  
4.  单击源窗口顶部的工具栏选项卡切换到工具栏。  
  
5.  从“编辑”菜单中选择“粘贴”。  
  
     图像将作为新按钮显示在工具栏上。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 MFC 或 ATL  
  
## 请参阅  
 [Toolbar Button Properties](../mfc/toolbar-button-properties.md)   
 [Creating, Moving, and Editing Toolbar Buttons](../mfc/creating-moving-and-editing-toolbar-buttons.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)