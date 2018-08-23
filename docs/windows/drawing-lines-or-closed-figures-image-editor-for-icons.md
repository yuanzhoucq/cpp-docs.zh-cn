---
title: 绘制线条或闭合的图形 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- closed figures, drawing
- lines [C++], painting
- lines [C++], drawing
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d1eba17d961db9ec96e4250e49c10ecad5b75b4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590725"
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>绘制线条或闭合图形（图标的图像编辑器）

图像编辑器工具用于绘制线条和所有闭合的图形工作相同的方式： 将插入点放在某个时间点并拖动到另一个。 对于行，这些点是终结点。 为闭合图形，这些点是边框的相反图的角。

宽度由当前画笔选项，绘制线条空心的图形绘制，以确定由当前宽度选定内容的宽度。 行和所有的图形，同时构建框架和填充，绘制或当前的背景色中的当前前景色如果按鼠标左键，如果按鼠标右键。

### <a name="to-draw-a-line"></a>若要绘制的线条

1. 上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)(或从**映像**菜单中，**工具**命令)，单击**行**工具。

2. 如有必要，选择颜色和画笔：

   - 在中[颜色调色板](../windows/colors-window-image-editor-for-icons.md)，单击鼠标左键以选择前景色或鼠标右键按钮以选择背景色。

   - 在中[选项选择器](../windows/toolbar-image-editor-for-icons.md)，单击表示你想要使用的画笔的形状。

3. 将指针放置在该行的起始点。

4. 将拖到行的终结点。

### <a name="to-draw-a-closed-figure"></a>若要绘制闭合的图形

1. 上**的图像编辑器**工具栏 (或从**映像**菜单中，**工具**命令)，单击**封闭图绘制**工具。

   **封闭图绘制**工具按照其各自的按钮上的指示创建图形。

2. 如有必要，选择颜色和线条宽度。

3. 将指针移动到您要在其中绘制图的矩形区域的一角。

4. 到对角拖动指针。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[加速键](../windows/accelerator-keys-image-editor-for-icons.md)  
[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[图标的图像编辑器](../windows/image-editor-for-icons.md)  
[处理颜色](../windows/working-with-color-image-editor-for-icons.md)