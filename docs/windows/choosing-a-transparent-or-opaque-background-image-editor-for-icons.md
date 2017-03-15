---
title: "Choosing a Transparent or Opaque Background (Image Editor for Icons) | Microsoft Docs"
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
  - "opaque backgrounds"
  - "background colors, images"
  - "colors [C++], image"
  - "Image editor [C++], transparent or opague backgrounds"
  - "background images"
  - "images [C++], transparency"
  - "images [C++], opaque background"
  - "transparent backgrounds"
  - "transparency, background"
  - "transparent backgrounds, images"
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Choosing a Transparent or Opaque Background (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当从图像中移动或复制选定内容时，选定内容中匹配当前背景色的任何像素在默认情况下都是透明的；它们不遮掩目标位置中的像素。  
  
 您可以从透明背景（默认情况）切换到不透明背景，然后再切换回去。  当使用选择工具时，“透明背景”和“不透明背景”选项出现在“图像编辑器”工具栏上的“选项”选择器中（如下所示）。  
  
 ![背景选项 &#45; 不透明或透明](../Image/vcImageEditorOpaqTranspBack.gif "vcImageEditorOpaqTranspBack")  
在“图像编辑器”工具栏上的透明和不透明选项  
  
### 在透明背景和不透明背景之间切换  
  
1.  在**“图像编辑器”**工具栏中，单击**“选项”**选择器，然后单击适当的背景：  
  
    -   **不透明背景 \(O\)**：现有图像被选定内容的所有部分遮掩。  
  
    -   **透明背景 \(T\)**：现有图像透过选定内容中匹配当前背景色的部分显示。  
  
 \- 或 \-  
  
-   在“图像”菜单上选择或清除“不透明处理”。  
  
 在选定内容已经生效时，可以更改背景色以更改图像的哪一部分透明。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Working with Color](../mfc/working-with-color-image-editor-for-icons.md)