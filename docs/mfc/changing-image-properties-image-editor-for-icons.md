---
title: "Changing Image Properties (Image Editor for Icons) | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "images [C++], properties"
  - "Image editor [C++], Properties window"
  - "Image editor [C++], image properties"
  - "Properties window, image editor"
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing Image Properties (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用[“属性”窗口](../Topic/Properties%20Window.md)设置或修改图像的属性。  
  
### 更改图像的属性  
  
1.  在图像编辑器中打开图像。  
  
2.  在**“属性”**窗口中，更改图像的任何属性或全部属性。  
  
    |属性|说明|  
    |--------|--------|  
    |**Colors**|指定图像的配色方案。  选择单色、16 色、256 色或真彩色。  如果已经用 16 色调色板绘制图像，选择单色将导致用黑色和白色替换图像中的颜色。  并不总是保持对比度：例如，红色和绿色的邻近区域都被转换为黑色。|  
    |**Filename**|指定图像文件的名称。  默认情况下，Visual Studio 分配一个基文件名，该基文件名是通过从默认资源标识符 \(IDB\_BITMAP1\) 中移除前四个字符（“IDB\_”）并添加适当的扩展名创建的。  在本例中，图像的文件名为 BITMAP1.bmp。  可以将它重命名为 MYBITMAP1.bmp。|  
    |**高度**|设置图像的高度（以像素为单位）。  默认值为 48。  裁剪图像或在现有图像下面添加空白区域。|  
    |**ID**|设置资源的标识符。  默认情况下，Microsoft Visual Studio 为图像分配系列 IDB\_BITMAP1、IDB\_BITMAP2 等中的下一个可用的标识符。  图标和光标使用相似的名称。|  
    |**Palette**|更改颜色属性。  双击以选择一种颜色并显示[“调整颜色”对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。  通过在适当的文本框中键入 RGB 或 HSL 值定义颜色。|  
    |**SaveCompressed**|指示图像是否为压缩格式。  此属性为只读。  Visual Studio 不允许用压缩格式保存图像，因此对于任何在 Visual Studio 中创建的图像，此属性将为 **False**。  如果在 Visual Studio 中打开压缩图像（它在另一个程序中创建），此属性将为 **True**。  如果使用 Visual Studio 保存压缩图像，图像将被解压缩，而且此属性将恢复为 **False**。|  
    |**宽度**|设置图像的宽度（以像素为单位）。  位图的默认值为 48。  裁剪图像或在现有图像的右侧添加空白区域。|  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 无  
  
## 请参阅  
 [Accelerator Keys](../mfc/accelerator-keys-image-editor-for-icons.md)   
 [Editing Graphical Resources](../mfc/editing-graphical-resources-image-editor-for-icons.md)   
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)