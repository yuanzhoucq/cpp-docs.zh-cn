---
title: "Icons and Cursors: Image Resources for Display Devices (Image Editor for Icons) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.icon"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cursors [C++], creating"
  - "image resources, display devices"
  - "icons [C++], creating"
  - "cursors [C++], types"
  - "icons [C++]"
  - "Image editor [C++], icons and cursors"
  - "cursors [C++]"
  - "display devices, creating icons for"
  - "cursors [C++], hot spots"
  - "icons [C++], types"
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Icons and Cursors: Image Resources for Display Devices (Image Editor for Icons)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

图标和光标是图形资源，可以为不同类型的显示设备包含大小和配色方案不同的多个图像。 此外，光标还具有一个“热点”，即 Windows 用来跟踪其位置的位置。 可使用图像编辑器创建和编辑图标和光标以及位图和其他图像。  
  
 当创建新图标或光标时，图像编辑器首先会创建一个标准类型的图像。 图像最初用屏幕（透明）颜色填充。 如果图像是光标，热点最初是左上角（坐标为 0,0）。  
  
 默认情况下，图像编辑器支持为下表中所列的设备创建附加图像。 可以通过向[自定义图像对话框](../mfc/custom-image-dialog-box-image-editor-for-icons.md)中键入宽度、高度和色彩计数参数为其他设备创建图像。  
  
> [!NOTE]
>  你可以使用“图像编辑器”查看 32 位图像，但是不能对它们进行编辑。  
  
|颜色|宽度（像素）|高度（像素）|  
|--------|------------|------------|  
|单色|16|16|  
|单色|32|32|  
|单色|48|48|  
|单色|64|64|  
|单色|96|96|  
|16|16|16|  
|16|32|32|  
|16|64|64|  
|16|48|48|  
|16|96|96|  
|256|16|16|  
|256|32|32|  
|256|48|48|  
|256|64|64|  
|256|96|96|  
  
-   [创建新设备图像（图标或光标）](../mfc/creating-a-device-image-image-editor-for-icons.md)  
  
-   [为不同的显示设备添加图像](../mfc/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)  
  
-   [复制设备图像](../mfc/copying-a-device-image-image-editor-for-icons.md)  
  
-   [删除设备图像](../mfc/deleting-a-device-image-image-editor-for-icons.md)  
  
-   [在设备图像中创建透明或反转区域](../mfc/creating-transparent-or-inverse-regions-in-device-images.md)  
  
-   [创建 256 色图标或光标](../mfc/creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)  
  
-   [设置光标的作用点](../mfc/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 无  
  
## 请参阅  
 [Image Editor for Icons](../mfc/image-editor-for-icons.md)   
 [图标](http://msdn.microsoft.com/library/windows/desktop/ms646973)   
 [光标](http://msdn.microsoft.com/library/windows/desktop/ms646970)