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
ms.openlocfilehash: b0041124c35414a0c1c998642b5321319602c872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359855"
---
# <a name="how-to-use-a-drawing-tool"></a>如何：使用绘图工具

**图像编辑器**具有徒手绘图和可重复使用的工具，这些工具的工作方式相同。 选择该工具，并在必要时[选择前景和背景颜色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)以及大小和形状选项。 然后，将指针移动到图像，然后单击或拖动以绘制和擦除。

## <a name="drawing-tools"></a>绘图工具

您可以从 **"图像编辑器"** 工具栏或 **"图像"** 菜单中选择绘图工具。 当您选择**橡皮擦**工具、**画笔**工具或**喷枪**工具时，选项选择器将显示该工具的选项。

> [!TIP]
> 将光标悬停在[图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)上的按钮上时，将显示工具提示。 这些提示将帮助您确定此处提及的特定按钮。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>从图像编辑器工具栏中选择和使用绘图工具

1. 在 **"图像编辑器"** 工具栏上选择一个按钮。

   - 按下鼠标左键时，"**橡皮擦"** 工具使用当前背景颜色在图像上绘制。

      > [!TIP]
      > 您可以使用其中一个绘图工具在背景颜色中绘制，而不是使用**橡皮擦**工具。

   - **铅笔**工具以一个像素的恒定宽度徒手绘制。

   - **画笔**工具具有各种形状和大小。

   - **喷枪**工具随机分布画笔中心周围的颜色像素。

1. 如有必要，请选择颜色和画笔：

   - 在["颜色"调色板](../windows/colors-window-image-editor-for-icons.md)中，选择鼠标左键以选择前景颜色或鼠标右键以选择背景颜色。

   - 在["选项选择器](../windows/toolbar-image-editor-for-icons.md)"中，选择表示要使用的画笔的形状。

1. 指向要开始绘制或绘画的图像上的位置。 指针会根据您选择的工具更改形状。

1. 按鼠标左键（对于前景颜色）或鼠标右键（对于背景颜色），并在绘制时按住它。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>从"图像"菜单中选择和使用绘图工具

1. 转到菜单**图像** > **工具**。

1. 在级联子菜单上，选择要使用的工具。

## <a name="lines-or-closed-figures"></a>线或封闭数字

用于绘制线条和闭合图形**的图像编辑器**工具的工作方式都相同：将插入点放在一个点，然后拖动到另一个点。 对于行，这些点是端点。 对于闭合图，这些点是与图形相界的矩形的相反角。

线条以当前画笔选择确定的宽度绘制，框架图形以当前宽度选择确定的宽度绘制。 如果按鼠标左键，则线条和所有图形（框架和填充）以当前前景颜色绘制，如果按右鼠标按钮，则以当前背景颜色绘制。

### <a name="to-draw-a-line"></a>绘制线条

1. 使用["图像编辑器"工具栏](../windows/toolbar-image-editor-for-icons.md)或转到"**图像**> **工具**"菜单并选择 **"行"** 工具。

1. 如有必要，请选择颜色和画笔：

   - 在["颜色"调色板](../windows/colors-window-image-editor-for-icons.md)中，选择鼠标左键以选择前景颜色或鼠标右键以选择背景颜色。

   - 在["选项选择器](../windows/toolbar-image-editor-for-icons.md)"中，选择表示要使用的画笔的形状。

1. 将指针放在线的起始点。

1. 拖动到行的终结点。

### <a name="to-draw-a-closed-figure"></a>绘制闭合图

1. 使用 **"图像编辑器"** 工具栏或转到"**图像** > **工具**"菜单并选择 **"闭合图形绘图**"工具。

   **"闭合图"绘图**工具可按其各自按钮上所示创建图形。

1. 如有必要，选择颜色和线条宽度。

1. 将指针移动到要绘制图形的矩形区域的一个角。

1. 将指针拖动到对角对角。

## <a name="custom-brushes"></a>自定义画笔

自定义画笔是图像的矩形部分，您像**图像编辑器**的现成画笔一样拾取和使用。 您可以对所选内容执行所有操作，也可以在自定义画笔上执行。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>从图像的一部分创建自定义画笔

1. 选择要用于画笔的图像部分。

1. 按住**Shift**键，在选择中选择并将其拖动到图像中，或转到菜单 **"图像** > **使用选择作为画笔**"。

   您的选择将成为自定义画笔，用于在整个图像中分布所选内容中的颜色。 所选内容的副本沿拖动路径保留。 拖动得越慢，制作的副本就越多。

   > [!NOTE]
   > 选择"**使用选择作为画笔**，而不首先选择图像的一部分"将使用整个图像作为画笔。 使用自定义画笔的结果还取决于您选择了["不透明"或"透明"背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

自定义画笔中与当前背景颜色匹配的像素通常透明：它们不在现有图像上绘制。 您可以更改此行为，以便背景色像素在现有图像上绘制。

您可以使用自定义画笔（如图章或模具）来创建不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>以背景颜色绘制自定义画笔形状

1. 选择不透明或透明背景。

1. 将背景颜色设置为要绘制的颜色。

1. 将自定义画笔放置在要绘制的位置。

1. 选择鼠标右键。 自定义画笔的任何不透明区域都以背景颜色绘制。

### <a name="to-double-or-halve-the-custom-brush-size"></a>使自定义画笔大小翻倍或减半

按**加号**（**+**） 键将画笔大小翻倍，或按**减号**（**-**） 键将其减半。

### <a name="to-cancel-the-custom-brush"></a>取消自定义画笔

按**Esc**或选择其他绘图工具。

## <a name="requirements"></a>要求

None

## <a name="see-also"></a>另请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[如何：创建图标或其他图像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：编辑图像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[加速器键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
