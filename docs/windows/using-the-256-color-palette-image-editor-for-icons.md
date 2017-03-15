---
title: "Using the 256-Color Palette (Image Editor for Icons) | Microsoft Docs"
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
  - "colors, icons and cursors"
  - "cursors, color"
  - "color palettes, 256-color"
  - "palettes, 256-color"
  - "icons, color"
ms.assetid: 1506ed00-669b-4a21-b1a4-39b6a84a78bb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Using the 256-Color Palette (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要用 256 色调色板中的颜色绘制，则需要从[颜色窗口](../windows/colors-window-image-editor-for-icons.md)中的“颜色调色板”中选择这些颜色。  
  
### 为大图标从 256 色调色板中选择颜色  
  
1.  选择大图标或光标，或者创建新的大图标或光标。  
  
2.  从“颜色”窗口“颜色”调色板显示的 256 种颜色中，选择一种颜色。  
  
     选定的颜色将成为“颜色”窗口“颜色调色板”中的当前颜色。  
  
    > [!NOTE]
    >  用于 256 色图像的初始调色板与由 CreateHalftonePalette Windows API 返回的调色板相匹配。  所有准备用于 Windows shell 的图标应使用此调色板以防止在调色板实现过程中产生闪烁。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Creating a 256\-Color Icon or Cursor](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)   
 [Icons and Cursors: Image Resources for Display Devices](../mfc/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)