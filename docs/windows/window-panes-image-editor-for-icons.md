---
title: 窗口窗格（图标的图像编辑器）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: 72b7cf056147cdbd216d861f0e710da423951c5a
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560304"
---
# <a name="window-panes-image-editor-for-icons"></a>窗口窗格（图标的图像编辑器）

**的图像编辑器**窗口通常由拆分栏分隔两个窗格中显示图像。 其中一个视图是实际大小和其他被放大 （默认的放大因子为 6）。 这两个窗格中的视图会自动更新： 其他立即显示在一个窗格中所做的更改。 两个窗格轻松处理的映像，在其中可以区分单个像素并，同时，观察其对图像的实际大小视图所做的工作的影响的放大视图。

左窗格中使用所需空间 (最多一半**图像**窗口) 以显示你的映像的 1:1 放大视图 （默认值）。 右窗格显示缩放的图像 （默认情况下 6:1 放大倍数）。 你可以在每个窗格使用放大倍数**Magnify**上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)或通过使用加速键。

您可以扩大的较小的窗格**的图像编辑器**窗口并使用两个窗格显示大图像的不同区域。 选择窗格中选择它。

可以通过将指针定位在拆分栏和向右或向左移动拆分条来更改窗格的相对大小。 如果你想要在只有一个窗格中，在拆分栏可以移动到任意一侧。

如果**的图像编辑器**窗格处于放大 4 倍或更高版本，可以显示像素网格在图像中的单个像素的界限。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="to-change-the-magnification-factor"></a>若要更改放大因子

默认情况下**图像**编辑器以实际大小的左窗格中显示的视图和 6 个在右窗格中的查看时间实际大小。 放大因子 （在工作区底部的状态栏中所示） 是图像的实际大小和显示的大小之间的比率。 默认因子为 6，范围是从 1 到 10。

1. 选择**的图像编辑器**你想要更改其放大因子窗格。

1. 上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)，选择右侧的箭头[放大工具](../windows/toolbar-image-editor-for-icons.md)和从子菜单中选择缩放系数：**1 X**， **2 X**， **6 X**，或**8 X**。

   > [!NOTE]
   > 若要选择中列出的内容中的放大因子**Magnify**工具中，使用加速键。

## <a name="to-display-or-hide-the-pixel-grid"></a>若要显示或隐藏像素网格

为所有**的图像编辑器**放大因子为 4 或更高版本的窗格，可以显示一个网格在图像中的单个像素的界限。

1. 上**图像**菜单中，选择**网格设置**。

1. 选择**像素网格**复选框以显示网格中，或清除相应的框以隐藏网格。

> [!TIP]
> 将鼠标光标悬停工具栏按钮上时，会出现工具提示。 这些提示可以帮助您确定每个按钮的功能。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)