---
title: 使用绘图工具 （图标的图像编辑器） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.drawing
dev_langs:
- C++
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 17211518789113c11194314b57b741ab2b274ddc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="using-a-drawing-tool-image-editor-for-icons"></a>使用绘图工具（图标的图像编辑器）
图像编辑器的手工绘制和擦除的工具都以相同的方式工作： 选择的工具，如有必要，[选择前景色和背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)和大小和形状的选项。 然后将指针移到映像并单击或拖动以绘制和擦除。  
  
 当选择**橡皮擦**工具，**画笔**工具，或**喷枪**工具，选项选择器将显示该工具的选项。  
  
> [!TIP]
>  而不是使用**橡皮擦**工具，你可能会发现它更方便地在使用一种绘制工具的背景色绘制。  
  
 你可以从选择绘图工具**图像编辑器**工具栏或**映像**菜单。  
  
### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>选择并使用从图像编辑器工具栏上的绘图工具  
  
1.  单击一个按钮**图像编辑器**工具栏。  
  
    -   **橡皮擦**工具绘制在当前的背景色图像上，当你按下鼠标左键时。  
  
    -   **铅笔**工具以一个像素的固定宽度手工绘制。  
  
    -   **选项选择器确定画笔工具的形状和大小**。  
  
    -   **喷枪**工具随机分布围绕中心画笔的颜色像素。  
  
        > [!TIP]
        >  当你将鼠标悬停光标在按钮上时会出现工具提示[图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)。 这些提示将帮助您识别特定此处提及的按钮。  
  
2.  如有必要，选择颜色和画笔：  
  
    -   在[调色板](../windows/colors-window-image-editor-for-icons.md)，单击鼠标左键以选择前景色或鼠标右键按钮以选择背景色。  
  
    -   在[选项选择器](../windows/toolbar-image-editor-for-icons.md)，单击表示你想要使用的画笔的形状。  
  
3.  指向你想要开始绘制的图像上绘制的位置。 指针将改变形状，根据你选择工具。  
  
4.  按鼠标左键 （适用于的前景色） 或鼠标右键按钮 （针对背景色），并按住它作为你绘图。  
  
### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>若要选择并使用图像菜单中的绘制工具  
  
1.  单击**映像**菜单，然后选择**工具**命令。  
  
2.  级联子菜单中，选择你想要使用的工具。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)   
 [处理颜色](../windows/working-with-color-image-editor-for-icons.md)

