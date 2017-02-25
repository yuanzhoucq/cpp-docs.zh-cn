---
title: "Drawing Lines or Closed Figures (Image Editor for Icons) | Microsoft Docs"
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
  - "closed figures, drawing"
  - "lines [C++], painting"
  - "lines [C++], drawing"
  - "Image editor [C++], drawing lines"
  - "shapes, drawing"
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Drawing Lines or Closed Figures (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用于绘制线条和闭合图形的图像编辑器工具都以同样的方式工作：将插入点放在一个点处，然后再拖动到另一个点。  对于线条，这些点为端点。  对于闭合图形，这些点为该图形的边框的对角点。  
  
 线条以由当前画笔选定内容确定的宽度绘制，空心图形以由当前宽度选定内容确定的宽度绘制。  对于线条和所有的图形（包括空心的和实心的），如果按下鼠标左键就用当前前景色绘制，如果按下鼠标右键则以当前背景色绘制。  
  
### 绘制线条  
  
1.  在[“图像编辑器”工具栏](../mfc/toolbar-image-editor-for-icons.md)上（或从“工具”命令 \-\>“图像”菜单），单击“线条”工具。  
  
2.  如有必要，请选择颜色和画笔：  
  
    -   在[调色板](../windows/colors-window-image-editor-for-icons.md)中，单击鼠标左键以选择前景色或单击鼠标右键以选择背景色。  
  
    -   在[选项选择器](../mfc/toolbar-image-editor-for-icons.md)中，单击表示要使用的画笔的形状。  
  
3.  将指针放在线条的起点。  
  
4.  拖动到线条的终点。  
  
### 绘制闭合图形  
  
1.  在“图像编辑器”工具栏上（或从“工具”命令 \-\>“图像”菜单），单击“封闭图绘制”工具。  
  
     “封闭图绘制”工具按照它们各自按钮上的指示创建图形。  
  
2.  如有必要，请选择颜色和线条宽度。  
  
3.  将指针移动到要在其中绘制图形的矩形区域的一角。  
  
4.  将指针拖动到对角。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)