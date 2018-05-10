---
title: 在设备图像 （图标的图像编辑器） 中创建透明或反转区域 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors, device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices, transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects, transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70fd2411eefba495478baaf5fb20fe7a27031001
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>在设备图像中创建透明或反色区域（图标的图像编辑器）
在[图像编辑器](../windows/image-editor-for-icons.md)，初始图标或光标图像具有透明特性。 尽管图标和光标映像为矩形，许多不会显示，因为图像的部分都是透明的;通过图标或光标显示在屏幕上的基础映像。 当拖动图标时，图像的部分可能以反转的颜色。 通过设置屏幕颜色和中的反转颜色创建此效果[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。  
  
 屏幕和反转颜色将应用于图标，游标形状和颜色导出的图像或者指定反转区域。 这些颜色指示图像中具有这些属性的部分。 你可以更改表示中编辑屏幕颜色和反色属性的颜色。 这些更改不会影响图标或光标位于你的应用程序的外观。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅 [在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-create-transparent-or-inverse-regions"></a>若要创建透明或反转区域  
  
1.  在**颜色**窗口中，单击**屏幕颜色**选择器或**反色**选择器。  
  
2.  应用的屏幕或反色到你使用绘图工具的映像。 绘图工具的详细信息，请参阅[使用绘图工具](using-a-drawing-tool-image-editor-for-icons.md)。  
  
### <a name="to-change-the-screen-or-inverse-color"></a>若要更改屏幕或反转颜色  
  
1.  选择**屏幕颜色**选择器或**反色**选择器。  
  
2.  选择一种颜色从**颜色**调色板中的**颜色**窗口。  
  
     补色自动指定为另一个选择器。  
  
    > [!TIP]
    >  如果双击屏幕颜色或反色选择器[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)显示。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

