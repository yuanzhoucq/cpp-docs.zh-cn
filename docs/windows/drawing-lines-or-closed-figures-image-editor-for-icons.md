---
title: "绘制线条或闭合的图形 （图标的图像编辑器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- closed figures, drawing
- lines [C++], painting
- lines [C++], drawing
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c2f5169c6340b756c31e1986e46b52f48b4edd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>绘制线条或闭合图形（图标的图像编辑器）
图像编辑器工具用于绘制线条和所有闭合的图形工作方式相同： 你将插入点放在某个时间点并将其拖到另一个。 对于行，这些点是终结点。 为闭合图形，这些点是对角边界图的矩形。  
  
 行由当前画笔选定内容宽度中绘制空心的图形绘制，以由当前的宽度所选内容宽度。 行和所有的图形，同时确定框架，并填写，绘制或当前的背景色中的当前前景色如果按鼠标左键，如果您按下鼠标右键按钮。  
  
### <a name="to-draw-a-line"></a>若要绘制线条  
  
1.  上[图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)(或从**映像**菜单上，**工具**命令)，单击**行**工具。  
  
2.  如有必要，选择颜色和画笔：  
  
    -   在[调色板](../windows/colors-window-image-editor-for-icons.md)，单击鼠标左键以选择前景色或鼠标右键按钮以选择背景色。  
  
    -   在[选项选择器](../windows/toolbar-image-editor-for-icons.md)，单击表示你想要使用的画笔的形状。  
  
3.  将指针放在行的起始点。  
  
4.  将拖到行的终结点。  
  
### <a name="to-draw-a-closed-figure"></a>若要绘制闭合的图形  
  
1.  上**图像编辑器**工具栏 (或从**映像**菜单上，**工具**命令)，单击**封闭图绘制**工具。  
  
     **封闭图绘制**工具按照其各自的按钮上的指示创建图形。  
  
2.  如有必要，选择颜色和线条宽度。  
  
3.  将指针移动到你要在其中绘制图的矩形区域的一个角。  
  
4.  将指针拖到对角。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 惠?  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)   
 [处理颜色](../windows/working-with-color-image-editor-for-icons.md)

