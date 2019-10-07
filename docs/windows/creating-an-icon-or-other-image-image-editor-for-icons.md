---
title: 如何：创建图标或其他图像
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 2605644533d55527a07904ac89fa937db1b2eec5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513749"
---
# <a name="how-to-create-an-icon-or-other-image"></a>如何：创建图标或其他图像

可以创建新的图像、位图、图标、光标或工具栏, 并使用**图像编辑器**来自定义其外观。 你还可以在[资源模板](../windows/how-to-use-resource-templates.md)之后创建一个新的位图。

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>图标和光标:显示设备的图像资源

图标和光标是图形资源，可以为不同类型的显示设备包含大小和配色方案不同的多个图像。 游标还有一个作用点, 即 Windows 用来跟踪其位置的位置。 使用**图像编辑器**创建和编辑图标和光标, 如位图和其他图像。

当创建新图标或光标时,**图像编辑器**首先会创建一个标准类型的图像。 图像最初用屏幕（透明）颜色填充。 如果图像是光标, 则热点最初是带有坐标`0,0`的左上角。

默认情况下,**图像编辑器**支持为下表中所示的设备创建附加图像。 可以通过在 "**自定义图像**" 对话框中键入宽度、高度和颜色计数参数, 为其他设备创建图像。

|颜色|宽度（像素）|高度（像素）|
|-----------|----------------------|-----------------------|
|单色|16|16|
|单色|32|32|
|单色|48|48|
|单色|64|64|
|单色|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>创建设备图像 (图标或光标)

当你创建新的图标或光标资源时,**图像编辑器**将首先创建一个特定样式的图像 (32 × 32, 16 种颜色用于图标和32× 32, 单色用于游标)。 然后, 可以将不同大小和样式的图像添加到初始图标或光标处, 并根据需要为不同的显示设备编辑每个附加图像。 还可以通过使用现有图像类型或图形程序中创建的位图中的剪切和粘贴操作来编辑图像。

当您在[图像编辑器](../windows/image-editor-for-icons.md)中打开图标或光标资源时, 默认情况下会打开最匹配当前显示设备的图像。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件, 请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

"**新建&lt;设备&gt;图像类型**" 对话框可用于创建指定类型的新设备映像。 若要打开 **" \<新建设备 > 映像**" 对话框, 请参阅 "菜单**图像** > " "**新建图像类型**"。 包括的以下属性是**目标映像类型**和**自定义**。

"**目标图像类型**" 属性列出可用的图像类型, 您可以在其中选择要打开的图像类型:

||||
|-|-|-|
|-16 x 16, 16 色|-48 x 48, 16 色|-96 x 96, 16 色|
|-16 x 16, 256 颜色|-48 x 48, 256 颜色|-96 x 96, 256 颜色|
|-16 x 16, 单色|-48 x 48, 单色|-96 x 96, 单色|
|-32 x 32, 16 色|-64 x 64, 16 色||
|-32 x 32, 256 颜色|-64 x 64, 256 颜色||
|-32 x 32, 单色|-64 x 64, 单色||

> [!NOTE]
> 此列表中将不显示任何现有映像。

**自定义**属性将打开 "**自定义图像**" 对话框, 您可以在该对话框中创建具有自定义大小和颜色数的新图像。

使用 "**自定义图像**" 对话框, 您可以创建具有自定义大小和颜色数的新图像。 包括以下属性:

