---
title: "Saving and Loading Different Color Palettes (Image Editor for Icons) | Microsoft Docs"
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
  - "color palettes [C++]"
  - "palettes"
  - "palettes, Image editor"
  - "colors [C++], Image editor"
  - "Image editor [C++], palettes"
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Saving and Loading Different Color Palettes (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

你可以保存并加载包含[自定义颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)的调色板。  （默认情况下，启动 Visual Studio 时，会自动加载最近使用的调色板。）  
  
> [!TIP]
>  由于图像编辑器无法还原默认调色板，所以你应保存默认调色板（名称如 standard.pal 或 default.pal），这样便可轻松还原默认设置。  
  
### 保存自定义调色板  
  
1.  从“图像”菜单上选择“保存调色板”。  
  
2.  导航到要用于保存调色板的目录并键入调色板的名称。  
  
3.  单击**“保存”**。  
  
### 加载自定义调色板  
  
1.  从“图像”菜单上选择“加载调色板”。  
  
2.  在[“加载调色板”对话框](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)中，导航到正确的目录，然后选择需加载的调色板。  以 .pal 文件扩展名保存调色板。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)