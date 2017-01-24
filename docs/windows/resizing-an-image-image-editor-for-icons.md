---
title: "Resizing an Image (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.image.editing"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], resizing images"
  - "graphics [C++], resizing"
  - "images [C++], resizing"
  - "resizing images"
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resizing an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调整图像大小时图像编辑器的行为取决于是已[选定的](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md)整个图像还是仅选定图像的一部分。  
  
 当选定内容只包括图像的一部分时，图像编辑器通过删除像素行或列并用当前背景色填充空出的区域以缩小选定内容，或者通过复制像素行或列拉伸选定内容。  
  
 当选定内容包括整个图像时，图像编辑器或者缩小和拉伸此图像，或者裁剪和扩展它。  
  
 调整图像大小的机制有两种：尺寸柄和[“属性”窗口](../Topic/Properties%20Window.md)。  可以拖动尺寸柄更改整个图像或图像的一部分的大小。  可以拖动的尺寸柄是实心的。  不能拖动空心的尺寸柄。  使用“属性”窗口只能调整整个图像的大小，而不能调整选定部分的大小。  
  
 ![位图上的大小调整控点](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
尺寸柄  
  
> [!NOTE]
>  如果已在[“网格设置”对话框](../mfc/grid-settings-dialog-box-image-editor-for-icons.md)中选定“平铺网格”选项，则调整大小将对齐下一个平铺网格线。  如果只选择了“像素网格”选项（默认设置），则调整大小将对齐下一个可用像素。  
  
-   [调整整个图像的大小](../mfc/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [裁剪或扩展整个图像](../mfc/cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [缩小或拉伸整个图像](../mfc/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [缩小或拉伸图像的一部分](../mfc/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)