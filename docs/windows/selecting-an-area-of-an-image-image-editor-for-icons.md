---
title: 如何：编辑图像
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 9324e3dc5c6691a7b50f137da1fad446b416e968
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167844"
---
# <a name="how-to-edit-an-image"></a>如何：编辑图像

可以使用 "选择" 工具定义要剪切、复制、清除、重设大小、反转或移动的图像区域。 使用 "**矩形选择**" 工具，可以定义并选择图像的矩形区域。 使用不规则的 "**选择**" 工具，可以绘制要为剪切、复制或其他操作选择的区域的自由轮廓。

> [!NOTE]
> 请参阅 "[图像编辑器" 工具栏](../windows/toolbar-image-editor-for-icons.md)中的 "**矩形选择**" 和 "**不规则选择**" 工具，或查看与 "**图像编辑器**" 工具栏上每个按钮相关联的工具提示。

您还可以从所选内容创建自定义画笔。 有关详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

## <a name="how-to"></a>如何

若要编辑图像，请参阅如何：

### <a name="to-select-an-image"></a>选择图像

1. 使用 "**图像编辑器**" 工具栏或 **" > ** **工具**" 菜单中的 "浏览"，然后选择所需的选择工具。

1. 将插入点移动到要选择的图像区域的一个角。 当插入点在图像上时，将显示十字线。

1. 将插入点拖到要选择的区域的另一角。 矩形将显示选定的像素。 矩形内的所有像素（包括矩形下方的像素）都包含在选定内容中。

1. 释放鼠标按钮。 选择边框包围选定区域。

#### <a name="to-select-an-entire-image"></a>选择整个映像

在当前所选内容之外选择图像。 选择边框会改变焦点并再次包含整个图像。

### <a name="to-edit-parts-of-an-image"></a>编辑图像的各个部分

你可以在[选择](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)时执行标准编辑操作（剪切、复制、清除和移动），无论选定内容是整个图像还是只是它的一部分。 由于**图像编辑器**使用**windows 剪贴板**，因此你可以在**图像编辑器**和适用于 Windows 的其他应用程序之间传输图像。

此外，您还可以调整所选内容的大小，无论其包含整个图像还是仅包含部分。

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>剪切当前选定内容并将其移到剪贴板

"切换到菜单"**编辑** > **剪切**"。

#### <a name="to-copy-the-selection"></a>复制选定内容

1. 将指针置于选择边框内或其上的任何位置（大小调整控点除外）。

1. 按住**Ctrl**键的同时将所选内容拖到新位置。 原始选择的区域保持不变。

1. 若要将所选内容复制到图像的当前位置，请在选择光标的外部进行选择。

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>将剪贴板内容粘贴到映像中

1. "切换到菜单" "**编辑** > **粘贴**"。

   剪贴板内容由选择边框环绕，并显示在窗格的左上角。

1. 将指针置于选择边框内，然后将图像拖到图像上的所需位置。

1. 若要将图像定位在其新位置，请在选择边框之外选择。

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>删除当前所选内容，而不将其移动到剪贴板

"切换到菜单"**编辑** > **删除**"。

   将用当前背景色填充所选内容的原始区域。

> [!NOTE]
> 您可以通过在 "**资源视图**" 窗口中右键单击来访问**剪切**、**复制**、**粘贴**和**删除**命令。

#### <a name="to-move-the-selection"></a>移动选定内容

1. 将指针置于选择边框内或其上的任何位置（大小调整控点除外）。

1. 将所选内容拖到新位置。

1. 若要在图像中将所选内容锚定到其新位置，请在选择边框之外选择。

有关使用选择进行绘制的详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

### <a name="to-flip-an-image"></a>翻转图像

您可以翻转或旋转图像，以创建原始的镜像图像，将图像上下翻转，或将图像向右旋转90度。

- 若要水平翻转图像（镜像图像），请转到菜单**图像** > **水平翻转**。

- 若要垂直翻转图像（倒置），请转到 "菜单" "**图像** > "**垂直翻转**"。

- 要旋转图像90度，请转到菜单**图像** > **旋转90度**。

   > [!NOTE]
   > 你还可以使用这些命令的[快捷键（快捷）键](../windows/accelerator-keys-image-editor-for-icons.md)，或从快捷菜单中访问命令（在**图像编辑器**中选择图像外部）。

### <a name="to-resize-an-image"></a>调整图像大小

调整图像大小时**图像编辑器**的行为取决于您是选择了整个图像还是只[选择](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)了其中的一部分。

当所选内容仅包含图像的一部分时，**图像编辑器**会通过删除像素的行或列，并用当前背景色填充空出的区域，从而缩小选定范围。 它还可以通过复制像素的行或列来拉伸选定内容。

当所选内容包括整个图像时，**图像编辑器**缩小并拉伸图像，或裁剪并扩展图像。

调整图像大小的机制有两种：调整大小控点和[属性窗口](/visualstudio/ide/reference/properties-window)。 拖动调整大小控点可以更改图像的全部或部分的大小。 您可以拖动的尺寸控点为纯色控点。 不能拖动为空心的句柄。 使用 "**属性**" 窗口只调整整个图像的大小，而不是所选部分的大小。

