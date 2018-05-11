---
title: 图标的图像编辑器 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, images
- resource editors, graphics
- Image editor [C++]
- resource editors, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 41c4bf71d8d3479f8353c1f57e725f07926dee47
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="image-editor-for-icons"></a>图标的图像编辑器
图像编辑器具有一组丰富的图像创建和编辑工具，以及有助于创建工具栏位图的功能。 除了位图、图标和光标，你还可以使用 **“图像”** 菜单上的命令和 **“图像编辑器”** 工具栏上的工具来编辑 GIF 或 JPEG 格式的图像。  
  
 使用图像编辑器，可以执行下列操作：  
  
-   [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)  
  
-   [处理颜色](../windows/working-with-color-image-editor-for-icons.md)  
  
-   [处理图标和光标：显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)  
  
-   [使用图像编辑器命令的快捷键](../windows/accelerator-keys-image-editor-for-icons.md)  
  
 “图像编辑器”窗口显示图像的两个视图，并用一个拆分条将这两个窗格隔开。 你可以将拆分条从一端拖动到另一端来更改窗格的相对大小。 活动窗格将显示选择边框。  
  
 可以对“图像编辑器”窗口进行调整以适合你的需要和喜好。 你可以 [更改放大因子](../windows/changing-the-magnification-factor-image-editor-for-icons.md) 以及 [显示或隐藏像素网格](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)。  
  
> [!NOTE]
>  你可以使用“图像编辑器”查看 32 位图像，但是不能对它们进行编辑。  
  
## <a name="visual-studio-image-library"></a>Visual Studio 图像库  
 你可以免费下载 Visual Studio 图像库，其中包含的许多动画、位图和图标均可用于你的应用程序。 有关如何下载库的详细信息，请参阅 [Visual Studio 图像库](/visualstudio/designers/the-visual-studio-image-library)。  
  
## <a name="managed-resources"></a>托管资源  
 你可以使用图像编辑器和 [二进制编辑器](binary-editor.md) 处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
### <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [资源编辑器](../windows/resource-editors.md)   
 [图标](http://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)

