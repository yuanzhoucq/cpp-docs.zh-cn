---
title: 选择透明或不透明背景 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- opaque backgrounds
- background colors, images
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- background images
- images [C++], transparency
- images [C++], opaque background
- transparent backgrounds
- transparency, background
- transparent backgrounds, images
ms.assetid: 61b743d9-c86b-405d-9a81-0806431b4363
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c8a809e7cd7ed7a461149707cc9e0b2a4a62158
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649515"
---
# <a name="choosing-a-transparent-or-opaque-background-image-editor-for-icons"></a>选择透明或不透明背景（图标的图像编辑器）
移动或复制所选内容从映像，所选内容与当前的背景色匹配的任何像素时，默认情况下，透明;它们不清楚在目标位置中的像素为单位。  
  
 可以从透明背景 （默认值） 切换到不透明背景，并后又返回。 当使用选择工具时，**透明背景**并**不透明背景**选项出现在**选项**上的选择器**的图像编辑器**工具栏 （如下所示）。  
  
 ![背景选项&#45;不透明或透明](../windows/media/vcimageeditoropaqtranspback.gif "vcImageEditorOpaqTranspBack")  
**透明且不透明选项**上**的图像编辑器工具栏**  
  
### <a name="to-switch-between-a-transparent-and-opaque-background"></a>若要切换透明且不透明背景  
  
1.  在中**的图像编辑器**工具栏上，单击**选项**选择器，然后单击适当的背景：  
  
    -   `Opaque Background (O)`： 现有的映像将被遮盖的所选内容的所有部件。  
  
    -   `Transparent Background (T)`： 现有图显示了与当前的背景色匹配所选内容的部件。  
  
 \- 或 -  
  
-   上**图像**菜单上，选中或清除**绘制不透明**。  
  
 选择已在要更改的图像的哪些部分是透明的效果时，可以更改背景色。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [加速键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [处理颜色](../windows/working-with-color-image-editor-for-icons.md)