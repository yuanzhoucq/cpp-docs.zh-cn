---
title: "Aligning Controls on a Guide | Microsoft Docs"
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
  - "DLUs (dialog units)"
  - "controls [C++], aligning"
  - "Dialog editor, snap to guides"
  - "guides, tick mark interval"
  - "dialog box controls, placement"
  - "guides, aligning controls"
  - "dialog units (DLUs)"
  - "snap to guides (Dialog editor)"
  - "controls [C++], sizing"
  - "tick mark interval in Dialog editor"
  - "controls [C++], snap to guides/grid"
ms.assetid: 17db84ba-5288-4478-be57-afa748aa6447
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Aligning Controls on a Guide
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当移动控件时，控件的尺寸柄对齐参考线，而参考线对齐控件（如果以前没有任何控件对齐参考线的话）。  当移动参考线时，与它对齐的控件也同时移动。  与一条以上的参考线对齐的控件在其中一条参考线移动时调整大小。  
  
 确定参考线和控件间距的标尺中的刻度线由对话框单元 \(DLU\) 定义。  DLU 基于对话框字体的大小，通常为 8 磅 MS Shell Dlg 字体。  水平 DLU 是按四划分的对话框字体的平均宽度。  垂直 DLU 是按八划分的字体的平均高度。  
  
### 用参考线调整一组控件的大小  
  
1.  将控件的一端与一条参考线对齐。  
  
2.  将另一条参考线拖到控件的另一端。  
  
     如果需要对多个控件执行此操作，则调整每个控件的大小使其与第二条参考线对齐。  
  
3.  移动任一参考线以调整控件的大小。  
  
### 更改刻度线的间隔  
  
1.  从“格式”菜单中选择“参考线设置”。  
  
2.  在[“参考线设置”对话框](../mfc/guide-settings-dialog-box.md)中，在“网格间距”字段中指定以 DLU 为单位的新的宽度和高度。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Dialog Editor States \(Guides and Grids\)](../mfc/dialog-editor-states-guides-and-grids.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)