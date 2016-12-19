---
title: "显示或隐藏对话框编辑器工具栏 | Microsoft Docs"
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
helpviewer_keywords: 
  - "控件 [C++]，显示或隐藏“对话框编辑器”工具栏"
  - "工具栏 [C++]，显示"
  - "工具栏 [C++]，隐藏"
  - "对话框编辑器，显示或隐藏工具栏"
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 显示或隐藏对话框编辑器工具栏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当打开对话框编辑器时，对话框编辑器工具栏自动出现在解决方案的顶端。  
  
### 对话框编辑器工具栏  
  
|图标|含义|图标|含义|  
|--------|--------|--------|--------|  
|![“测试对话框”按钮](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|测试对话框|![“横向间隔”按钮](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|水平均匀放置|  
|![“左对齐”按钮](../Image/vcDialogEditorAlignLefts.png "vcDialogEditorAlignLefts")|左对齐|![“纵向间隔”按钮](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|向下|  
|![“右对齐”按钮](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|右对齐|![“使宽度相同”按钮](../Image/vcDialogEditorSameWidth.png "vcDialogEditorSameWidth")|等宽|  
|![“顶端对齐”按钮](../Image/vcDialogEditorAlignTops.png "vcDialogEditorAlignTops")|顶端对齐|![“使高度相同”按钮](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|等高|  
|![“底端对齐”按钮](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|底端对齐|![“使大小相同”按钮](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|等大小|  
|![“垂直居中”按钮](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![“切换网格”按钮](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切换网格|  
|![“水平居中”按钮](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![“切换辅助线”按钮](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切换辅助线|  
  
 对话框编辑器工具栏包含用于在对话框上安排控件布局（如大小和对齐方式）的按钮。  对话框编辑器工具栏按钮对应于“格式”菜单。  有关详细信息，请参见[对话框编辑器的快捷键](../mfc/accelerator-keys-for-the-dialog-editor.md)。  
  
 在对话框编辑器中，通过从可用工具栏和窗口列表中选择对话框编辑器工具栏，可以切换它的显示。  
  
### 显示或隐藏对话框编辑器工具栏  
  
1.  在**“视图”**菜单上，单击**“工具栏”**，然后从子菜单中选择**“对话框编辑器”**。  
  
    > [!NOTE]
    >  当在对话框编辑器中打开对话框资源时，默认情况下将显示对话框编辑器工具栏；然而，如果显式关闭了此工具栏，下次打开对话框资源时需要调用它。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Dialog Editor](../mfc/dialog-editor.md)