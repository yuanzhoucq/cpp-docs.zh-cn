---
title: 图像菜单 （图标的图像编辑器 c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
helpviewer_keywords:
- Image menu
- Grid Settings dialog box [C++]
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
ms.openlocfilehash: e7d7d92401d5910cbb8aba8ab4c6000eca45cb01
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849725"
---
# <a name="image-menu-c-image-editor-for-icons"></a>图像菜单 （图标的图像编辑器 c + +）

**图像**时才会显示菜单**映像**编辑器处于活动状态，具有命令，用于编辑映像、 管理调色板，以及设置**的图像编辑器**窗口选项。 此外，使用设备映像的命令是可用时使用的图标和光标。

|命令|描述|
|---|---|
|**反转颜色**|反转颜色。 有关详细信息，请参阅[反转所选内容中的颜色](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md)。|
|**水平翻转**|水平翻转图像或选定内容。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。|
|**垂直翻转**|垂直翻转图像或选定内容。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。|
|**旋转 90 度**|将图像或选定内容旋转 90 度。 有关详细信息，请参阅[翻转图像](../windows/flipping-an-image-image-editor-for-icons.md)。|
|**显示颜色窗口**|此时将打开[颜色窗口](../windows/colors-window-image-editor-for-icons.md)，在其中可以选择要用于你的映像的颜色。 有关详细信息，请参阅[处理颜色](../windows/working-with-color-image-editor-for-icons.md)。|
|**所选内容用作画笔**|使你能够从图像的一部分创建自定义画笔。 你的选择将成为在图像中分布中所选内容的颜色的自定义画笔。 在拖动路径也会保留所选内容的副本。 您拖动的速度就越慢，进行更多副本。 有关详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。|
|**复制和大纲选择**|创建当前选定内容的副本并绘制其轮廓。 如果当前选定内容中包含的背景色，它将被排除在外已[透明](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)选定。
|**调整颜色**|此时将打开[自定义颜色选择器](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)，可用于自定义映像的使用的颜色。 有关详细信息，请参阅[自定义或更改颜色](../windows/customizing-or-changing-colors-image-editor-for-icons.md)。|
|**加载调色板**|此时将打开[加载调色板对话框](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md)，这样您就可以加载以前保存到.pal 文件的调色板颜色。|
|**保存调色板**|.Pal 文件将保存调色板颜色。|
|**绘制不透明**|选定，将使当前所选内容不透明。 未选中状态，将使当前所选内容透明。 有关详细信息，请参阅[选择透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。|
|**工具栏编辑器**|此时将打开[新建工具栏资源对话框](../windows/new-toolbar-resource-dialog-box.md)。|
|**网格设置**|此时将打开**网格设置**映像可以在其中指定网格的对话框。|
|**新建图像类型**|此时将打开[新建\<设备 > 图像类型对话框](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md)。 单个图标资源可以包含不同大小的多个映像，windows 可以使用相应的图标大小，具体取决于将如何显示。 新的设备类型不会修改该图标的大小，但而不是创建图标中的新映像。 仅适用于图标和光标。|
|**当前图标/光标图像类型**|将打开子菜单，其中列出了前几个可用的游标或图标映像 （前九个）。 最后一个命令在子菜单，**更多...**，打开[开放\<设备 > 图像对话框的](../windows/open-device-image-dialog-box-image-editor-for-icons.md)。|
|**删除图像类型**|删除所选的设备映像。|
|**工具**|启动包含所有可用工具的子菜单[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)。|

**网格设置**对话框允许您指定映像的网格设置和编辑图像上显示网格线。 行可用于编辑映像，而不保存为图像本身的一部分。

|属性|描述|
|---|---|
|**像素网格**|选中时，图像编辑器中显示一个网格，每个像素周围。 仅在 4 × 及更高分辨率显示网格。|
|**磁贴网格**|选中时，显示的像素为单位的块周围的网格中网格间距值所指定的图像编辑器。|
|**Width**|指定每个磁贴块的宽度。 绘制位图包含按固定间隔排列的多个映像时，此属性很有用。|
|**Height**|指定每个磁贴块的高度。 绘制位图包含按固定间隔排列的多个映像时，此属性很有用。|

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[调整图像大小](../windows/resizing-an-image-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)