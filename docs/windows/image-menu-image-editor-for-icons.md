---
title: "“图像”菜单（图标的图像编辑器） | Microsoft Docs"
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
  - "“图像”菜单"
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# “图像”菜单（图标的图像编辑器）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“图像”菜单只在图像编辑器处于活动状态时出现，它具有用于编辑图像、管理调色板和设置“图像编辑器”窗口选项的命令。  另外，当处理图标和光标时，使用设备图像的命令可用。  
  
 **反色**  
 反转颜色。  有关更多信息，请参见[反转选定内容中的颜色](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)。  
  
 **水平翻转**  
 水平翻转图像或选定内容。  有关更多信息，请参见[翻转图像](../mfc/flipping-an-image-image-editor-for-icons.md)。  
  
 **垂直翻转**  
 垂直翻转图像或选定内容。  有关更多信息，请参见[翻转图像](../mfc/flipping-an-image-image-editor-for-icons.md)。  
  
 **旋转 90 度**  
 将图像或选定内容旋转 90 度。  有关更多信息，请参见[翻转图像](../mfc/flipping-an-image-image-editor-for-icons.md)。  
  
 **显示颜色窗口**  
 打开[“颜色”窗口](../windows/colors-window-image-editor-for-icons.md)，在其中可以选择用于图像的颜色。  有关更多信息，请参见[处理颜色](../mfc/working-with-color-image-editor-for-icons.md)。  
  
 **使用选定项作为画笔**  
 使您能够从图像的一部分创建自定义画笔。  选定内容成为自定义画笔，它在图像中分布选定内容中的颜色。  选定内容的副本被留在拖动路径上。  拖动速度越慢，产生的副本越多。  有关更多信息，请参见[创建自定义画笔](../mfc/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 **复制和绘制选定内容的轮廓**  
 创建当前选定内容的副本并绘制其轮廓。  如果背景色包含在当前选定内容中，则在您已选择[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)的情况下它将被排除在外。  
  
 **调整颜色**  
 打开[调整颜色](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)，它允许您自定义要用于图像的颜色。  有关更多信息，请参见[自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  
  
 **加载调色板**  
 打开[“加载调色板”对话框](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)，它使您能够加载以前保存到 .pal 文件中的调色板颜色。  
  
 **保存调色板**  
 将调色板颜色保存到 .pal 文件。  
  
 **不透明处理**  
 选择此命令将使当前选定内容不透明。  清除此命令将使当前选定内容透明。  有关更多信息，请参见[选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
 **工具栏编辑器**  
 打开[“新建工具栏资源”对话框](../mfc/new-toolbar-resource-dialog-box.md)。  
  
 **网格设置**  
 打开[“网格设置”对话框](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)，在其中可以指定图像的网格。  
  
 **新建图像类型**  
 打开[“新建 \<设备\> 图像类型”对话框](../mfc/new-device-image-type-dialog-box-image-editor-for-icons.md)。  单个图标资源可以包含数个不同大小的图像；窗口可以使用适当的图标大小（取决于将如何显示它）。  新的设备类型并不修改图标的大小，而是在图标内部创建新的图像。  仅适用于图标和光标。  
  
 **当前图标\/光标图像类型**  
 打开一个子菜单，该子菜单列出前面几个可用的光标或图标图像（前九个）。  该子菜单上的最后一个命令**“更多...”**用于打开[“打开 \<设备\> 图像”对话框](../mfc/open-device-image-dialog-box-image-editor-for-icons.md)。  
  
 **删除图像类型**  
 删除选定的设备图像。  
  
 **工具**  
 启动包含[“图像编辑器”工具栏](../mfc/toolbar-image-editor-for-icons.md)种所有可用的工具的子菜单。  
  
## 要求  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)