---
title: "Using a Drawing Tool (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.image.drawing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], selecting drawing tools"
  - "Image editor [C++], toolbar"
  - "drawing tools"
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Using a Drawing Tool (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

图像编辑器的手工绘制和清除工具都以相同的方式工作：选择工具并且（如有必要）[选择前景和背景颜色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)以及大小和形状选项。  然后将鼠标指针移到图像并单击或拖动以绘制和清除图像。  
  
 当选择“清除”工具、“画笔”工具或“喷枪”工具时，选项选择器显示该工具的选项。  
  
> [!TIP]
>  您可能会发现用绘制工具以背景色进行绘制比使用**“橡皮擦”**工具更为方便。  
  
 可以从“图像编辑器”工具栏或“图像”菜单选择绘制工具。  
  
### 从“图像编辑器”工具栏选择和使用绘制工具  
  
1.  在“图像编辑器”工具栏上单击按钮。  
  
    -   当按下鼠标左键时，“清除”工具将当前背景色涂抹在图像上。  
  
    -   “铅笔”工具以一个像素的固定宽度手工绘制。  
  
    -   选项选择器确定“画笔”工具的形状和大小。  
  
    -   “喷枪”工具围绕画笔的中心随机分布颜色像素。  
  
        > [!TIP]
        >  当光标悬停在[“图像编辑器”工具栏](../mfc/toolbar-image-editor-for-icons.md)上的按钮上方时会出现工具提示。  这些提示有助于识别这里提到的特定按钮。  
  
2.  如有必要，请选择颜色和画笔：  
  
    -   在[调色板](../windows/colors-window-image-editor-for-icons.md)中，单击鼠标左键以选择前景色或单击鼠标右键以选择背景色。  
  
    -   在[选项选择器](../mfc/toolbar-image-editor-for-icons.md)中，单击表示要使用的画笔的形状。  
  
3.  指向图像上要开始绘制或绘画的位置。  指针将根据选择的工具更改形状。  
  
4.  按下鼠标左键（使用前景色）或鼠标右键（使用背景色）并在绘制时按住不放。  
  
### 从“图像”菜单选择和使用绘制工具  
  
1.  单击“图像”菜单并选择“工具”命令。  
  
2.  在级联子菜单上选择要使用的工具。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)