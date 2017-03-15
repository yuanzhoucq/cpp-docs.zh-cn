---
title: "Window Panes (Image Editor for Icons) | Microsoft Docs"
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
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "graphics editor [C++]"
  - "Image editor [C++], panes"
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Window Panes (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“图像编辑器”窗口通常用两个被拆分条分隔开的窗格显示图像。  一个视图是实际大小的图像，另一个是放大的图像（默认放大因子为 6）。  这两个窗格中的视图自动更新：在一个窗格中所做的更改会立即在另一个窗格中显示出来。  这两个窗格使您易于在图像的放大视图（在此放大视图中，可以区分单个像素）上进行处理，并且可同时在图像的实际大小视图上观察工作结果。  
  
 左边的窗格使用能够满足需要的空间（最大为“图像”窗口的一半）显示图像的 1:1 放大倍数视图（默认值）。  右边的窗格显示缩放的图像（默认缩放倍数为 6:1）。  可以使用[“图像编辑器”工具栏](../mfc/toolbar-image-editor-for-icons.md)上的“放大”工具或通过使用快捷键在每个窗格中[更改放大倍数](../mfc/changing-the-magnification-factor-image-editor-for-icons.md)。  
  
 可以放大“图像编辑器”窗口的较小窗格并使用两个窗格显示较大图像的不同区域。  在窗格中单击以选择它。  
  
 通过将指针置于拆分条上并向右或向左移动拆分条可以更改窗格的相对大小。  如果希望只在一个窗格上工作，可以将拆分条一直移动到任何一侧。  
  
 如果图像编辑器窗格被以 4 或更大的因子放大，则可以[显示像素网格](../mfc/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)（它们确定图像中的单个像素的界限）。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)