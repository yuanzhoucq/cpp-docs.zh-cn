---
title: 自定义或更改颜色（图标的图像编辑器）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.customcolorselector
helpviewer_keywords:
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
ms.assetid: e58f6b32-f435-4d9a-a570-7569433661ae
ms.openlocfilehash: 7ab353ad0aa22c74eeba58e9310d9bc0f8d5a832
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560278"
---
# <a name="customizing-or-changing-colors-image-editor-for-icons"></a>自定义或更改颜色（图标的图像编辑器）

**图像**编者[调色板](../windows/colors-window-image-editor-for-icons.md)最初显示 16 种标准颜色。 使用显示的颜色，还可以创建您自己的自定义颜色。 然后，可以[保存和加载自定义的调色板](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md)。

**自定义颜色选择器**对话框中，可自定义映像的使用的颜色。 是包含的以下属性：

|属性|描述|
|---|---|
|**渐变颜色显示**|更改所选颜色的值。 你想要更改位置十字线颜色。 然后移动滑块向上或向下更改亮度或颜色的 RGB 值。|
|**亮度栏**|设置中选择的颜色的亮度**渐变颜色显示**框。 选择并拖动了更高的亮度条形的白色箭头或向下的翻更少。 **颜色**框显示所选的颜色和亮度设置的效果。|
|**Color**|列出了你定义的颜色的色调 （颜色滚轮值）。 值的范围介于 0 到 240 之间，其中 0 是红色 60 为黄色，120 是绿色、 180 青色、 洋红色，可以是 200，是 240 为蓝色。|
|**Hue**|列出了你定义的颜色的色调 （颜色滚轮值）。 值的范围介于 0 到 240 之间，其中 0 是红色 60 为黄色，120 是绿色、 180 青色、 洋红色，可以是 200，是 240 为蓝色。|
|**Sat**|指定正在定义的颜色的饱和度值。 饱和度是中指定的色调颜色量。 值的范围从 0 到 240。|
|**Lum**|列出了你定义的颜色的亮度 （亮度）。 值的范围从 0 到 240。|
|**红色**|指定正在定义的颜色的红色值。 值范围从 0 到 255 之间。|
|**绿色**|指定正在定义的颜色的绿色值。 值范围从 0 到 255 之间。|
|**Blue**|指定正在定义的颜色的蓝色值。 值范围从 0 到 255 之间。|

## <a name="to-change-colors-on-the-colors-palette"></a>更改调色板上的颜色

1. 从**图像**菜单中，选择**调整颜色**。

1. 在中**自定义颜色选择器**对话框框中，通过在相应的文本框中键入 RGB 或 HSL 值定义的颜色或选择中的颜色**渐变颜色显示**框。

1. 通过移动滑块来设置亮度**亮度**栏。

1. 许多自定义颜色是抖色。 如果要纯色最接近于抖色，双击**颜色**框。

   如果你以后决定要抖的色，移动滑块**亮度**条形图或将十字线移**渐变颜色显示**框再次还原抖色。

1. 选择**确定**以添加新的颜色。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[处理颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[图像菜单](../windows/image-menu-image-editor-for-icons.md)<br/>
[颜色窗口](../windows/colors-window-image-editor-for-icons.md)