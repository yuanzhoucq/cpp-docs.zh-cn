---
title: "Working with Color (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.image.color"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "images [C++], background colors"
  - "Image editor [C++], Colors Palette"
  - "colors [C++], image"
  - "Colors Palette, Image editor"
  - "palettes, Image editor colors"
  - "foreground colors, Image editor"
  - "colors [C++]"
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Working with Color (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

图像编辑器包含许多专门处理和自定义颜色的功能。  可以设置前景色或背景色、用颜色填充限定区域或在图像上选择一种颜色作为当前前景色或背景色。  可以使用[“图像编辑器”工具栏](../mfc/toolbar-image-editor-for-icons.md)上的工具和[颜色窗口](../windows/colors-window-image-editor-for-icons.md)中的“颜色调色板”创建图像。  
  
 所有用于单色和 16 色图像的颜色都显示在“颜色”窗口中的“颜色调色板”中。  除 16 种标准颜色外，您可以创建自己的自定义颜色。  更改调色板中的任何颜色时将立即更改图像中的相应颜色。  
  
 当处理 256 色图标和光标图像时，使用[“属性”窗口](../Topic/Properties%20Window.md)中的“颜色”属性。  有关更多信息，请参见[创建 256 色图标或光标](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)。  
  
> [!NOTE]
>  您可以使用“图像编辑器”查看 32 位图像，但是不能对它们进行编辑。  
  
 还可以创建真彩色图像。  然而，真彩色示例不出现在“颜色”窗口的完全调色板中；它们仅出现在前景色或背景色指示器区域中。  使用[“调整颜色”对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)创建真彩色。  有关更多信息，请参见[自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  
  
 可以将自定义调色板保存到磁盘上并在需要时重新加载它们。  您最近使用过的调色板保存在“注册表”中并在下次启动 Visual Studio 时自动加载。  
  
-   [选择前景色或背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)  
  
-   [用颜色填充图像的限定区域](../windows/filling-a-bounded-area-of-an-image-with-a-color-image-editor-for-icons.md)  
  
-   [从图像中选取颜色用于其他地方](../windows/picking-up-a-color-from-an-image-to-use-elsewhere-image-editor-for-icons.md)  
  
-   [选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)  
  
-   [反转选定内容中的颜色](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)  
  
-   [自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)  
  
-   [保存和加载不同的调色板](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)  
  
-   [“颜色”窗口](../windows/colors-window-image-editor-for-icons.md)  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [资源](_win32_Resources)