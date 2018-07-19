---
title: 图像菜单 （图标的图像编辑器） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- Image menu
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bfeeda8d358bf3144cd5c3168686561b3586581
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880525"
---
# <a name="image-menu-image-editor-for-icons"></a>“图像”菜单（图标的图像编辑器）
图像菜单，仅在图像编辑器处于活动状态时，才显示，提供用于编辑图像、 管理调色板，和设置的图像编辑器窗口选项的命令。 此外，使用设备图像提供了个命令使用图标和光标时。  
  
 **反转颜色**  
 反转颜色。 有关详细信息，请参阅[反转选定内容中的颜色](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)。  
  
 **水平翻转**  
 水平翻转图像或选定内容。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。  
  
 **垂直翻转**  
 垂直翻转图像或选定内容。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。  
  
 **旋转 90 度**  
 将图像或选定内容旋转 90 度。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。  
  
 **显示颜色窗口**  
 打开[颜色窗口](../windows/colors-window-image-editor-for-icons.md)，在其中可以选择要用于你的映像的颜色。 有关详细信息，请参阅[处理颜色](../windows/working-with-color-image-editor-for-icons.md)。  
  
 **所选内容用作画笔**  
 使用此选项可从映像的一部分创建自定义画笔。 你的选择将成为一个自定义画笔，它在图像中分布中所选内容的颜色。 在拖动路径也会保留所选内容的副本。 拖动时速度就越慢，进行更多副本。 有关详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。  
  
 **复制和选定内容的轮廓**  
 创建当前选定内容的副本并绘制其轮廓。 如果当前选定内容中包含的背景色，它将被排除在外必须[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)选。  
  
 **调整颜色**  
 打开[自定义颜色选择器](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)，该编辑器可以自定义用于你的映像的颜色。 有关详细信息，请参阅[自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。  
  
 **加载调色板**  
 打开[加载调色板对话框](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)，这样您就可以加载以前保存到.pal 文件的调色板颜色。  
  
 **保存调色板**  
 到.pal 文件将保存调色板颜色。  
  
 **绘制不透明**  
 当选中时，使当前所选内容不透明。 清除时，使当前所选内容透明。 有关详细信息，请参阅[选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。  
  
 **工具栏编辑器**  
 打开[新建工具栏资源对话框](../windows/new-toolbar-resource-dialog-box.md)。  
  
 **网格设置**  
 打开[网格设置对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md)在其中可以指定你的映像的网格。  
  
 **新映像类型**  
 打开[新建\<设备 > 图像类型对话框](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)。 一个图标资源可以包含多个映像的不同的大小;windows 可以使用相应的图标大小，具体取决于将如何显示。 新的设备类型不会修改在图标的大小，但而是创建图标中的新映像。 仅适用于图标和光标。  
  
 **当前的图标/光标图像类型**  
 打开一个子菜单，其中列出了前几个可用的光标或图标映像 （前九个）。 在子菜单中，最后一个命令**更...**，打开[打开\<设备 > 图像对话框](../windows/open-device-image-dialog-box-image-editor-for-icons.md)。  
  
 **删除映像类型**  
 删除所选的设备映像。  
  
 **工具**  
 启动的子菜单，其中包含所有可用的工具[图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)。  
  
## <a name="requirements"></a>要求  
 无  
  
## <a name="see-also"></a>请参阅  
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)

