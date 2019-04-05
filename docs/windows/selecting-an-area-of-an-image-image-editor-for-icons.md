---
title: 如何：编辑图像
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
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
ms.openlocfilehash: 849da0d14987a057d39d5f9531e97545b3d4b8cf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033282"
---
# <a name="how-to-edit-an-image"></a>如何：编辑图像

选择工具可用于定义你想要剪切、 复制、 清除、 重设大小、 反转，或移动的图像的区域。 与**矩形选择**工具可以定义并选择图像的矩形区域。 与**不规则选择**工具可以绘制需选择它以执行剪切、 复制或其他操作的区域的徒手画的轮廓。

> [!NOTE]
> 请参阅**矩形选择**并**不规则选择**工具中所示[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)或查看与的每个按钮关联的工具提示**图像编辑器**工具栏。

此外可以从选定项创建自定义画笔。 有关详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

## <a name="how-to"></a>操作说明

若要编辑映像，请参阅如何：

### <a name="to-select-an-image"></a>若要选择一个映像

1. 使用**的图像编辑器**工具栏或转到菜单**映像** > **工具**，然后选择你想选择工具。

1. 将插入点移动到你想要选择的图像区域的一角。 插入点位于图像上方时，会显示十字线。

1. 到你想要选择的区域的对角拖动该插入点。 一个矩形显示了将选择的像素为单位。 所选内容中包含的矩形，包括那些在该矩形内的所有像素。

1. 释放鼠标按钮。 选择边框环绕选定的区域。

#### <a name="to-select-an-entire-image"></a>若要选择整个图像

选择当前所选内容之外的映像。 选择边框焦点更改，然后再一次包含整个图像。

### <a name="to-edit-parts-of-an-image"></a>若要编辑的图像部分

您可以执行标准的编辑操作 — 剪切、 复制、 清除和移动 — 上[选择](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)、 所选内容是否整个图像或它的其中一部分。 因为**的图像编辑器**使用**Windows 剪贴板**，你可以将图像传输之间**的图像编辑器**和 Windows 其他应用程序。

此外，它包括整个图像或其一部分是否可以调整大小所选内容。

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>若要剪切当前所选内容并将其移动到剪贴板

转到菜单**编辑** > **剪切**。

#### <a name="to-copy-the-selection"></a>若要复制所选内容

1. 除调整大小控点在其上放置内部选择边框或任意位置的指针。

1. 按住**Ctrl**键将所选内容拖动到新位置。 原选定内容的区域保持不变。

1. 若要将所选内容复制到其当前位置的图像中，选择外部选择光标。

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>若要将剪贴板内容粘贴到映像中

1. 转到菜单**编辑** > **粘贴**。

   在窗格的左上角显示剪贴板内容，通过选择边框，括起来。

1. 选择边框内指针定位并将图像拖到所需位置，在映像上。

1. 若要定位到其新位置的映像，选择选择边框之外。

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>若要删除当前所选内容，而不将其移动到剪贴板

转到菜单**编辑** > **删除**。

   使用当前的背景色填充所选内容的原始区域。

> [!NOTE]
> 可以访问**剪切**，**副本**，**粘贴**，以及**删除**命令中右键单击**资源视图**窗口。

#### <a name="to-move-the-selection"></a>若要移动选定内容

1. 除调整大小控点在其上放置内部选择边框或任意位置的指针。

1. 将所选内容拖动到其新位置。

1. 若要定位到其新位置的映像中的选择，选择选择边框之外。

通过选择绘图的详细信息，请参阅[创建自定义画笔](../windows/creating-a-custom-brush-image-editor-for-icons.md)。

### <a name="to-flip-an-image"></a>翻转图像

可以翻转或旋转图像来创建原始镜像映像、 将图像上下颠倒，或将右侧图像旋转 90 度，一次。

- 若要水平翻转图像 （镜像），请转至菜单**图像** > **水平翻转**。

- 垂直翻转图像 （将上下颠倒），请转至菜单**图像** > **垂直翻转**。

- 若要将图像旋转 90 度，请转到菜单**图像** > **旋转 90 度**。

   > [!NOTE]
   > 此外可以使用[加速 （快捷） 键](../windows/accelerator-keys-image-editor-for-icons.md)这些命令或从快捷菜单访问命令 (选择中的图像时外部**图像编辑器**)。

### <a name="to-resize-an-image"></a>若要调整图像大小

行为**的图像编辑器**而调整图像的大小取决于是否已[选](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)整个图像或只是它的一部分。

所选内容包含仅的映像的一部分时**的图像编辑器**通过删除行或列的像素为单位，并使用当前的背景色填充空出的区域缩小选定内容。 通过复制行或列的像素为单位，它也可以延迟所选内容。

当所选内容包括整个图像**的图像编辑器**收缩和拉伸图像，，或裁剪和对其进行扩展。

有两种方式调整图像大小： 调整大小控点和[属性窗口](/visualstudio/ide/reference/properties-window)。 拖动调整大小控点，若要更改的所有大小或映像的一部分。 可以拖动调整大小控点都是可靠的。 您不能拖动空心的句柄。 使用**属性**窗口来调整大小整个仅，图像不是所选的一部分。

