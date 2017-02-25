---
title: "Saving Bitmaps as GIFs or JPEGs (Image Editor for Icons) | Microsoft Docs"
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
  - ".gif files, saving bitmaps as"
  - "jpg files, saving bitmaps as"
  - "jpeg files, saving bitmaps as"
  - ".jpg files, saving bitmaps as"
  - "Image editor [C++], converting image formats"
  - "gif files, saving bitmaps as"
  - "bitmaps [C++], converting formats"
  - ".jpeg files, saving bitmaps as"
  - "graphics [C++], converting formats"
  - "images [C++], converting formats"
ms.assetid: 115df69f-10fb-4e6f-906b-853c1e4a54af
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Saving Bitmaps as GIFs or JPEGs (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建位图时，该图像以位图格式 \(.bmp\) 创建。  然而，可以将此图像保存为 GIF 或 JPEG 格式或以其他图形格式保存。  
  
> [!NOTE]
>  此处理不适用于图标和光标。  
  
### 创建位图并保存为 .gif 或 .jpeg  
  
1.  从“文件”菜单中选择“打开”，然后单击“文件”。  
  
2.  在**“新建文件”**对话框中，单击 **Visual C\+\+** 文件夹，然后在**“模板”**框中选择**“位图文件\(.bmp\)”**并单击**“打开”**。  
  
     位图在图像编辑器中打开。  
  
3.  根据需要对新的位图进行更改。  
  
4.  在位图仍在图像编辑器中打开的情况下，单击**“文件”**菜单上的**“*filename*.bmp 另存为”**。  
  
5.  在**“另存文件为”**对话框中，在**“文件名”**框中键入要提供给此文件的名称和表示所需文件格式的扩展名。  例如，myfile.gif。  
  
     **注意** 必须在项目外部创建或打开位图以便将它保存为其他文件格式。  如果在项目内部创建或打开位图，则**“另存为”**命令将不可用。  有关更多信息，请参见[在项目外查看资源脚本文件中的资源（独立运行）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
6.  单击**“保存”**。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 请参阅  
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)