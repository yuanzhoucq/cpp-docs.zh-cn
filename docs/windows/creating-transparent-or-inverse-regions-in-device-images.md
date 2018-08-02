---
title: 在设备图像 （图标的图像编辑器） 中创建透明或反转区域 |Microsoft Docs
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
ms.openlocfilehash: c8ebecf984254175a15075e8d8a4125f9fc5ec17
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462529"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>在设备图像中创建透明或反色区域（图标的图像编辑器）
在中[的图像编辑器](../windows/image-editor-for-icons.md)，初始的图标或光标图像有透明特性。 尽管图标和光标图像矩形，但许多不会出现，因为图像的部分都是透明的;通过图标或光标显示在屏幕上的基础映像。 当您拖动的图标图像的部分可能会出现在倒排的颜色。 通过设置屏幕颜色和中的反转颜色创建这种效果[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。  
  
 屏幕和反转颜色将应用于图标和光标形状，颜色派生的映像或者指定反转区域。 这些颜色指示图像中具有这些属性的部分。 您可以更改表示屏幕颜色和反色中编辑属性的颜色。 这些更改不会影响应用程序中的光标的图标的外观。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[在 Visual Studio 中自定义开发设置](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-create-transparent-or-inverse-regions"></a>若要创建透明或反转区域  
  
1.  在中**颜色**窗口中，单击**屏幕颜色**选择器或**反色**选择器。  
  
2.  将应用的屏幕或使用绘图工具在图像上的反转颜色。 有关绘图工具的详细信息，请参阅[使用绘图工具](using-a-drawing-tool-image-editor-for-icons.md)。  
  
### <a name="to-change-the-screen-or-inverse-color"></a>若要更改屏幕或反转颜色  
  
1.  选择任一**屏幕颜色**选择器或**反色**选择器。  
  
2.  选择从一种颜色**颜色**中的调色板**颜色**窗口。  
  
     补色被自动指定为另一个选择器。  
  
    > [!TIP]
    >  如果您双击屏幕颜色或反转颜色选择器中，[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)出现。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [加速键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)