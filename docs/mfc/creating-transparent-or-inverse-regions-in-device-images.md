---
title: "Creating Transparent or Inverse Regions in Device Images (Image Editor for Icons) | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], screen regions"
  - "inverse colors, device images"
  - "transparent regions, device images"
  - "transparency, device images"
  - "Image editor [C++], device images"
  - "inverse regions, device images"
  - "cursors [C++], transparent regions"
  - "screen colors"
  - "regions, transparent"
  - "icons [C++], transparent regions"
  - "display devices, transparent and screen regions"
  - "transparent regions in devices"
  - "regions, inverse"
  - "colors [C++], Image editor"
  - "device projects, transparent images"
  - "icons [C++], screen regions"
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating Transparent or Inverse Regions in Device Images (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在[图像编辑器](../mfc/image-editor-for-icons.md)中，初始图标或光标图像具有透明特性。  虽然图标和光标图像是矩形的，但有许多并不显示为矩形，这是因为图像的某些部分是透明的；屏幕上的基础图像透过图标或光标显示。  当拖动图标时，该图像的某些部分可能以反转的颜色显示。  通过在[颜色窗口](../windows/colors-window-image-editor-for-icons.md)中设置屏幕颜色和反转颜色创建此效果。  
  
 应用于图标和光标的屏幕颜色和反转颜色或者给导出的图像定形和涂色，或者指定反转区域。  这些颜色指示图像中具有这些特性的部分。  编辑时可以更改这些表示屏幕颜色和反转颜色特性的颜色。  这些更改不会影响应用程序中的图标或光标的外观。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于您现用的设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关更多信息，请参见 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 创建透明或反转区域  
  
1.  在“颜色”窗口中，单击“屏幕颜色”选择器或“补色”选择器。  
  
2.  使用绘图工具将屏幕颜色或补色应用于您的图像。  有关绘图工具的更多信息，请参见 [Using a Drawing Tool](../mfc/using-a-drawing-tool-image-editor-for-icons.md)。  
  
### 更改屏幕颜色或反转颜色  
  
1.  选择“屏幕颜色”选择器或“补色”选择器。  
  
2.  从“颜色”窗口中的“颜色调色板”中选择一种颜色。  
  
     自动为另一个选择器指定补色。  
  
    > [!TIP]
    >  如果双击“屏幕颜色”选择器或“补色”选择器，则出现[“自定义颜色选择器”对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)