|属性|描述|
|---|---|
|**Width**|提供空间以输入自定义图像的宽度 (以像素为单位 (1-512, 2048)。|
|**Height**|提供空间以输入自定义图像的高度 (以像素为单位 (1-512, 2048)。|
|**颜色**|为您提供用于选择自定义图像的颜色数的空间:2、16或256。|

使用 "**打开&lt;设备&gt;图像**" 对话框打开项目中的C++设备映像。 它列出当前资源 (当前资源中的映像) 中的现有设备映像。 包含以下属性:

|Property|描述|
|---|---|
|**当前映像**|列出资源中包含的映像。 选择要打开的图像类型。|

#### <a name="to-create-a-new-icon-or-cursor"></a>创建新的图标或光标

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中, 右键单击 *.rc*文件, 然后选择 "**插入资源**"。 如果 *.rc*文件中已存在现有的图像资源 (如光标), 则可以右键单击该**光标**文件夹, 然后选择 "**插入光标**"。

1. 在 "[插入资源" 对话框](../windows/add-resource-dialog-box.md)中, 选择 "**图标**" 或 "**光标**" 并选择 "**新建**"。 对于图标, 此操作将创建一个具有32×32、16色图标的图标资源。 对于游标, 将创建一个32×32、单色 (2 色) 图像。

   如果 "**插入资源**" **+** 对话框中的图像资源类型旁边出现一个加号 (), 则表示工具栏模板可用。 选择加号以展开模板列表, 选择模板, 然后选择 "**新建**"。

### <a name="to-add-an-image-for-a-different-display-device"></a>为不同的显示设备添加图像

1. "中转到" 菜单 "**图像** > " "**新建设备图像**", 或在 "**图像编辑器**" 窗格中右键单击, 然后选择 "**新建设备映像**"。

1. 选择要添加的映像类型。 你还可以选择 "**自定义**" 来创建其大小在默认列表中不可用的图标。

### <a name="to-copy-a-device-image"></a>复制设备映像

1. "中转到 > " 菜单 "**打开设备映像**", 然后从 "当前映像" 列表中选择一个映像。 例如, 选择 "32 × 32, 16 色版本的图标"。

1. 复制当前显示的图标图像 (**Ctrl +** +)。

1. 在另一个 "**图像编辑器**" 窗口中打开图标的不同图像。 例如, 打开图标的16× 16 16 色版本。

1. 将图标图像 (**Ctrl**+**V**) 从一个**图像编辑器**窗口粘贴到另一个。 如果将较大的大小粘贴到较小的大小, 则可以使用图标句柄来调整图像的大小。

### <a name="to-delete-a-device-image"></a>删除设备映像

图标图像显示在 "**图像编辑器**" 中时, 请参阅 "菜单**图像** > " "**删除设备映像**"。 删除资源中的最后一个图标图像时, 还会删除该资源。

> [!NOTE]
> 按**Del**键时, 将删除在图标上绘制的图像和颜色, 但会保留图标, 你现在可以重新设计该图标。 如果错误地按**Del** , 请按**Ctrl**+**Z**撤消该操作。

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>在设备图像中创建透明或反转区域

在[图像编辑器](../windows/image-editor-for-icons.md)中, 初始图标或光标图像具有透明特性。 尽管图标和光标图像是矩形, 但很多不会出现, 因为图像的各个部分是透明的, 而屏幕上的基础图像则通过图标或光标显示。 拖动图标时, 图像的部件可能会以反转颜色显示。 您可以通过在 "[颜色" 窗口](../windows/colors-window-image-editor-for-icons.md)中设置屏幕颜色和反转颜色来创建此效果。

应用于图标和光标的屏幕和反转颜色既可以为派生图像着色, 也可以指定反转区域。 颜色指示具有这些属性的图像部分。 在编辑时, 可以更改表示屏幕颜色和反色属性的颜色。 这些更改不会影响应用程序中图标或光标的外观。

> [!NOTE]
> 显示的对话框和菜单命令可能与“帮助”中的描述不同，具体取决于现用的设置或版本。 若要更改设置, 请转到 "菜单" "**工具** > " "**导入和导出设置**"。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

#### <a name="to-create-transparent-or-inverse-regions"></a>创建透明或反转区域

1. 在 "**颜色**" 窗口中, 选择选择器**屏幕颜色**或**反转颜色**。

1. 使用绘图工具对图像应用屏幕或反转颜色。 有关绘图工具的详细信息, 请参阅[使用绘图工具](using-a-drawing-tool-image-editor-for-icons.md)。

#### <a name="to-change-the-screen-or-inverse-color"></a>更改屏幕或反转颜色

1. 选择**屏幕颜色**选择器或**反转颜色**选择器。

1. 从 "**颜色**" 窗口的 "**颜色**" 调色板中选择一种颜色。

   为其他选择器自动分配互补色。

   > [!TIP]
   > 如果双击**屏幕颜色**或**反转颜色**选择器, 则会显示 "[自定义颜色选择器" 对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)。

### <a name="use-the-256-color-palette"></a>使用256调色板

使用**图像编辑器**, 可以将图标和光标调整为大 (64 × 64), 并使用256调色板进行选择。 创建资源后, 会选择设备图像样式。

#### <a name="to-create-a-256-color-icon-or-cursor"></a>创建256色图标或光标

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中, 右键单击 *.rc*文件, 然后选择 "**插入资源**"。 如果 *.rc*文件中已存在现有的图像资源 (如光标), 则可以右键单击该**光标**文件夹, 然后选择 "**插入光标**"。

1. 在 "[插入资源" 对话框](../windows/add-resource-dialog-box.md)中, 选择 "**图标**" 或 "**光标**" 并选择 "**新建**"。

1. "中转到" 菜单 "**图像** > " "**新建设备图像**", 并选择所需的256颜色图像样式。

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>为大图标从256调色板选择颜色

若要使用256调色板的所选内容进行绘制, 需要从 "[颜色" 窗口](../windows/colors-window-image-editor-for-icons.md)的 "**颜色**" 调色板中选择颜色。

1. 选择大图标或光标, 或创建新的大图标或光标。