![大小调整控点上位图](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
调整大小控点

> [!NOTE]
> 如果有**磁贴网格**中选择选项[网格设置对话框](../windows/grid-settings-dialog-box-image-editor-for-icons.md)，然后调整大小将下一步的平铺网格线对齐。 如果只有**像素网格**选项是选择 （默认设置），调整大小将对齐到下一个可用的像素。

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>若要调整整个图像使用属性窗口的大小

1. 打开你想要更改其属性的图像。

1. 在中**宽度**并**高度**框[属性窗口](/visualstudio/ide/reference/properties-window)，键入所需的尺寸。

   如果要增加映像的大小**的图像编辑器**扩展和 / 或右侧，向下，映像，并使用当前的背景色填充新的区域。 图像未被拉伸。

   如果缩短图像的大小**的图像编辑器**裁剪该图像右边缘或下边缘，或这两者。

   > [!NOTE]
   > 可以使用**宽度**并**高度**属性，以仅整个调整图像的大小，无法调整部分选定内容的大小。

#### <a name="to-crop-or-extend-an-entire-image"></a>若要裁剪或扩展整个图像

1. 选择整个图像。

   如果当前选择的映像的一部分，并且你想要选择整个图像，选择任意位置上当前选定内容边框外部图像。

1. 拖动调整大小控点，直到该图像是适当的大小。

通常情况下，**的图像编辑器**裁剪或增大图像时调整其大小通过移动调整大小控点。 如果您按住**Shift**键移动大小调整句柄**图像编辑器**缩小或拉伸图像。

#### <a name="to-shrink-or-stretch-an-entire-image"></a>若要缩小或拉伸整个图像

1. 选择整个图像。

   如果当前所选映像的一部分，并且你想要选择整个图像，选择任意位置上当前选定内容边框外部图像。

1. 按住**Shift**键并拖动调整大小控点，直到该图像是适当的大小。

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>若要缩小或拉伸图像的一部分

1. 选择要重设大小的图像的一部分。 有关详细信息，请参阅[选择的图像区域](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)。

1. 拖动调整大小控点之一，直到所选内容是适当的大小。

### <a name="to-edit-an-image-outside-of-a-project"></a>若要编辑在项目外部图像

您可以打开并编辑开发环境中的映像，就像在任何图形应用程序中，例如打开独立编辑的位图。 您使用的映像不需要 Visual Studio 项目的一部分。

1. 转到菜单**文件** > **打开**。

1. 在中**Files of Type**框中，选择**的所有文件**。

1. 找到并打开你想要编辑的图像。

### <a name="to-change-image-properties"></a>若要更改图像属性

可以设置或修改映像使用的属性[属性窗口](/visualstudio/ide/reference/properties-window)。

1. 打开中的图像**的图像编辑器**。

1. 在中**属性**窗口中，更改你的映像的任何或所有属性。

   |属性|描述|
   |--------------|-----------------|
   |**颜色**|指定图像的颜色方案。 选择**单色**， **16**，或**256**，或者**True 颜色**。<br/><br/>如果您已绘制具有 16 调色板的图像，则选择**单色**图像会导致的黑色和白色的颜色的替换项。 对比度并不总是保持： 例如，红色和绿色的相邻区域均会转换为黑色。|
   |**Filename**|指定图像文件的名称。<br/><br/>默认情况下，Visual Studio 中的默认资源标识符 (IDB_BITMAP1) 并添加相应的扩展分配给通过删除前四个字符 ("IDB_") 创建的基文件名。 在此示例中的图像文件名称将为*BITMAP1.bmp*。 你可以重命名*MYBITMAP1.bmp*。|
   |**高度**|设置图像的高度 （以像素为单位）。 默认值为 48。<br/><br/>裁剪图像或以下现有映像添加空格。|
   |**Id**|设置资源的标识符。<br/><br/>对于一个映像，Microsoft Visual Studio 中，默认情况下，将分配一系列中的下一步提供标识符：IDB_BITMAP1、 IDB_BITMAP2，等等。 类似的名称用于图标和光标。|
   |**调色板**|更改颜色属性。<br/><br/>双击以选择一种颜色，并显示[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。 通过在相应的文本框中键入 RGB 或 HSL 值定义颜色。|
   |**SaveCompressed**|指示图像是否以压缩格式。 此属性是只读的。<br/><br/>Visual Studio 不允许您保存图像以压缩格式，因此，对于 Visual Studio 中创建任何图像，此属性将**False**。 如果在 Visual Studio 中打开 （在另一个程序中创建） 的压缩的映像，请将此属性 **，则返回 True**。 如果你保存压缩的映像使用 Visual Studio 中，将未压缩，并且此属性将返回到**False**。|
   |**宽度**|设置图像的宽度 （以像素为单位）。 位图的默认值为 48。<br/><br/>裁剪图像或空白区域添加到现有的图像的右侧。|

## <a name="requirements"></a>要求

None

## <a name="see-also"></a>请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[如何：创建图标或其他图像](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：使用绘图工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：处理颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>