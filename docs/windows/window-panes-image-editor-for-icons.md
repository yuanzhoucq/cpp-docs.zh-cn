---
title: 窗口窗格 （图标的图像编辑器） |Microsoft 文档
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
ms.openlocfilehash: e899729e70db089c1c55f00aa9c4196a22c67060
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="window-panes-image-editor-for-icons"></a>窗口窗格（图标的图像编辑器）
图像编辑器窗口通常显示两个窗格隔开拆分条中的图像。 其中一个视图是实际大小和其他扩大 （默认放大因子为 6）。 这两个窗格中的视图都将自动更新： 立即显示另一部分中的两侧加上一个窗格中所做的更改。 两个窗格方便在你的映像，在其中你可以区分单个像素并，同时，观察对映像的实际大小视图所做的工作的影响的放大视图上工作。  
  
 左窗格中使用根据所是空间需要 （最多的一半图像窗口） 显示的图像 1:1 放大倍数视图 （默认值）。 右窗格中显示缩放的图像 （默认情况下 6:1 放大倍数）。 你可以[更改放大倍数](../windows/changing-the-magnification-factor-image-editor-for-icons.md)中每个窗格使用**放大**工具上[图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)或通过使用加速键。  
  
 可以放大的图像编辑器窗口的较小窗格中，还可以使用两个窗格显示的较大的图像的不同区域。 在窗格中单击以将其选中。  
  
 可以通过将指针定位在拆分栏并向左或向右移动拆分栏来更改窗格的相对大小。 如果你想要在只有一个窗格中，拆分栏可以移动到任意一侧。  
  
 如果图像编辑器窗格被放大 4 或更高版本的因素，则可以[显示像素网格](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md)分隔映像中的单个像素。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)

