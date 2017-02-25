---
title: "Creating and Setting Guides and Margins | Microsoft Docs"
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
  - "guides, clearing"
  - "guides"
  - "Dialog editor, guides and margins"
  - "dialog box controls, placement"
  - "controls [C++], guides and margins"
  - "guides, creating"
  - "guides, moving"
  - "margins, moving"
ms.assetid: fafa4545-8f00-436f-b590-300e76601156
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating and Setting Guides and Margins
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

无论是移动控件、添加控件还是重新安排当前布局，参考线都可以帮助在对话框中精确地对齐控件。  参考线显示为横跨编辑器中显示的对话框的蓝色虚线，并在标尺中显示相应的箭头，标尺位于对话框编辑器的顶部和左侧。  
  
 创建对话框时，会提供四个边距。  边距是已修改的参考线，显示为蓝色虚线。  
  
### 创建参考线  
  
1.  在标尺中，单击一次可创建参考线。  （单击一下创建一条新参考线；双击则启动[“参考线设置”对话框](../mfc/guide-settings-dialog-box.md)，在其中可以指定参考线设置。）  
  
### 设置参考线  
  
1.  在对话框上，单击参考线并将它拖到新位置。  （也可以单击标尺中的箭头拖动关联的参考线。）  
  
     参考线的坐标显示在窗口底部的状态栏中和标尺中。  将指针移动到标尺中的箭头上可显示参考线的确切位置。  
  
### 删除参考线  
  
1.  将参考线拖出对话框。  
  
 \- 或 \-  
  
-   将相应的箭头拖离标尺。  
  
#### 移动边距  
  
1.  将边距拖动到新位置。  
  
     若要使边距消失，请将边距移到零位置。  若要重新显示边距，请将指针放在边距的零位置上并使边距移动就位。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 要求  
 Win32  
  
## 请参阅  
 [Dialog Editor States \(Guides and Grids\)](../mfc/dialog-editor-states-guides-and-grids.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)