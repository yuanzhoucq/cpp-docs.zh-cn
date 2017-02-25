---
title: "Selecting an Area of an Image (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.image.editing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Image editor [C++], image selection"
  - "Image editor [C++], selecting images"
  - "images [C++], selecting"
  - "cursors [C++], selecting areas of"
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Selecting an Area of an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用选择工具定义要剪切、复制、清除、调整大小、反转或移动的图像区域。  使用“矩形选择”工具可以定义和选择图像中的矩形区域。  使用“不规则选择”工具可以手工绘制您要选择以执行剪切、复制或其他操作的区域的轮廓。  
  
> [!NOTE]
>  请参见[“图像编辑器”工具栏](../mfc/toolbar-image-editor-for-icons.md)中给出的**“矩形选择”**和**“不规则选择”**工具，或查看与**“图像编辑器”**工具栏上的每个按钮相关的“工具”提示。  
  
 还可以从选定内容中创建自定义画笔。  有关更多信息，请参见[创建自定义画笔](../mfc/creating-a-custom-brush-image-editor-for-icons.md)。  
  
### 选择图像的区域  
  
1.  在“图像编辑器”工具栏上（或从“工具”命令 \-\>“图像”菜单），单击要选择的工具。  
  
2.  将插入点移动到要选择的图像区域的一角。  当插入点位于图像上方时会出现十字型光标。  
  
3.  将插入点拖动到要选择的区域的对角。  矩形显示将选择哪些像素。  矩形内部的所有像素（包括那些矩形下面的像素）都被包括在选定内容中。  
  
4.  释放鼠标按钮。  选定内容边框封闭选定区域。  
  
### 选择整个图像  
  
1.  在当前选定内容外部单击图像。  选定内容边框更改焦点并重新包围整个图像。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)