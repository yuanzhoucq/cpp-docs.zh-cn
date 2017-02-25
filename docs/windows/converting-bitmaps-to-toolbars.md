---
title: "Converting Bitmaps to Toolbars | Microsoft Docs"
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
  - "bitmaps [C++], converting to toolbars"
  - "Toolbar editor, converting bitmaps"
  - "toolbars [C++], converting bitmaps"
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Converting Bitmaps to Toolbars
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以通过转换位图来创建新工具栏。  位图的图形转换为工具栏的按钮图像。  位图通常包含单个位图的若干按钮图像，每个按钮一个图像。  图像可以为任意大小；默认的图像高度和宽度为 16 像素。  在图像编辑器中，当从“图像”菜单选择“工具栏编辑器”时，可以在[“新建工具栏资源”对话框](../mfc/new-toolbar-resource-dialog-box.md)中指定按钮图像的大小。  
  
### 将位图转换为工具栏  
  
1.  在[图像编辑器](../mfc/image-editor-for-icons.md)中打开现有的位图资源。  （如果 .rc 文件中尚没有位图，则右击 .rc 文件，从快捷菜单中选择“导入”，定位到想添加到 .rc 文件中的位图，然后单击“打开”。）  
  
2.  从“图像”菜单中选择“工具栏编辑器”。  
  
     出现[“新建工具栏资源”对话框](../mfc/new-toolbar-resource-dialog-box.md)。  可以更改图标图像的宽度和高度，以与位图匹配。  然后工具栏图像显示在工具栏编辑器中。  
  
3.  若要完成转换，请使用[“属性”窗口](../Topic/Properties%20Window.md)更改按钮的命令 **ID**。  键入新 **ID** 或从下拉列表中选择 **ID**。  
  
    > [!TIP]
    >  “属性”窗口在标题栏中包含一个图钉按钮。  单击该按钮将启用或禁用窗口的自动隐藏功能。  若要快速循环通过所有工具栏按钮属性，而不必重新打开各个属性窗口，请关闭自动隐藏功能，以便“属性”窗口保持不变。  
  
 也可以通过使用[“属性”窗口](../Topic/Properties%20Window.md)更改新工具栏上按钮的命令 ID。  有关编辑新工具栏的信息，请参见[创建、移动和编辑工具栏按钮](../mfc/creating-moving-and-editing-toolbar-buttons.md)。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 MFC 或 ATL  
  
## 请参阅  
 [Creating New Toolbars](../mfc/creating-new-toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)