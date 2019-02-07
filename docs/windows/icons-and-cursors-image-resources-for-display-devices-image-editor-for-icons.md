---
title: 图标和光标：显示设备 （c + + 图标的图像编辑器） 的图像资源
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
helpviewer_keywords:
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
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
ms.openlocfilehash: 027c3c0380a73c624432bbe45758b3296732949a
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849940"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-c-image-editor-for-icons"></a>图标和光标：显示设备 （c + + 图标的图像编辑器） 的图像资源

图标和光标是图形资源，可以为不同类型的显示设备包含大小和配色方案不同的多个图像。 此外，光标还具有一个"热点，"Windows 用来跟踪其位置的位置。 图标和光标使用创建和编辑**图像**编辑器中，以及位图和其他映像。

当创建新图标或光标，**图像**编辑器首先会创建标准类型的图像。 图像最初用屏幕（透明）颜色填充。 如果图像是光标，热点最初是左上角（坐标为 0,0）。

默认情况下**图像**编辑器支持为下表中所示的设备创建附加图像。 可以通过向 [自定义图像对话框](custom-image-dialog-box-image-editor-for-icons.md)中键入宽度、高度和色彩计数参数为其他设备创建图像。

> [!NOTE]
> 使用**的图像编辑器**，可以查看 32 位映像，但不能编辑这些。

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

## <a name="create-a-device-image-icon-or-cursor"></a>创建设备图像 （图标或光标）

当创建新图标或光标资源**图像**编辑器首先在特定样式 （32 × 32，16 种颜色图标和 32 × 32，游标的单色） 中创建映像。 然后可以将不同大小和样式的图像添加到初始图标或光标，并编辑每个其他映像，根据需要对不同的显示设备。 此外可以通过使用剪切和粘贴操作从现有的映像类型或在图形计划中创建的位图编辑映像。

当你打开中的图标或光标资源[的图像编辑器](../windows/image-editor-for-icons.md)，默认情况下将打开大多数紧密匹配当前的显示设备的图像。

### <a name="new-ltdevicegt-image-type-dialog-box"></a>新&lt;设备&gt;映像类型对话框

**新建&lt;设备&gt;映像类型**对话框中，可创建指定类型的新设备图像。 若要打开**新建\<设备 > 图像**对话框中，选择**新建图像类型**上**映像**菜单。 包含的以下属性是**目标图像类型**并**自定义**。

#### <a name="target-image-type"></a>目标图像类型

列出了可用的图像类型。 选择想要打开的映像类型：

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

#### <a name="custom"></a>自定义

此时将打开**自定义映像**对话框可以创建新的映像使用自定义的大小和颜色数。

**自定义映像**对话框中，可创建新的映像使用自定义的大小和颜色数。 是包含的以下属性：

|属性|描述|
|---|---|
|**Width**|提供空间以输入自定义图像的宽度以像素为单位 （1-512，限制 2048年）。|
|**Height**|提供空间以输入自定义映像以像素为单位 （1-512，限制 2048年） 的高度。|
|**颜色**|提供空间以选择自定义图像的颜色数：2、 16 或 256。|

### <a name="open-ltdevicegt-image-dialog-box"></a>打开&lt;设备&gt;图像对话框

使用**打开&lt;设备&gt;映像**对话框可以在 c + + 项目中打开设备图像。 它列出了当前资源 （属于当前资源的映像） 中的现有设备图像。 是包含以下属性：

|属性|描述|
|---|---|
|**当前映像**|列出资源中包含的映像。 选择你想要打开的图像类型。|

