---
title: "Creating a 256-Color Icon or Cursor (Image Editor for Icons) | Microsoft Docs"
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
  - "256-color palette"
  - "cursors, color"
  - "colors, icons"
  - "colors, cursors"
  - "icons, color"
ms.assetid: 2738089b-4fd3-4c45-96ae-6a15e4c6b780
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating a 256-Color Icon or Cursor (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用图像编辑器，可以从 256 色调色板中选择颜色以增大图标和光标 \(64 × 64\)。  创建资源之后，选择设备图像样式。  
  
### 创建 256 色图标或光标  
  
1.  在[资源视图](../windows/resource-view-window.md)中右击 .rc 文件，然后从快捷菜单中选择“插入资源”。  （如果在 .rc 文件中已经有现成的图像资源，如光标，则只需右击“Cursor”文件夹，并从快捷菜单中选择“插入 Cursor”。）  
  
     **注意** 如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[“插入资源”对话框](../windows/add-resource-dialog-box.md)中选择**“Icon”**或**“Cursor”**，然后单击**“新建”**。  
  
3.  在“图像”菜单上，单击“新建设备图像”。  
  
4.  选择想要的 256 色图像样式。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 无  
  
## 请参阅  
 [Using the 256\-Color Palette](../mfc/using-the-256-color-palette-image-editor-for-icons.md)   
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)