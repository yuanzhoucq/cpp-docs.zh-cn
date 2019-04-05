---
title: 如何：使用绘图工具
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: 7b362749c9a5cb1c7ec77e5cac8625aa7eb260f0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037784"
---
# <a name="how-to-use-a-drawing-tool"></a>如何：使用绘图工具

**的图像编辑器**具有的手绘图和擦除工具都以相同方式工作。 选择的工具，如有必要，[选择前景色和背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)和大小和形状选项。 然后将指针移动到图像并单击或拖动以绘制和擦除。

## <a name="drawing-tools"></a>绘图工具

可以从选择绘图工具**的图像编辑器**工具栏或**映像**菜单。 当选择**橡皮擦**工具**画笔**工具，或**喷枪**工具，选项选择器将显示该工具的选项。

> [!TIP]
>  当您将光标悬停按钮上时会出现工具提示[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)。 这些提示将帮助你识别此处提及的特定按钮。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>选择并使用图像编辑器工具栏中的绘图工具

1. 选择上一个按钮**的图像编辑器**工具栏。

   - **橡皮擦**工具在当前的背景色图像上绘制，按下鼠标左键时。

      > [!TIP]
      > 而不是使用**橡皮擦**工具，您可能会发现它更方便地在其中一个绘图工具的背景色绘制。

   - **铅笔**工具中的一个像素固定宽度手工绘制。

   - **画笔**工具具有各种形态和规模。

   - **喷枪**工具随机分布围绕的中心画笔的颜色像素。

1. 如有必要，选择颜色和画笔：

   - 在中[颜色调色板](../windows/colors-window-image-editor-for-icons.md)，选择以选择前景色的鼠标按钮或鼠标右键按钮以选择背景色。

   - 在中[选项选择器](../windows/toolbar-image-editor-for-icons.md)，选择表示你想要使用的画笔的形状。

1. 指向你想要开始绘制的图像或绘制的位置。 指针改变了根据你选择工具的形状。

1. 按鼠标左键 （适用于的前景色） 或 （对于背景色），鼠标右键，并按住它为您绘制。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>选择并使用从映像菜单上的绘图工具

1. 转到菜单**图像** > **工具**。

1. 在级联子菜单，选择你想要使用的工具。

## <a name="lines-or-closed-figures"></a>线条或闭合的图形

**的图像编辑器**用于绘制直线和闭合的图形工具的工作方式相同： 将插入点放在某个时间点并拖动到另一个。 对于行，这些点是终结点。 为闭合图形，这些点是边框的相反图的角。

宽度由当前画笔选项，绘制线条空心的图形绘制，以确定由当前宽度选定内容的宽度。 行和所有的图形，同时构建框架和填充，绘制或当前的背景色中的当前前景色如果按鼠标左键，如果按鼠标右键。

### <a name="to-draw-a-line"></a>若要绘制的线条

1. 使用[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)转到菜单或**映像**> **工具**，然后选择**行**工具。

1. 如有必要，选择颜色和画笔：

   - 在中[颜色调色板](../windows/colors-window-image-editor-for-icons.md)，选择以选择前景色的鼠标按钮或鼠标右键按钮以选择背景色。

   - 在中[选项选择器](../windows/toolbar-image-editor-for-icons.md)，选择表示你想要使用的画笔的形状。

1. 将指针放置在该行的起始点。

1. 将拖到行的终结点。

### <a name="to-draw-a-closed-figure"></a>若要绘制闭合的图形

1. 使用**的图像编辑器**工具栏或转到菜单**映像** > **工具**，然后选择**封闭图绘制**工具。

   **封闭图绘制**工具按照其各自的按钮上的指示创建图形。

1. 如有必要，选择颜色和线条宽度。

1. 将指针移动到您要在其中绘制图的矩形区域的一角。

1. 到对角拖动指针。

## <a name="custom-brushes"></a>自定义画刷

自定义画笔是选取并的方式之一使用的图像的矩形部分**的图像编辑器**的现成的画笔。 可以执行所选内容的所有操作，可以自定义画笔上都执行。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>若要从图像的一部分创建自定义画笔

1. 选择你想要将它用作画笔映像的一部分。

1. 保存**Shift**按键按下、 在所选内容中选择和拖动在图像，或转到菜单**映像** > **使用所选内容用作画笔**。

   你的选择将成为在图像中分布中所选内容的颜色的自定义画笔。 在拖动路径也会保留所选内容的副本。 您拖动的速度就越慢，进行更多副本。

   > [!NOTE]
   > 选择**将所选内容用作画笔**没有首先选择图像的一部分将用作整个图像画笔。 使用自定义画笔的结果还取决于是否已选中[透明或不透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

自定义画笔中匹配当前的背景色的像素通常是透明： 它们不在现有的映像上绘画。 可以更改此行为，以便现有图像上绘制背景色像素为单位。

如戳记或模具中的自定义画笔可用于创建不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>若要绘制自定义画笔形状中的背景色

1. 选择透明或不透明背景。

1. 背景色设置为想要绘制的颜色。

1. 定位你想要绘制的自定义画笔。

1. 选择适当的鼠标按钮。 自定义画笔的不透明的任何区域中的背景色绘制。

### <a name="to-double-or-halve-the-custom-brush-size"></a>双击或四倍的自定义画笔大小

按**加号**(**+**) 密钥翻倍，画笔大小，或**减号**(**-**) 键减半.

### <a name="to-cancel-the-custom-brush"></a>若要取消的自定义画笔

按**Esc**或选择另一个绘制工具。

## <a name="requirements"></a>要求

None

## <a name="see-also"></a>请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[如何：创建图标或其他图像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：编辑图像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：处理颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>