1. 从 "**颜色**" 窗口的 "**颜色**" 调色板中显示的256颜色中选择一种颜色。

   选择的颜色将成为 "**颜色**" 窗口的 "**颜色**" 调色板中的当前颜色。

   > [!NOTE]
   > 用于256颜色图像的初始调色板匹配`CreateHalftonePalette` Windows API 返回的调色板。 所有适用于 Windows shell 的图标都应使用此调色板来防止调色板实现期间闪烁。

### <a name="to-set-a-cursors-hot-spot"></a>设置光标的作用点

光标的作用点是 Windows 在跟踪光标位置时所指向的点。 默认情况下, 作用点设置为光标的左上角和坐标`0,0`。 [属性窗口](/visualstudio/ide/reference/properties-window)中的**热点**属性显示了作用点坐标。

1. 在 "[图像编辑器" 工具栏](../windows/toolbar-image-editor-for-icons.md)上, 选择 "**设置热点**" 工具。

1. 选择要分配为光标作用点的像素。

   "**属性**" 窗口中的 "**作用点**" 属性显示新坐标。

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>以 .gif 或 jpeg 格式创建并保存位图

创建位图时, 将以位图格式 (.bmp) 创建图像。 不过, 您可以将图像保存为 GIF 或 JPEG 格式, 也可以其他图形格式保存。

> [!NOTE]
> 此过程不适用于图标和光标。

1. "打开" "**打开**" 菜单**文件** > , 然后选择 "**文件**"。

1. 在 "**新建文件" 对话框**中, 选择 **" C++视觉对象**" 文件夹, 然后在 "**模板**" 框中选择 "**位图文件 (.bmp)** ", 然后选择 "**打开**"。

   将在**图像编辑器**中打开位图。

1. 根据需要更改新的位图。

1. **图像编辑器**中的位图仍处于打开状态, 请参阅菜单**文件** > **将*filename*保存为**。

1. 在 "**将文件另存为**" 对话框中, 在 "文件名" 框中键入要为该文件指定的名称以及表示所需文件格式的扩展名。 例如, *myfile.txt*。

   > [!NOTE]
   > 若要将位图另存为其他文件格式, 必须在项目外创建或打开位图。 如果在项目中创建或打开此项目, "**另存为**" 命令将不可用。 有关详细信息, 请参阅[查看项目外部的资源脚本文件中的资源 (独立)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

1. 选择**保存**。

### <a name="to-convert-an-image-from-one-format-to-another"></a>将图像从一种格式转换为另一种格式

您可以在**图像编辑器**中打开 GIF 或 JPEG 图像, 并将其保存为位图。 此外, 还可以打开位图文件并将其保存为 GIF 或 JPEG。 所使用的图像不需要是项目的一部分, 因此无法在开发环境中进行编辑 (请参阅[独立的图像编辑](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md))。

1. 在**图像编辑器**中打开图像。

1. 中转到菜单**文件** > **将*文件名*另存为**。

1. 在 "将**文件另存为**" 对话框中的 "文件名" 框中, 键入用于表示所需格式的文件名称和扩展名。

1. 选择**保存**。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>向非托管C++项目中添加新的图像资源

1. 在[资源视图](how-to-create-a-resource-script-file.md#create-resources)中, 右键单击 *.rc*文件, 然后选择 "**插入资源**"。 如果 *.rc*文件中已存在现有的图像资源 (如光标), 只需右键单击该**光标**文件夹, 然后选择 "**插入光标**" 即可。

1. 在 "[插入资源" 对话框](../windows/add-resource-dialog-box.md)中, 选择想要创建的图像资源类型 (例如**Bitmap**), 然后选择 "**新建**"。

   如果 "**插入资源**" **+** 对话框中的图像资源类型旁边出现一个加号 (), 则表示工具栏模板可用。 选择加号以展开模板列表, 选择模板, 然后选择 "**新建**"。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>向 .NET 编程语言中的项目添加新的图像资源

1. 在**解决方案资源管理器**中, 右键单击项目文件夹 (例如, *WindowsApplication1*)。

1. 在快捷菜单中, 选择 "**添加**", 然后选择 "**添加新项**"。

1. 在 "**类别**" 窗格中, 展开 "**本地项目项目**" 文件夹, 然后选择 "**资源**"。

1. 在 "**模板**" 窗格中, 选择要添加到项目中的资源类型。

   资源将添加到**解决方案资源管理器**中的项目, 并在[图像编辑器](../windows/image-editor-for-icons.md)中打开资源。 你现在可以使用 "**图像编辑器**" 中提供的所有工具来修改映像。 有关将图像添加到托管项目的详细信息, 请参阅[在设计时加载图片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[如何：编辑图像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用绘图工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：处理颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->