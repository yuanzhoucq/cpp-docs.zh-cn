---
title: "Creating a Device Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], creating"
  - "icons [C++], creating"
  - "display devices"
  - "display devices, creating image"
  - "images [C++], creating for display devices"
  - "icons [C++], inserting"
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Creating a Device Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当创建新的图标或光标资源时，图像编辑器首先以特定的样式创建一个图像。对于图标，样式为 32 x 32，16 色；对于光标，样式为 32 x 32，单色。  然后可以将具有不同大小和样式的图像添加到初始图标或光标中，并根据需要为不同的显示设备编辑每个附加图像。  您也可以通过对某个现有图像类型或在图形程序中创建的位图执行剪切和粘贴操作来编辑图像。  有关 Windows 使用的图标大小的更多信息，请参见 Windows SDK 文档中的[图标](_win32_Icons_cpp)。  
  
 当在[图像编辑器](../mfc/image-editor-for-icons.md)中打开图标或光标资源时，默认情况下将打开最匹配当前显示设备的图像。  
  
### 创建新的图标或光标  
  
1.  在[资源视图](../windows/resource-view-window.md)中右击 .rc 文件，然后从快捷菜单中选择**“插入资源”**。  （如果 .rc 文件中已有图像资源，例如光标，则只需右击**“光标”**文件夹，然后在快捷菜单中选择**“插入光标”**。）  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入资源](../windows/add-resource-dialog-box.md)对话框中，选择**“图标”**或**“光标”**，然后单击**“新建”**。  对于图标，这将创建一个具有 32 x 32、16 色图标的图标资源。  对于光标，则创建一个 32 x 32、单色（两种颜色）图像。  
  
     如果在**“插入资源”**对话框中的图像资源类型旁边出现一个加号（**“\+”**），则说明工具栏模板可用。  单击加号展开模板列表，选择一个模板，然后单击**“新建”**。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 无  
  
## 请参阅  
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)