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
ms.openlocfilehash: 61c06ee3fecac18fb95663c0d13474b8bd3b94f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214378"
---
# <a name="how-to-use-a-drawing-tool"></a>如何：使用绘图工具

使用**图像编辑器**，可以采用相同的方式绘制和擦除所有工具。 选择该工具，并在必要时[选择 "前景颜色" 和 "背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)" 和 "大小和形状选项"。 然后，将指针移动到图像，然后单击或拖动以绘制和擦除。

## <a name="drawing-tools"></a>绘图工具

可以从 "**图像编辑器**" 工具栏或 "**图像**" 菜单中选择 "绘图工具"。 选择 "**橡皮擦**" 工具、"**画笔**工具" 或 "**喷枪**" 工具时，选项选择器将显示该工具的选项。

> [!TIP]
>  当你将光标悬停在 "[图像编辑器" 工具栏](../windows/toolbar-image-editor-for-icons.md)上的按钮上时，将显示工具提示。 这些提示将帮助你识别此处提到的特定按钮。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>从 "图像编辑器" 工具栏选择和使用绘图工具

1. 在 "**图像编辑器**" 工具栏上选择一个按钮。

   - 当您按下鼠标左键时，**橡皮擦**工具将用当前背景色绘制图像。

      > [!TIP]
      > 您可能会发现使用一种绘图工具在背景颜色中进行绘制更方便，而不是使用**橡皮擦**工具。

   - **铅笔**工具在一个像素的固定宽度内绘制。

   - **画笔**工具具有不同的形状和大小。

   - **喷枪**工具围绕画笔中心随机分布颜色像素。

1. 如有必要，请选择颜色和画笔：

   - 在 "[颜色" 调色板](../windows/colors-window-image-editor-for-icons.md)中，选择鼠标左键以选择前景色或鼠标右键以选择背景色。

   - 在[选项选择器](../windows/toolbar-image-editor-for-icons.md)中，选择表示要使用的画笔的形状。

1. 指向要开始绘制或绘制的图像上的位置。 指针根据您选择的工具更改形状。

1. 按下鼠标左键（对于前景色）或鼠标右键（适用于背景色），并在绘图时将其按下。

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>从 "图像" 菜单中选择和使用绘图工具

1.  > **工具**" **Image**中转到" 菜单 "。

1. 在级联子菜单中，选择要使用的工具。

## <a name="lines-or-closed-figures"></a>线条或闭合图形

用于绘制线条和闭合图形的**图像编辑器**工具都以相同的方式工作：将插入点放置在一个点上并拖动到另一个点。 对于线条，这些点是终结点。 对于闭合图形，这些点是以图形为边界的矩形的对角角。

线条以当前画笔选择所确定的宽度进行绘制，而用当前宽度选择所确定的宽度绘制有框的数字。 如果按下鼠标左键，则以当前前景色绘制线条和所有图形，如果按下鼠标右键，则以当前背景色绘制线条和所有图形。

### <a name="to-draw-a-line"></a>绘制线条

1. 使用 "[图像编辑器" 工具栏](../windows/toolbar-image-editor-for-icons.md)或 **"> ** **工具**" 菜单中的 "浏览"，然后选择 "**线条**" 工具。

1. 如有必要，请选择颜色和画笔：

   - 在 "[颜色" 调色板](../windows/colors-window-image-editor-for-icons.md)中，选择鼠标左键以选择前景色或鼠标右键以选择背景色。

   - 在[选项选择器](../windows/toolbar-image-editor-for-icons.md)中，选择表示要使用的画笔的形状。

1. 将指针置于行的起始点。

1. 拖动到线条的端点。

### <a name="to-draw-a-closed-figure"></a>绘制闭合图形

1. 使用 "**图像编辑器**" 工具栏或 **" > ** **工具**" 菜单中的 "浏览"，然后选择闭合图形的**绘图**工具。

   **闭合图形绘图**工具会根据各自的按钮来创建图形。

1. 如有必要，选择 "颜色" 和 "线条宽度"。

1. 将指针移到要在其中绘制图形的矩形区域的一个角。

1. 将指针拖到对角对角的角。

## <a name="custom-brushes"></a>自定义画笔

自定义画笔是您选取的图像的矩形部分，并使用**图像编辑器**的现成画笔。 您可以对选择执行的所有操作也可以在自定义画笔上执行。

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>从图像的一部分创建自定义画笔

1. 选择要用于画笔的图像部分。

1. 按住**Shift**键，选择所选内容并将其拖动到图像上，或转到 "菜单" "**图像** > **将所选内容用作画笔**。

   你的选择将成为一种自定义画笔，它在图像中分布所选内容中的颜色。 所选内容的副本沿着拖动路径为左。 拖动速度越慢，生成的副本就越多。

   > [!NOTE]
   > 选择 "将**所选内容用作画笔**"，而不先选择部分图像将使用整个图像作为画笔。 使用自定义画笔的结果还将取决于您是否选择了[透明或透明背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)。

与当前背景色匹配的自定义画笔中的像素通常是透明的：它们不会在现有图像上绘制。 您可以更改此行为，以便背景色像素在现有图像上进行绘制。

您可以使用自定义画笔（如戳记或模具）来创建不同的特殊效果。

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>以背景色绘制自定义画笔形状

1. 选择透明或透明背景。

1. 将背景色设置为要绘制的颜色。

1. 将自定义画笔定位到要绘制的位置。

1. 选择鼠标右键。 将以背景色绘制自定义画笔的任何不透明区域。

### <a name="to-double-or-halve-the-custom-brush-size"></a>双击或分自定义画笔大小

按**加号**（ **+** ）键将画笔大小加倍，或按**减号**（ **-** ）键分。

### <a name="to-cancel-the-custom-brush"></a>取消自定义画笔

按**Esc**或选择其他绘图工具。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>另请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[如何：创建图标或其他图像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：编辑图像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
