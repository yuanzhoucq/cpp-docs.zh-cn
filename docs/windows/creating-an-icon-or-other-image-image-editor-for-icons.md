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
ms.openlocfilehash: d10593ffbae7aef55adc3334057402b6952d8ba7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345521"
---
# <a name="how-to-create-an-icon-or-other-image"></a>如何：创建图标或其他图像

您可以创建新图像、 位图、 图标、 游标或工具栏上，，然后使用**的图像编辑器**来自定义其外观。 此外可以创建新的位图采用[资源模板](../windows/how-to-use-resource-templates.md)。

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>图标和光标：显示设备的图像资源

图标和光标是图形资源，可以为不同类型的显示设备包含大小和配色方案不同的多个图像。 游标还具有一个热点，位置 Windows 用来跟踪其位置。 图标和光标使用创建和编辑**的图像编辑器**、 以及位图和其他映像。

当创建新图标或光标，**的图像编辑器**首先创建标准类型的图像。 图像最初用屏幕（透明）颜色填充。 如果图像是光标，热点最初是左上角坐标`0,0`。

默认情况下**的图像编辑器**支持为下表中所示的设备创建附加图像。 可以通过键入宽度、 高度和色彩计数参数创建其他设备的映像**自定义映像**对话框。

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

### <a name="create-a-device-image-icon-or-cursor"></a>创建设备图像 （图标或光标）

当创建新图标或光标资源**的图像编辑器**首先在特定样式 （32 × 32，16 种颜色图标和 32 × 32，游标的单色） 中创建映像。 然后可以将不同大小和样式的图像添加到初始图标或光标，并编辑每个其他映像，根据需要对不同的显示设备。 此外可以通过使用剪切和粘贴操作从现有的映像类型或在图形计划中创建的位图编辑映像。

当你打开中的图标或光标资源[的图像编辑器](../windows/image-editor-for-icons.md)，默认情况下将打开大多数紧密匹配当前的显示设备的图像。

> [!NOTE]
> 如果你的项目尚未包含.rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

**新建&lt;设备&gt;映像类型**对话框中，可创建指定类型的新设备图像。 若要打开**新建\<设备 > 图像**对话框中，转到菜单**图像** > **新建图像类型**。 包含的以下属性是**目标图像类型**并**自定义**。

**目标图像类型**属性列出了可用的图像类型选择映像你想要打开的类型：

||||
|-|-|-|
|-16 x 16，16 种颜色|-48 x 48，16 种颜色|-96 x 96，16 种颜色|
|-16 x 16，256 种颜色|-48 x 48，256 种颜色|-96 x 96，256 种颜色|
|-16 x 16，单色|-48 x 48，单色|-96 x 96，单色|
|-32 x 32，16 种颜色|-64 x 64，16 种颜色||
|-32 x 32，256 种颜色|-64 x 64，256 种颜色||
|-32 x 32，单色|-64 x 64，单色||

> [!NOTE]
> 任何现有的映像将不显示在此列表中。

**自定义**属性将打开**自定义映像**对话框可以创建新的映像使用自定义的大小和颜色数。

**自定义映像**对话框中，可创建新的映像使用自定义的大小和颜色数。 是包含的以下属性：

|属性|描述|
|---|---|
|**Width**|提供空间以输入自定义图像的宽度以像素为单位 （1-512，限制 2048年）。|
|**Height**|提供空间以输入自定义映像以像素为单位 （1-512，限制 2048年） 的高度。|
|**颜色**|提供空间以选择自定义图像的颜色数：2、 16 或 256。|

使用**打开&lt;设备&gt;映像**对话框以打开设备图像中的C++项目。 它列出了当前资源 （属于当前资源的映像） 中的现有设备图像。 是包含以下属性：

|属性|描述|
|---|---|
|**当前映像**|列出资源中包含的映像。 选择你想要打开的图像类型。|

#### <a name="to-create-a-new-icon-or-cursor"></a>若要创建新图标或光标

