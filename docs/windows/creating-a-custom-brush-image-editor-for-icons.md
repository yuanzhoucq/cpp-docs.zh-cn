---
title: "Creating a Custom Brush (Image Editor for Icons) | Microsoft Docs"
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
  - "colors [C++], brush"
  - "brushes, colors"
  - "brushes, creating custom"
  - "images [C++], creating custom brushes"
  - "graphics [C++], custom brushes"
  - "custom brushes"
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a Custom Brush (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自定义画笔是在图像中选取的矩形部分，您可以像使用图像编辑器的现成画笔一样使用它。  可以对选定内容执行的所有操作也可以对自定义画笔执行。  
  
### 从图像的一部分创建自定义画笔  
  
1.  [选择部分图像](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md)（您要将它用作画笔）。  
  
2.  按住 **Shift** 键，在选定内容中单击并在图像中拖动它。  
  
     \- 或 \-  
  
3.  从“图像”菜单中选择“使用选定项作为画笔”。  
  
     选定内容成为自定义画笔，它在图像中分布选定内容中的颜色。  选定内容的副本被留在拖动路径上。  拖动速度越慢，产生的副本越多。  
  
     **注意** 未首先选择图像的一部分就单击“使用选定项作为画笔”会将整个图像用作画笔。  使用自定义画笔的结果还将取决于是否已选择[透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
 匹配当前背景色的自定义画笔中的像素通常是透明的：它们不在现有的图像上绘画。  可以更改此行为以便背景色像素在现有图像上绘画。  
  
 可以像使用戳或蜡纸一样使用自定义画笔，以便创建各种特殊效果。  
  
#### 用背景色绘制自定义画笔形状  
  
1.  [选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
2.  [设置背景颜色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)为想要绘制的颜色。  
  
3.  将自定义画笔置于要进行绘制的位置。  
  
4.  单击鼠标右键。  自定义画笔的任何不透明区域用背景色绘制。  
  
#### 将自定义画笔的大小加倍或减半  
  
1.  按“加号”\(**\+**\) 键将画笔大小加倍，按“减号”\(**–**\) 键将画笔大小减半。  
  
#### 取消自定义画笔  
  
1.  按 **Esc** 或选择其他绘制工具。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)