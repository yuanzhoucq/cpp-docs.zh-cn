---
title: "“新建工具栏资源”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.newtoolbarresource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "“新建工具栏资源”对话框"
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# “新建工具栏资源”对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“新建工具栏资源”对话框允许指定添加到工具栏资源中的按钮的宽度和高度。  默认值是 16 × 15 像素。  
  
 用于创建工具栏的位图的最大宽度为 2048。  因此如果将“按钮宽度”设置成 512，则只能有四个按钮。  如果将宽度设置成 513，则只能有三个按钮。  
  
 **按钮宽度**  
 提供一个场所，以输入从位图资源转换为工具栏资源的工具栏按钮的宽度。  图像被裁剪为指定的宽度和高度，并且颜色调整为使用标准工具栏颜色（16 色）。  
  
 **按钮高度**  
 提供一个场所，以输入从位图资源转换为工具栏资源的工具栏按钮的高度。  图像被裁剪为指定的宽度和高度，并且颜色调整为使用标准工具栏颜色（16 色）。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 MFC 或 ATL  
  
## 请参阅  
 [Toolbar Button Properties](../mfc/toolbar-button-properties.md)   
 [Converting Bitmaps to Toolbars](../mfc/converting-bitmaps-to-toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)