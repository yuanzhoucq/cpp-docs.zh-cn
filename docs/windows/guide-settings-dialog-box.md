---
title: "“参考线设置”对话框 | Microsoft Docs"
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
  - "DLU（对话框单元）"
  - "对话框编辑器，参考线对齐"
  - "网格间距"
  - "参考线设置"
  - "对话框单元 (DLU)"
  - "对话编辑器中的布局网格"
  - "参考线对齐（对话框编辑器）"
  - "控件 [C++]，参考线/网格线对齐"
  - "“参考线设置”对话框（对话框编辑器）"
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# “参考线设置”对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 版式参考线  
 显示布局参考线的设置。  
  
 **无**  
  
 隐藏布局工具。  
  
 **标尺和参考线**  
  
 如果启用，则在布局工具中添加标尺；可将参考线放置在标尺中。  默认参考线是边距，可以通过拖动来移动它。  在标尺中单击以设置参考线。  当控件在参考线上面或旁边移动时，控件将“对齐”参考线。  控件附加到参考线上后便与参考线一起移动。  如果控件的每一端均附加到参考线上，则当参考线移动时，控件将调整大小。  
  
 **网格**  
  
 创建布局网格。  新控件自动对齐网格。  
  
## 网格间距  
 显示以对话框单元 \(DLU\) 为单位的网格间距设置。  
  
 **宽度：DLU**  
  
 设置以 DLU 为单位的布局网格宽度。  水平 DLU 是按四划分的对话框字体的平均宽度。  
  
 **高度：DLU**  
  
 设置以 DLU 为单位的布局网格高度。  垂直 DLU 是按八划分的对话框字体的平均高度。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Modifying the Layout Grid](../mfc/modifying-the-layout-grid.md)   
 [Dialog Editor States \(Guides and Grids\)](../mfc/dialog-editor-states-guides-and-grids.md)