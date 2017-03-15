---
title: "Creating an Icon or Other Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.bitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bitmaps [C++]"
  - "images [C++], creating"
  - "resource toolbars"
  - "resources [Visual Studio], creating images"
  - "bitmaps [C++], creating"
  - "graphics [C++], creating"
  - "Image editor [C++], creating images"
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Creating an Icon or Other Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以创建新的图像（位图、图标、光标或工具栏），然后使用图像编辑器自定义它的外观。  还可以创建模仿[模板](../windows/how-to-use-resource-templates.md)的新位图。  
  
### 向非托管 C\+\+ 项目中添加新图像资源  
  
1.  在[资源视图](../windows/resource-view-window.md)中右击 .rc 文件，然后从快捷菜单中选择“插入资源”。  （如果在 .rc 文件中已经有现成的图像资源，如光标，则只需右击“Cursor”文件夹，并从快捷菜单中选择“插入 Cursor”。）  
  
    > [!NOTE]
    >  **注意** 如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[“插入资源”对话框](../windows/add-resource-dialog-box.md)中，选择要创建的图像资源的类型（例如**“位图”**），然后单击**“新建”**。  
  
     如果在“插入资源”对话框中的图像资源类型旁边出现一个加号 \(**\+**\)，则说明此工具栏模板可用。  单击加号展开模板列表，选择一个模板，然后单击**“新建”**。  
  
### 向使用 .NET 编程语言的项目添加新的图像资源  
  
1.  在**解决方案资源管理器**中右击项目文件夹（如 **WindowsApplication1**）。  
  
2.  从快捷菜单中单击**“添加”**，然后选择**“添加新项”**。  
  
3.  在**“类别”**窗格中，展开**“本地项目项”**文件夹，然后选择**“资源”**。  
  
4.  在“模板”窗格中，选择要添加到项目的资源类型。  
  
     资源将添加到解决方案资源管理器中的项目，而且资源在[图像编辑器](../mfc/image-editor-for-icons.md)中打开。  现在可以使用图像编辑器中所有可用的工具修改图像。  有关向托管项目中添加图像的更多信息，请参见[设计时加载图片](../Topic/How%20to:%20Load%20a%20Picture%20Using%20the%20Designer%20\(Windows%20Forms\).md)。  
  
    > [!NOTE]
    >  您要编辑的任何托管资源都必须是链接的资源。  Visual Studio 资源编辑器不支持编辑嵌入的资源。  有关更多信息，请参见“.NET Framework 开发员指南”中的[创建资源文件](../Topic/Creating%20Resource%20Files%20for%20Desktop%20Apps.md)。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Converting Bitmaps to Toolbars](../mfc/converting-bitmaps-to-toolbars.md)   
 [Creating New Toolbars](../mfc/creating-new-toolbars.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)