---
title: "Editing Parts of an Image (Image Editor for Icons) | Microsoft Docs"
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
  - "Image editor [C++], editing images"
  - "Clipboard [C++], pasting"
  - "images [C++], editing"
  - "images [C++], deleting selected parts"
  - "images [C++], copying selected parts"
  - "images [C++], moving selected parts"
  - "images [C++], dragging and replicating selected parts"
  - "images [C++], pasting into"
  - "graphics [C++], editing"
ms.assetid: ff4f5fef-71a4-4fd8-825e-049399fed391
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Editing Parts of an Image (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以对[选定内容](../mfc/selecting-an-area-of-an-image-image-editor-for-icons.md)执行标准的编辑操作，包括剪切、复制、清除和移动，而不管选定内容是整个图像还是仅是图像的一部分。  由于图像编辑器使用 Windows 剪贴板，所以可以传输图像在图像编辑器和其他应用程序之间对于 Windows。  
  
 另外，可以调整选定内容的大小，不论它是包括整个图像还是只包括图像的一部分。  
  
### 剪切当前选定内容并将其移动至剪贴板  
  
1.  在“编辑”菜单上单击“剪切”。  
  
### 复制选定内容  
  
1.  将指针置于选定内容边框内部或选定内容边框上除尺寸柄以外的任意位置。  
  
2.  在将选定内容拖动至新位置时按住 **Ctrl** 键。  原始选定内容的区域不更改。  
  
3.  若要将选定内容复制到图像中的当前位置，请在选定内容光标外部单击。  
  
### 将剪贴板内容粘贴到图像中  
  
1.  从“编辑”菜单中选择“粘贴”。  
  
     被选定内容边框环绕着的剪贴板内容出现在窗格的左上角。  
  
2.  将指针置于选定内容边框内部并将图像拖动到图像上的所需位置。  
  
3.  若要在新位置锚定图像，请在选定内容边框外部单击。  
  
### 删除当前选定内容（在不将其移动到剪贴板的情况下）  
  
1.  从“编辑”菜单中选择“删除”。  
  
     用当前背景色填充选定内容的原始区域。  
  
    > [!NOTE]
    >  通过在“资源视图”窗口中右击可以访问“剪切”、“复制”、“粘贴”和“删除”命令。  
  
### 移动选定内容  
  
1.  将指针置于选定内容边框内部或选定内容边框上除尺寸柄以外的任意位置。  
  
2.  将选定内容拖动到新位置。  
  
3.  若要在新位置锚定图像中的选定内容，请在选定内容边框外部单击。  
  
 有关用选定内容绘制的更多信息，请参见[创建自定义画笔](../mfc/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)