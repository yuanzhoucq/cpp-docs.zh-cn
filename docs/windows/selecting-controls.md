---
title: "Selecting Controls | Microsoft Docs"
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
  - "Dialog editor, selecting controls"
  - "dominant controls"
  - "dialog box controls, selecting in editor"
  - "controls [C++], selecting"
  - "size, controls"
  - "controls [C++], dominant"
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Selecting Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

选定控件以调整大小、对齐、移动、复制或删除它们，然后执行所需的操作。  在大多数情况下，需要选择一个以上的控件才能使用[“对话框编辑器”工具栏](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)上的大小调整和对齐工具。  
  
 当选定一个控件时，它的周围有阴影框以及实心（活动）或空心（非活动）“尺寸柄”，即出现在选框中的小方块。  当选定多个控件时，主导控件有实心尺寸柄；所有其他选定的控件有空心尺寸柄。  
  
 当调整多个控件的大小或对齐它们时，对话框编辑器使用“主导控件”来确定如何调整其他控件的大小或对齐它们。  默认情况下，主导控件是第一个选定的控件。  
  
-   [选定多个控件](../mfc/selecting-multiple-controls.md)  
  
-   [指定主导控件](../mfc/specifying-the-dominant-control.md)  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)