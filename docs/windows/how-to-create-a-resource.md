---
title: 如何：创建资源 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- resources [C++], viewing
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
ms.openlocfilehash: fdf158bab7894497dbcfb147eb2c6e061879be75
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764046"
---
# <a name="how-to-create-a-resource-c"></a>如何：创建资源 （c + +）

**资源视图**窗口将显示在项目中包含的资源文件。 展开顶部文件夹（如 Project1.rc）将显示该 .rc 文件中的资源类型。 展开每种资源类型将显示该类型的各个资源。

> [!NOTE]
> 此信息不适用于通用 Windows 平台应用中的资源。 有关的详细信息，请参阅[应用程序资源和资源管理系统](/windows/uwp/app-resources/)。

> [!NOTE]
> **资源视图**Express 版本不支持。

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

> [!NOTE]
> 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

**资源视图**窗口中使用**添加资源**对话框将资源添加到 c + + Windows 桌面应用程序项目。 此对话框具有以下属性：

|属性|描述|
|---|---|
|**资源类型**|指定你想要创建的资源类型。<br/><br/>你可以展开光标和对话框资源目录以显示其他资源。 这些资源都位于 Visual Studio...\Microsoft `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct。 如果添加.rct 文件，必须将其放在此目录也必须指定[包括路径](../windows/how-to-specify-include-directories-for-resources.md)它们。 之后，这些文件中的资源将显示在相应类别下的第二层。 可以添加的.rct 文件数没有预设的限制。<br/><br/>显示在树控件顶层的资源是 Visual Studio 提供的默认资源。|
|**新建**|创建基于中已选择的类型的资源**资源类型**框。 资源将在适当的编辑器中打开。 例如，如果创建对话框资源，它在中打开[对话框编辑器](../windows/dialog-editor.md)。|
|**Import**|此时将打开**导入**对话框中，在其中您可以导航到资源你想要导入到当前项目。 可导入位图、图标、光标、HTML 资源文件、声音 (.WAV) 资源文件或自定义资源文件。|
|**自定义**|此时将打开**新的自定义资源**对话框可以在其中创建自定义资源。 仅可以在二进制编辑器中编辑自定义资源。|

**新的自定义资源**对话框中，可在 c + + 项目中创建新的自定义资源。 此对话框具有以下属性：

|属性|描述|
|---|---|
|**资源类型**|提供一个文本框，以输入自定义资源类型的名称。 Visual c + + 在退出时自动将大写名称**新的自定义资源**对话框。|

当创建新资源时，Visual c + + 的唯一名称为其指定，例如， `IDD_Dialog1`。 可通过在关联的资源编辑器中或 [“属性窗口”](/visualstudio/ide/reference/properties-window)中编辑该资源的属性来自定义该资源 ID。

可以创建资源，为新的默认资源 （不基于模板的资源） 或作为资源后面[模板](../windows/how-to-use-resource-templates.md)。

> [!NOTE]
> 未指定资源名称或保留的 Visual Studio 的 ID。 保留的名称为 DESIGNINFO、 HWB 和 TEXTINCLUDE，保留的 ID 为 255。

## <a name="to-open-the-resource-view-window"></a>打开资源视图窗口

选择**资源视图**上**视图**菜单。

   \- 或 -

按**Ctrl** + **Shift** + **E**。

> [!TIP]
> 您可以右键单击**资源视图**窗口来启动命令的快捷菜单。 也可以在标题栏上双击以停靠或取消停靠该窗口。 在标题栏上右击将提供允许控制窗口行为的其他命令。 有关详细信息，请参阅[Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

## <a name="to-create-a-new-resource-in-resource-view"></a>在“资源”视图中创建新资源

1. 与你的.rc 文件中的焦点**资源视图**，选择**编辑**菜单，然后选择**添加资源**(或右键单击.rc 文件中的**资源视图** ，然后选择**添加资源**从快捷菜单)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

1. 在中**添加资源**对话框框中，选择你想要添加到项目的资源的类型。

## <a name="to-create-a-new-resource-in-solution-explorer"></a>在解决方案资源管理器中创建新资源

1. 在 **“解决方案资源管理器”** 中，右击项目文件夹，然后选择 **“添加”**，然后单击快捷菜单上的 **“添加资源”** 。

   如果还没有在项目中的.rc 文件，此步骤将创建一个。 然后可以重复此步骤将特定资源类型添加到新的 .rc 文件。

2. 在中**添加资源**对话框框中，选择你想要添加到项目的资源的类型。

## <a name="to-create-a-new-resource-in-class-view"></a>在“类视图”中创建新资源

1. 在中[类视图](/visualstudio/ide/viewing-the-structure-of-code)，右键单击您的类，然后选择**添加**，然后选择**添加资源**从快捷菜单。

2. 在中**添加资源**对话框框中，选择你想要添加到项目的资源的类型。

## <a name="to-create-a-new-resource-from-the-project-menu"></a>从“项目”菜单创建新资源

从 **“项目”** 菜单中，选择 **“添加资源”**。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[使用资源文件](../windows/working-with-resource-files.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源编辑器](../windows/resource-editors.md)<br/>