![位图上的调整大小控点](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
调整大小控点

> [!NOTE]
> 如果您在 "[网格设置" 对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md)中选择了 "**磁贴网格**" 选项，则调整大小会对齐到下一个平铺网格线。 如果仅选择了**像素网格**选项（默认设置），则调整大小会对齐到下一个可用像素。

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>使用 "属性" 窗口调整整个图像的大小

1. 打开要更改其属性的映像。

1. 在 "**宽度**" 和 "**高度**" 框的 "[属性窗口](/visualstudio/ide/reference/properties-window)中，键入所需的维度。

   如果要增加图像的大小，**图像编辑器**会将图像向右、向下或同时扩展，并用当前背景色填充新区域。 图像未延伸。

   如果缩短图像的大小，**图像编辑器**将在右边缘或下边缘裁剪图像，或同时裁剪两者。

   > [!NOTE]
   > 您可以使用 "**宽度**" 和 "**高度**" 属性来仅调整整个图像的大小，而不是调整部分选定内容的大小。

#### <a name="to-crop-or-extend-an-entire-image"></a>裁剪或扩展整个图像

1. 选择整个映像。

   如果当前选择了图像的一部分，并且你想要选择整个图像，请选择图像上当前选定内容边框之外的任何位置。

1. 拖动调整大小控点，直到图像大小正确。

通常情况下，**图像编辑器**通过移动调整大小控点来裁剪或放大图像。 如果在移动尺寸控点时按住**Shift**键，**图像编辑器**将缩小或拉伸图像。

#### <a name="to-shrink-or-stretch-an-entire-image"></a>缩小或拉伸整个图像

1. 选择整个映像。

   如果当前选择了图像的一部分，并且你想要选择整个图像，请选择图像上当前选定内容边框之外的任何位置。

1. 按住**Shift**键并拖动调整大小控点，直到图像大小正确。

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>缩小或拉伸图像的一部分

1. 选择要调整大小的图像部分。 有关详细信息，请参阅[选择图像区域](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)。

1. 拖动其中一个尺寸控点，直到所选内容大小正确为止。

### <a name="to-edit-an-image-outside-of-a-project"></a>在项目外部编辑图像

您可以在开发环境中打开和编辑图像，就像在任何图形应用程序中一样，例如打开位图进行独立编辑。 所使用的映像不需要是 Visual Studio 项目的一部分。

1.  > "，请参阅"**打开**"菜单**文件**。

1. 在 "**文件类型**" 框中，选择 "**所有文件**"。

1. 找到并打开要编辑的映像。

### <a name="to-change-image-properties"></a>更改图像属性

您可以使用[属性窗口](/visualstudio/ide/reference/properties-window)来设置或修改图像的属性。

1. 在**图像编辑器**中打开图像。

1. 在 "**属性**" 窗口中，更改图像的任意或全部属性。

   |properties|说明|
   |--------------|-----------------|
   |**颜色**|指定图像的配色方案。 选择 "**单色**"、" **16**" 或 " **256**" 或 "**真彩色**"。<br/><br/>如果已绘制带有16色调色板的图像，则选择 "**单色**" 会导致图像中的颜色的黑色和白色的替换。 对比度并非始终保持不变：例如，红色和绿色的相邻区域都转换为黑色。|
   |**Filename**|指定图像文件的名称。<br/><br/>默认情况下，Visual Studio 会通过删除默认资源标识符（IDB_BITMAP1）中的前四个字符（"IDB_"）并添加适当的扩展，来分配创建的基本文件名。 在此示例中，图像的文件名为*BITMAP1*。 可以将其重命名为*MYBITMAP1*。|
   |高度|设置图像的高度（以像素为单位）。 默认值为48。<br/><br/>裁剪图像或将空白区域添加到现有图像下方。|
   |**ID**|设置资源的标识符。<br/><br/>对于图像，Microsoft Visual Studio 默认情况下会在序列中分配下一个可用标识符： IDB_BITMAP1、IDB_BITMAP2 等。 类似名称用于图标和光标。|
   |**调板**|更改颜色属性。<br/><br/>双击以选择颜色并显示 "[自定义颜色选择器" 对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 通过在相应的文本框中键入 RGB 或 HSL 值来定义颜色。|
   |**SaveCompressed**|指示图像是否为压缩格式。 此属性为只读。<br/><br/>Visual Studio 不允许以压缩格式保存图像，因此对于在 Visual Studio 中创建的任何图像，此属性将为**False**。 如果在 Visual Studio 中打开压缩的映像（在另一个程序中创建），则此属性将为**True**。 如果使用 Visual Studio 保存压缩的映像，则会将其解压缩，并且此属性将恢复为**False**。|
   |宽度|设置图像的宽度（以像素为单位）。 位图的默认值为48。<br/><br/>裁剪图像或将空白区域添加到现有图像的右侧。|

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>另请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[如何：创建图标或其他图像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：使用绘图工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
