---
title: 创建设备图像（图标的图像编辑器）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: ce1069f6f410d7a60d631461086ca8870ef679c0
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560291"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>创建设备图像（图标的图像编辑器）

当创建新图标或光标资源**图像**编辑器首先在特定样式 （32 × 32，16 种颜色图标和 32 × 32，游标的单色） 中创建映像。 然后可以将不同大小和样式的图像添加到初始图标或光标，并编辑每个其他映像，根据需要对不同的显示设备。 此外可以通过使用剪切和粘贴操作从现有的映像类型或在图形计划中创建的位图编辑映像。

当你打开中的图标或光标资源[的图像编辑器](../windows/image-editor-for-icons.md)，默认情况下将打开大多数紧密匹配当前的显示设备的图像。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="new-ltdevicegt-image-type-dialog-box"></a>新&lt;设备&gt;映像类型对话框

**新建&lt;设备&gt;映像类型**对话框中，可创建指定类型的新设备图像。 若要打开**新建\<设备 > 图像**对话框中，选择**新建图像类型**上**映像**菜单。 包含的以下属性是**目标图像类型**并**自定义**。

### <a name="target-image-type"></a>目标图像类型

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

### <a name="custom"></a>自定义

此时将打开**自定义映像**对话框可以创建新的映像使用自定义的大小和颜色数。

**自定义映像**对话框中，可创建新的映像使用自定义的大小和颜色数。 是包含的以下属性：

|属性|描述|
|---|---|
|**Width**|提供空间以输入自定义图像的宽度以像素为单位 （1-512，限制 2048年）。|
|**Height**|提供空间以输入自定义映像以像素为单位 （1-512，限制 2048年） 的高度。|
|**颜色**|提供空间以选择自定义图像的颜色数：2、 16 或 256。|

## <a name="open-ltdevicegt-image-dialog-box"></a>打开&lt;设备&gt;图像对话框

使用**打开&lt;设备&gt;映像**对话框可以在 c + + 项目中打开设备图像。 它列出了当前资源 （属于当前资源的映像） 中的现有设备图像。 是包含以下属性：

|属性|描述|
|---|---|
|**当前映像**|列出资源中包含的映像。 选择你想要打开的图像类型。|

## <a name="to-create-a-new-icon-or-cursor"></a>若要创建新图标或光标

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果已有现有的图像资源在.rc 文件中，例如游标，您可以右键单击**游标**文件夹，然后选择**插入光标**从快捷菜单。)

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**，然后选择**新建**。 对于图标，此操作使用 32 × 32，16 色图标创建一个图标资源。 对于游标，32 × 32，创建单色 （2 种颜色） 映像。

   如果一个加号 (**+**) 中的图像资源类型旁边会显示**插入资源**对话框中，这意味着工具栏模板都可用。 选择加号以展开模板列表中的，选择一个模板，然后选择**新建**。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标和光标：显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[快捷键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[图标和光标：显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[图像菜单](../windows/image-menu-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)<br/>
