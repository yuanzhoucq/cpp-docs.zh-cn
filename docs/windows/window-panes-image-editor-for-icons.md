---
title: 窗口窗格 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a38341f6c6bcbcdec6bb4e6f5e5820fa759e6dab
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652019"
---
# <a name="window-panes-image-editor-for-icons"></a>窗口窗格（图标的图像编辑器）
**的图像编辑器**窗口通常由拆分栏分隔两个窗格中显示图像。 其中一个视图是实际大小和其他被放大 （默认的放大因子为 6）。 这两个窗格中的视图会自动更新： 其他立即显示在一个窗格中所做的更改。 两个窗格轻松处理的映像，在其中可以区分单个像素并，同时，观察其对图像的实际大小视图所做的工作的影响的放大视图。  
  
 左窗格中使用所需空间 (最多一半**图像**窗口) 以显示你的映像的 1:1 放大视图 （默认值）。 右窗格显示缩放的图像 （默认情况下 6:1 放大倍数）。 你可以[更改放大倍数](../windows/changing-the-magnification-factor-image-editor-for-icons.md)中每个窗格使用**放大**上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)或通过使用加速键。  
  
 您可以扩大的较小的窗格**的图像编辑器**窗口并使用两个窗格显示大图像的不同区域。 单击在窗格中，以将其选中。  
  
 可以通过将指针定位在拆分栏和向右或向左移动拆分条来更改窗格的相对大小。 如果你想要在只有一个窗格中，在拆分栏可以移动到任意一侧。  
  
 如果**的图像编辑器**窗格处于放大 4 倍或更高版本，你可以[显示像素网格](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)分隔在图像中的单个像素。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [加速键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)