1. 在中[资源视图](how-to-create-a-resource-script-file.md#create-resources)，右键单击你 *.rc*文件，然后选择**插入资源**。 如果已有现有的图像资源您 *.rc*文件，例如游标，您可以右键单击**游标**文件夹，然后选择**插入光标**。

1. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**，然后选择**新建**。 对于图标，此操作使用 32 × 32，16 色图标创建一个图标资源。 对于游标，32 × 32，创建单色 （2 种颜色） 映像。

   如果一个加号 (**+**) 中的图像资源类型旁边会显示**插入资源**对话框中，这意味着工具栏模板都可用。 选择加号以展开模板列表中的，选择一个模板，然后选择**新建**。

### <a name="to-add-an-image-for-a-different-display-device"></a>若要添加不同的显示设备的图像

1. 转到菜单**图像** > **新设备图像**，或在右键单击**图像编辑器**窗格中选择**新设备图像**。

1. 选择你想要添加的图像的类型。 您还可以选择**自定义**以创建其大小不可用的默认列表中的图标。

### <a name="to-copy-a-device-image"></a>复制设备图像

1. 转到菜单**图像** > **打开设备图像**和从当前的图像列表中选择映像。 例如，选择 32 × 32，16 色版本的图标。

1. 复制当前显示的图标图像 (**Ctrl**+**C**)。

1. 打开另一个图像的图标在另一个**的图像编辑器**窗口。 例如，打开 16 × 16，16 色版本的图标。

1. 粘贴图标图像 (**Ctrl**+**V**) 从一个**图像编辑器**到其他窗口。 如果您要粘贴到较小的大小更大的大小，可以使用图标句柄来调整图像的大小。

### <a name="to-delete-a-device-image"></a>若要删除设备图像

在显示的图标图像同时**的图像编辑器**，请转到菜单**映像** > **删除设备图像**。 当您删除的资源中的最后一个图标图像时，也会删除该资源。

> [!NOTE]
> 当您按下**Del**键，图像和颜色绘制图标会删除，但图标将保持，现在可以重新设计它。 如果按下**Del**错误地按**Ctrl**+**Z**要撤消的操作。

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>若要在设备图像中创建透明或反转区域

在中[的图像编辑器](../windows/image-editor-for-icons.md)，初始的图标或光标图像有透明特性。 尽管图标和光标图像矩形，但许多不会这样显示因为图像的部分是透明的底层图像在屏幕上的显示了通过图标或光标。 当您拖动的图标图像的部分可能会出现在倒排的颜色。 通过设置屏幕颜色和中的反转颜色创建这种效果[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。

屏幕和反转颜色将应用于图标和光标形状，颜色派生的映像或者反向区域分配。 颜色指示图像的具有这些属性的部分。 您可以更改表示屏幕颜色和反色中编辑属性的颜色。 这些更改不会影响应用程序中的光标的图标的外观。

> [!NOTE]
> 显示的对话框和菜单命令可能与“帮助”中的描述不同，具体取决于现用的设置或版本。 若要更改设置，请转到菜单**工具** > **导入和导出设置**。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

#### <a name="to-create-transparent-or-inverse-regions"></a>若要创建透明或反转区域

1. 在中**颜色**窗口中，选择选择器**屏幕颜色**或**反色**。

1. 将应用的屏幕或使用绘图工具在图像上的反转颜色。 有关绘图工具的详细信息，请参阅[使用绘图工具](using-a-drawing-tool-image-editor-for-icons.md)。

#### <a name="to-change-the-screen-or-inverse-color"></a>若要更改屏幕或反转颜色

1. 选择任一**屏幕颜色**选择器或**反色**选择器。

1. 选择从一种颜色**颜色**中的调色板**颜色**窗口。

   另一个选择器自动分配补色。

   > [!TIP]
   > 如果您双击**屏幕颜色**或**反色**选择器中，[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)出现。

### <a name="use-the-256-color-palette"></a>使用 256 色调色板

使用**的图像编辑器**，图标和光标可以为固定大小较大 (64 × 64) 256 色调色板中选择。 创建资源后，选择设备映像样式。

#### <a name="to-create-a-256-color-icon-or-cursor"></a>若要创建 256 色图标或光标

1. 在中[资源视图](how-to-create-a-resource-script-file.md#create-resources)，右键单击你 *.rc*文件，然后选择**插入资源**。 如果已有现有的图像资源您 *.rc*文件，例如游标，您可以右键单击**游标**文件夹，然后选择**插入光标**。

1. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**，然后选择**新建**。

1. 转到菜单**图像** > **新设备图像**，然后选择所需的 256 色图像样式。

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要从大图标的 256 色调色板选择颜色

若要通过选择绘制从 256 色调色板，您需要选择中的颜色**颜色**中的调色板[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。

1. 大图标或光标，选择或创建新的大图标或光标。

1. 从显示中的 256 种颜色中选择颜色**颜色**中的调色板**颜色**窗口。

   选定的颜色将成为中的当前颜色**颜色**中的调色板**颜色**窗口。

   > [!NOTE]
   > 使用 256 色图像的初始调色板匹配返回的调色板`CreateHalftonePalette`Windows API。 适用于 Windows 外壳程序的所有图标应都使用此面板来防止在调色板实现过程的闪烁。

### <a name="to-set-a-cursors-hot-spot"></a>若要设置光标的作用点

游标的作用点的作用是指 Windows 跟踪光标的位置。 默认情况下，作用点设置为左上角的坐标为游标`0,0`。 **热点**属性中的[属性窗口](/visualstudio/ide/reference/properties-window)显示作用点坐标。

1. 上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)，选择**设置作用点**工具。

1. 选择想要分配为光标的作用点的像素。

   **热点**属性中的**属性**窗口将显示新的坐标。

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>若要创建并将位图另存为.gif 或.jpeg

在创建位图时，位图格式 (.bmp) 中创建映像。 但是，，您可以图像保存为 GIF 或 JPEG 或其他图形格式。

> [!NOTE]
> 此过程不适用于图标和光标。

1. 转到菜单**文件** > **打开**，然后选择**文件**。

1. 在中**新文件对话框**，选择**Visual C++** 文件夹，然后选择**位图文件 (.bmp)** 中**模板**框和选择**打开**。

   在中打开位图**的图像编辑器**。

1. 根据需要对新的位图进行更改。

1. 与仍在中打开位图**的图像编辑器**，请转到菜单**文件** > **保存*文件名*为.bmp**。

1. 在**将文件另存为**对话框框中，键入你想要提供的文件和表示中所需的文件格式的扩展插件的名称**文件名**框。 例如， *myfile.gif*。

   > [!NOTE]
   > 必须创建或打开在项目之外的位图，才能将其保存为另一种文件格式。 如果在创建或打开您的项目内**另存为**命令将不可用。 有关详细信息，请参阅[查看资源在资源脚本文件之外的项目 （独立版）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

1. 选择“保存”。

### <a name="to-convert-an-image-from-one-format-to-another"></a>若要将图像从一种格式转换到另一个

您可以打开 GIF 或 JPEG 图像的方式**的图像编辑器**并将其保存为位图。 此外，可以打开一个位图文件，并将其保存为 GIF 或 JPEG。 所处理的图像不需要在开发环境中编辑的项目的一部分 (请参阅[独立图像编辑](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md))。

1. 打开中的图像**的图像编辑器**。

1. 转到菜单**文件** > **保存*filename*作为**。

1. 在**将文件另存为**对话框中**文件名**框中，键入文件名称和扩展名，表示所需的格式。

1. 选择“保存”。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>若要将新的图像资源添加到非托管C++项目

1. 在中[资源视图](how-to-create-a-resource-script-file.md#create-resources)，右键单击你 *.rc*文件，然后选择**插入资源**。 如果已有现有的图像资源您 *.rc*文件中，可以如游标，您只需右键单击**光标**文件夹，然后选择**插入光标**。

1. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择你想要创建的图像资源的类型 (**位图**，例如) 然后选择**新建**。

   如果一个加号 (**+**) 中的图像资源类型旁边会显示**插入资源**对话框中，这意味着工具栏模板都可用。 选择加号以展开模板列表中的，选择一个模板，然后选择**新建**。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>若要将新的图像资源添加到.NET 编程语言中的项目

1. 在中**解决方案资源管理器**，右键单击项目文件夹 (例如， *WindowsApplication1*)。

1. 从快捷菜单中，选择**外**，然后选择**添加新项**。

1. 在中**类别**窗格中，展开**本地项目项**文件夹，然后选择**资源**。

1. 在中**模板**窗格中，选择你想要添加到项目的资源类型。

   该资源添加到项目中**解决方案资源管理器**，并在打开该资源[图像编辑器](../windows/image-editor-for-icons.md)。 现在可以使用所有中提供的工具**的图像编辑器**修改你的映像。 将映像添加到托管项目的详细信息，请参阅[加载在设计时图片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。

## <a name="requirements"></a>要求

None

## <a name="see-also"></a>请参阅

[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[如何：编辑图像](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用绘图工具](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：处理颜色](../windows/working-with-color-image-editor-for-icons.md)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/desktop/menurc/icons)<br/>
[Cursors](/windows/desktop/menurc/cursors)<br/>-->