### <a name="to-create-a-new-icon-or-cursor"></a>若要创建新图标或光标

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果已有现有的图像资源在.rc 文件中，例如游标，您可以右键单击**游标**文件夹，然后选择**插入光标**从快捷菜单。)

   > [!NOTE]
   > 如果你的项目尚未包含.rc 文件，请参阅[创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**，然后选择**新建**。 对于图标，此操作使用 32 × 32，16 色图标创建一个图标资源。 对于游标，32 × 32，创建单色 （2 种颜色） 映像。

   如果一个加号 (**+**) 中的图像资源类型旁边会显示**插入资源**对话框中，这意味着工具栏模板都可用。 选择加号以展开模板列表中的，选择一个模板，然后选择**新建**。

## <a name="add-an-image-for-a-different-display-device"></a>添加不同的显示设备的图像

1. 上**图像**菜单中，选择**新设备图像**(或右键单击**的图像编辑器**窗格中，然后选择**新设备图像**从快捷菜单）。

1. 选择你想要添加的图像的类型。 您还可以选择**自定义**以创建其大小不可用的默认列表中的图标。

## <a name="copy-a-device-image"></a>复制设备图像

1. 上**图像**菜单中，选择**打开设备图像**和从当前的图像列表中选择映像。 例如，选择 32 × 32，16 色版本的图标。

1. 复制当前显示的图标图像 (**Ctrl**+**C**)。

1. 打开另一个图像的图标在另一个**的图像编辑器**窗口。 例如，打开 16 × 16，16 色版本的图标。

1. 粘贴图标图像 (**Ctrl**+**V**) 从一个**图像编辑器**到其他窗口。 如果您要粘贴到较小的大小更大的大小，可以使用图标句柄来调整图像的大小。

## <a name="delete-a-device-image"></a>删除设备图像

在显示的图标图像同时**图像**编辑器中，选择**删除设备图像**从**图像**菜单。 当您删除的资源中的最后一个图标图像时，也会删除该资源。

   > [!NOTE]
   > 当您按下**Del**键、 图像和颜色绘制图标会删除，但是图标将保持; 现在可以重新设计它。 如果按下**Del**错误地，可以按**Ctrl**+**Z**要撤消的操作。

## <a name="create-transparent-or-inverse-regions-in-device-images"></a>在设备图像中创建透明或反转区域

在中[的图像编辑器](../windows/image-editor-for-icons.md)，初始的图标或光标图像有透明特性。 尽管图标和光标图像矩形，但许多没有出现，因为图像的部分是透明的;通过图标或光标显示在屏幕上的基础映像。 当您拖动的图标图像的部分可能会出现在倒排的颜色。 通过设置屏幕颜色和中的反转颜色创建这种效果[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。

屏幕和反转颜色将应用于图标和光标形状，颜色派生的映像或者反向区域分配。 颜色指示图像的具有这些属性的部分。 您可以更改表示屏幕颜色和反色中编辑属性的颜色。 这些更改不会影响应用程序中的光标的图标的外观。

> [!NOTE]
> 显示的对话框和菜单命令可能与“帮助”中的描述不同，具体取决于现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

### <a name="to-create-transparent-or-inverse-regions"></a>若要创建透明或反转区域

1. 在中**颜色**窗口中，选择**屏幕颜色**选择器或**反色**选择器。

1. 将应用的屏幕或使用绘图工具在图像上的反转颜色。 有关绘图工具的详细信息，请参阅[使用绘图工具](using-a-drawing-tool-image-editor-for-icons.md)。

### <a name="to-change-the-screen-or-inverse-color"></a>若要更改屏幕或反转颜色

1. 选择任一**屏幕颜色**选择器或**反色**选择器。

1. 选择从一种颜色**颜色**中的调色板**颜色**窗口。

   另一个选择器自动分配补色。

   > [!TIP]
   > 如果您双击**屏幕颜色**或**反色**选择器中，[自定义颜色选择器对话框](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)出现。

## <a name="use-the-256-color-palette"></a>使用 256 色调色板

使用**图像**编辑器、 图标和光标可以是固定大小较大 (64 × 64) 使用 256 色调色板，可供选择。 创建资源后，选择设备映像样式。

### <a name="to-create-a-256-color-icon-or-cursor"></a>若要创建 256 色图标或光标

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果已有现有的图像资源在.rc 文件中，例如游标，您可以右键单击**游标**文件夹，然后选择**插入光标**从快捷菜单。)

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**，然后选择**新建**。

1. 上**图像**菜单中，选择**新设备图像**。

1. 选择所需的 256 色图像样式。

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>若要从大图标的 256 色调色板选择颜色

若要通过选择绘制从 256 色调色板，您需要选择中的颜色**颜色**中的调色板[颜色窗口](../windows/colors-window-image-editor-for-icons.md)。

1. 大图标或光标，选择或创建新的大图标或光标。

1. 从显示中的 256 种颜色中选择颜色**颜色**中的调色板**颜色**窗口。

   选定的颜色将成为中的当前颜色**颜色**中的调色板**颜色**窗口。

   > [!NOTE]
   > 使用 256 色图像的初始调色板匹配返回的调色板`CreateHalftonePalette`Windows API。 适用于 Windows 外壳程序的所有图标应都使用此面板来防止在调色板实现过程的闪烁。

## <a name="set-a-cursor39s-hot-spot"></a>设置游标&#39;s 作用点

游标的作用点的作用是指 Windows 跟踪光标的位置。 默认情况下，作用点设置为游标 （坐标为 0，0） 的左上角。 **热点**属性中的[属性窗口](/visualstudio/ide/reference/properties-window)显示作用点坐标。

### <a name="to-set-a-cursors-hot-spot"></a>若要设置光标的作用点

1. 上[的图像编辑器工具栏](../windows/toolbar-image-editor-for-icons.md)，选择**设置作用点**工具。

1. 选择想要分配为光标的作用点的像素。

   **热点**属性中的**属性**窗口将显示新的坐标。

   > [!TIP]
   > 将鼠标光标悬停工具栏按钮上时，会出现工具提示。 这些提示可以帮助您确定每个按钮的功能。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图像菜单](../windows/image-menu-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
[图标](/windows/desktop/menurc/icons)<br/>
[光标](/windows/desktop/menurc/cursors)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
